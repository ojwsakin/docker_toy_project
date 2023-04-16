## docker_toy_project
# Docker swarm을 통한 Canary update구현과 Monitoring구축
#### 프로젝트 기간 : 2022.12.23 - 2.22.12.26
#### 작성자 : OH Jinwoo
#### 개인 프로젝트
---
### 프로젝트 목표
- Ubuntu를 base image로 하는 VM 3개를 Docker swarm을 통하여 인프라를 구축하고 운영합니다
- Update방식 중 하나인 Canary update방식을 학습합니다
- Monitoring을 위하여 cAdvisor, Prometheus, Grafana를 통해 리소스 및 클러스터 정보를 모니터링합니다
---
### 사용 기술 스택
#### "Docker-swarm"
- 어플리케이션이 서비스 단위로 배포되며 컨테이너들을 관리하기 위한 오케스트레이션 툴입니다
#### "Overlay Network"
- 물리적 네트워크 위에서 가상의 컴퓨터 네트워크입니다
- 새롭게 배포되는 이미지를 테스트 하기위해 사용했습니다
#### "web 3tier"
- apache, tomcat, mySQL를 이용하여 3tier 아키텍쳐를 구성했습니다
#### "Canary update"
- 새로운 버전의 일부를 배포해서 직접 확인해 본 후 오류가 없을 시 새로운 버전으로 업데이트 하는 방식입니다
#### "cAdvisor"
- 컨테이너에 대한 정보를 수집 및 처리하기 위한 데몬입니다
#### "Prometheus"
- 메트릭을 수집하고 시각화, 알람 등의 기능을 제공하는 오픈소스 모니터링 시스템입니다
- cAdvisor가 수집한 데이터를 가져오도록 설정했습니다
#### "Grafana"
- 수집된 시계열 데이터를 시각화 하기위한 dashboard를 제공합니다
- 다양한 플러그인이 존재하여 확장성면에서 뛰어납니다
