## Syncnet_python | 200409-200140

audio to video sync

- https://github.com/joonson/syncnet_python
  http://www.robots.ox.ac.uk/~vgg/publications/2019/Afouras19/afouras18c.pdf

#### Tensorflow-gpu 사용을 위한 기본 설정

- Tensorflow-gpu 

  gpu 및 nvidia 사용을 위해서

  1. 노트북 GPU 사양에 맞는 nvidia driver 설치

     => NVIDIA GeForce GTX 1060 window 10 - 64bit driver

  2. cuda 10.0 설치

     => Cuda 설치 시, visual studio가 깔려있지 않으면 실행 오류 발생

     => 오류 해결법

     ​		:  visual studio 설치 or cuda 설치 시, 빠른 실행이 아닌 사용자 설정에 들어가서 			visual studio integration 체크 해제

  3. cudnn 설치

     => cuda 10.0 version에 해당하는 cudnn설치 필요( cudnn-10.0-windows10-x64)

     => 다운 받은 zip 파일 압축 해제 후, 폴더 내 내용물을 복사

     => `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0` 경로내에 붙여넣기

- GPU 작동 체크

  ```python
  from tensorflow.python.client import device_lib
  
  print(device_lib.list_local_devices())
  ```

  

#### syncnet 코드 분석

- pytorch 설치

  - OS-windows, Package-pip, Language-Python, Cuda-10.0 일 경우

    ```
    pip install torch===1.4.0 torchvision===0.5.0 -f https://download.pytorch.org/whl/torch_stable.html
    ```

- requirements.txt 설치

  ```
  pip install -r requirements.txt
  ```

- script returns

  ![image-20200409211653200](C:/Users/multicampus/key/AI/sub2/documents/eunyoung/images/image-20200409211653200.png)

- pipeline

  ```
  sh download_model.sh
  python run_pipeline.py --videofile /path/to/video.mp4 --reference name_of_video --data_dir /path/to/output
  python run_syncnet.py --videofile /path/to/video.mp4 --reference name_of_video --data_dir /path/to/output
  python run_visualise.py --videofile /path/to/video.mp4 --reference name_of_video --data_dir /path/to/output
  ```

  - output 디렉토리 내에 저장

    ![image-20200410123247437](C:/Users/multicampus/key/AI/sub2/documents/eunyoung/images/image-20200410123247437.png)

    위 폴더 내에 동영상, 오디오, pckl 파일들이 모두 저장됨.

    

- run_pipline.py

  - face_detection

    ```python
    from detectors import S3FD
    
    def inference_video(opt):
    	DET = S3FD(device='cuda')
    	# S3FD: real-time face detector
    ```

    

  - detectors/s3fd/nets.py

    - `L2Norm`

      - Norm은 벡터의 길이 혹은 크기를 측정하는 함수.
      - Norm이 측정한 벡터의 크기는 우너점에서 벡터 조표까지의 거리 혹은 Magnitude
      - Norm은 각 요소별로 요소 절대값을 p번 곱한 값의 합을 p 제곱근한 값입니다.

      $$
      Lp=(∑^n_i |x_i|^p)^{\frac{1}{p}}
      $$

      - p는 Norm의 차수를 의미하며, p가 2일때 L2Norm 이다.
      - n은 대상 벡터의 요소수

      

  - detectors/s3fd/box_utils.py

    - `Class Detect()`

      - 인스턴스 변수

        num_classes 클래스

        top_k : The Maximum number of box preds to consider

        nms_thresh : The threshold to be used in NMS

        conf_thresh : The confidence scores threshold of detection boxes. Boxes with confidence scores under threshold should be ignored

        variance :

        nms_top_k : Maximum number of detections to be kept according to the confidences aftern the filtering detections based on score_threshold.

        

      

### nms (non maximum suppression)

- 중복 제거

- 기존 NMS 는 가장 높은 confidence 를 가지는 bbox 를 찾고, 같은 클래스 인 bbox 들 중 겹치는 영역이 일정 비율 이상인 (iou > threshold) bbox 를 제거해서 중복된 detection 결과를 없앤다

- 딥러닝을 이용한 Object Detection에서는 대부분 각종 boundingbox + 각 box에 object가 있을 확률 (class별 확률)들이 나오게 되는데, 이중 겹치는 부분 

  (차 한대에 여러가지 boundingbox가 그려지는 경우와 같은)을 제거하기 위한 방법으로 사용된다. 

- https://dyndy.tistory.com/275

- https://jetsonaicar.tistory.com/15

- 동작 알고리즘

  - 연산에는 IoU가 필요하며, IoU가 threshold 이상인 case에 대해서만 NMS 연산이 수행된다.
  - 연산 알고리즘은 다음과 같다.
    1. 동일한 class에 대해 confidence 순서대로 높-낮 순으로 정렬한다.(line 13)
    2. 가장 높은 confidence를 갖는 bounding box와 IoU가 일정 threshold 이상인 다른 bounding box가 존재한다면 동일한 객체를 탐지한것으로 판단하고 지운다.(16~20)
       - 보통 threshold는 0.5로 한다.(or 0.6-0.9)



1. nms로 중복되는 confidence가 낮은 후보들을 제거

## Pytorch

- python 기반 연산 패키지

  - NumPy 를 대체하면서 GPU 연산이 필요한 경우
  - 최대한 유연성과 속도를 제공하는 딥러닝 연구 플랫폼이 필요한 경우

- forward()

  - 모델이 학습 데이터를 입력받아서  forward propagation을 진행시키는 함수, 반드시 함수 이름이 foward 여야 한다.

    ** Forward propagation(순전파)

    - 뉴럴 네트워크 모델의 입력층부터 출력층 까지 순서대로 변수들을 계산하고 저장하는 것을 의미

  