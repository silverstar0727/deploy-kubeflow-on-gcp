# deploy-kubeflow-on-gcp


시험기간이라 바빠서 추후 정리할 예정입니다.

간단하게는 다음과 같은 순서로 이루어집니다.

우선은 VM 생성 및 설정입니다.
1. GCP VM instance 생성(spec: n1-standard-8, ubuntu18.04, 150Gi HDD)
2. 방화벽 설정: 30000-50000 포트 개방
3. VM에 방화벽 설정 적용

다음은 설치 작업입니다.

4. 아래 명령어를 통해 해당 레포를 클론 후 디렉토리를 변경해주세요
~~~sh
git clone https://github.com/silverstar0727/deploy-kubeflow-on-gcp.git
cd deploy-kubeflow-on-gcp.git
~~~

5. 모든 쉘 스크립트 파일을 실행 가능하도록 설정해주세요
~~~
chmod +x docker.sh
chmod +x kubectl.sh
chmod +x kubeflow.sh
chmod +x ip.sh
~~~

6. docker를 설치해주세요
~~~
./docker.sh
~~~

7. docker compose를 설치해주세요
~~~
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
~~~

8. exit 명령어를 통해 명령어 창을 끈 후 다시 ssh접속을 해주세요

9. kubectl을 설치해주세요
~~~
./kubectl.sh
~~~

10. kubeflow를 설치해주세요
~~~
./kubeflow.sh
~~~

위 명령어를 한 번 더 입력해주시면 됩니다.

11. 다음의 명령어를 통해 모든 pods가 Running 상태일때까지 12분 가량 기다려주세요
~~~
kubectl get pods -n kubeflow
~~~

12. ip를 확인해주세요
~~~
./ip.sh
~~~

13. VM의 외부 ip에 31380포트를 연결해주세요


# 끝!
