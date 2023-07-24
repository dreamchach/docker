# docker
1. 도커 파일을 만들 폴더 하나 만들기
2. 방금 생성한 도커 파일 폴더를 에디터를 이용해서 실행
3. 파일 하나를 생성
4. 그 안에 먼저 어떻게 진행해 나갈지 기본적인 토대를 명시
5. 이제 베이스 이미지부터 실제 값으로 추가해주기
6. 베이스 이미지는 `ubuntu`를 써도 되고 `centos`등을 써도 되지만, hello를 출력하는 기능은 굳이 사이즈가 큰 베이스 이미지를 쓸 필요가 없기에 사이즈가 작은 `alpine`베이스 이미지를 사용
7. hello 문자를 출력해주기 위해 `echo`를 사용하여야 하는데 이미 `alpine`안에 `echo`를 사용하게 할 수 있는 파일이 있기에 `RUN`부분은 생략함
8. 마지막으로 컨테이너 시작 시 실행될 명령어 `echo hello`를 적어준다
9. docker file에 입력된 것들이 docker 클라이언트에 전달되어서 docker server가 인식하게 하여야 합니다
그렇게 하기 위해서 `docker build ./` 또는 `docker build .`을 사용합니다.

>`build` 명령어는 해당 디렉토리 내에서 `dockerfile`이라는 파일을 찾아서 docker 클라이언트에 전달시켜줍니다.

10. `dockerfile`을 실행시킵니다. 실행을 위해서는 `docker build ./`시 나왔던 단어가 필요로 되는데,

```bash
kimjiyeong@gimjiyeong-ui-Macmini docker % docker build ./
[+] Building 3.4s (5/5) FINISHED                           docker:desktop-linux
 => [internal] load build definition from dockerfile                       0.0s
 => => transferring dockerfile: 334B                                       0.0s
 => [internal] load .dockerignore                                          0.0s
 => => transferring context: 2B                                            0.0s
 => [internal] load metadata for docker.io/library/alpine:latest           2.7s
 => [1/1] FROM docker.io/library/alpine@sha256:82d1e9d7ed48a7523bdebc18cf  0.6s
 => => resolve docker.io/library/alpine@sha256:82d1e9d7ed48a7523bdebc18cf  0.0s
 => => sha256:82d1e9d7ed48a7523bdebc18cf6290bdb97b82302a8 1.64kB / 1.64kB  0.0s
 => => sha256:e3bd82196e98898cae9fe7fbfd6e2436530485974dc4fb3 528B / 528B  0.0s
 => => sha256:5053b247d78b5e43b5543fec77c856ce70b8dc705d9 1.49kB / 1.49kB  0.0s
 => => sha256:8c6d1654570f041603f4cef49c320c8f6f3e4013249 3.33MB / 3.33MB  0.5s
 => => extracting sha256:8c6d1654570f041603f4cef49c320c8f6f3e401324913009  0.1s
 => exporting to image                                                     0.0s
 => => exporting layers                                                    0.0s
 => => writing image sha256:55f9561f3be8260639034a889fffb80178e4e51cf4b8e  0.0s

What's Next?
  View summary of image vulnerabilities and recommendations → docker scout quickview
```

여기서 기억해야 할 문장은 
```bash
 => => writing image sha256:55f9561f3be8260639034a889fffb80178e4e51cf4b8e  0.0s
 ```
 입니다.

단어 `55f9561f3be8260639034a889fffb80178e4e51cf4b8e`의 앞부분 일부만 따서 실행시키면 docker 작업이 실행됩니다.

여기서는 명령어를 `docker run 55f`로 넣어주면 되겠군요.
그럼 `hello`라는 단어가 나타납니다.
