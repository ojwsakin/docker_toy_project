## docker_toy_project
# Docker swarm을 통한 Canary update구현과 Monitoring구축
## 프로젝트 목표

- Ubuntu를 base image로 하는 VM 3개를 **docker swarm**을 통하여 인프라를 구축하고 운영합니다
- Update방식 중 하나인 **Canary update**방식을 학습합니다
- **모니터링**을 위하여 cAdvisor, Prometheus, Grafana를 통해 리소스 및 update과정을 확인합니다

---

## 사용한 기술 스택

**“docker-swarm”**

- 어플리케이션이 서비스 단위로 배포되며 컨테이너들을 관리하기 위한 **오케스트레이션 툴**입니다

**“Over-lay network”**

- 물리적 네트워크 위에서 가상의 컴퓨터 네트워크입니다
- 새롭게 배포되는 이미지를 테스트 하기위해 사용했습니다

**“web 3tier”**

- web은 apache를 사용했습니다
- was server은 tomcat 이미지를 기반으로 구축했습니다
- DB는 mySQL로 클러스터 내부에 구축했습니다

**“Canary update”**

- 새로운 버전(new)의 일부를 배포해서 직접 확인해 본 후 오류가 없을 시 새로운 버전으로 업데이트 하는 방식입니다

**“cAdvisor”**

- 컨테이너에 대한 정보를 수집 및 처리를 위한 데몬입니다

**“Prometheus”**

- 메트릭을 수집하고 시각화, 알람 등의 기능을 제공하는 오픈소스 모니터링 시스템입니다
- cAdvisor가 수집한 데이터를 가져오도록 설정했습니다

**“Grafana”**

- 수집된 시계열 데이터를 시각화 하기위한 dashboard를 제공하는 Tool입니다
- 다양한 플러그인이 존재하여 확장성면에서 뛰어납니다

---

## 아키텍쳐 구성도

### “Update”이전 (기존 버전의 서비스가 운영 중인 상황을 가정)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e3c9162f-ded8-480a-a3a8-270d8e1ce32e/Untitled.png)

- Worker1에 존재하는 흑백의 컨테이너에 배포되어 있는 새로운 버전이 ‘3tier-damo’라는 네트워크를 통해 일부만 배포되어 있는 환경입니다

### “Update”이후 (새로운 버전의 서비스로 업데이트)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4371a7ce-7631-41e8-93ec-c355134ac76f/Untitled.png)

- 새로운 서비스로 모두 업데이트를 완료하였으며, 서비스가 운영중인 ‘3tier’네트워크에 배포가 되었습니다

### “Monitoring 시스템”

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/48a82b1d-fc42-47be-b697-1071ecfa7764/Untitled.png)

- cAdvisor을 통해 컨테이너들에 대한 정보를 수집할 수 있습니다.

---

## 결론

- docker-swarm을 이용하여 인프라를 쉽게 구축 및 관리를 할 수 있고 update 방식에 대한 이해를 가질 수 있었습니다
- Monitoring을 위해 Grafana와 Prometheus, cAdvisor을 구축해 볼 수 있었고, 구성한 인프라에 대한 정보들을 시각적으로 확인 할 수 있었습니다.
- 구성한 인프라에 대한 정보와 사용 중인 리소스의 정보를 dashboard를 통해 쉽게 알아 볼 수 있었으나, 로그에 대한 정보를 얻는 방법을 도입해 보지 못한 것이 아쉽습니다
