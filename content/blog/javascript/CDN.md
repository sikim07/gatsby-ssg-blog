---
title: 'CDN / 컨텐츠 전송 네트워크 / Content delivery network / content distribution network'
date: 2022-08-24 09:00:39
category: 'javascript'
draft: false
---

## Definition

콘텐츠 전송 네트워크(`Content delivery network` 또는 `content distribution network` (CDN))는 **콘텐츠를 효율적으로 전달하기 
위해 여러 노드를 가진 네트워크에 데이터를 저장하여 제공하는 시스템**을 말한다. **인터넷 서비스 제공자(ISP)에 직접 연결되어 데이터를 
전송하므로, 콘텐츠 병목을 피할 수 있는 장점**이 있다.

CDN의 **목적**은 **높은 사용성과 효율로 사용자에게 컨텐츠를 전달함**에 있다. CDN은 오늘날 인터넷에 존재하는 컨텐츠의 상당수를 서비스하고 있는데 
이에는 웹 요소 (텍스트, 그래픽, 스크립트), 다운로드 가능한 요소 (미디어 파일, 소프트웨어, 문서), 애플리케이션 (전자상거래, 포털), 
실시간 미디어, 주문형 스트리밍, 그리고 소셜 네트워크 등이 있다.

미디어 회사나 전자상거래 업체와 같은 콘텐츠 제공자는 그들의 컨텐츠를 사용자들에게 전달하기 위해서 CDN 회사에 사용료를 지불한다. 반대로, 
CDN은 ISP, 이동통신사업자, 그리고 네트워크 사업자들에게 데이터 센터에서의 서버 호스팅 비용을 지불한다. 더 나은 퍼포먼스와 사용성 
이외에도 CDN은 컨텐츠 제공자의 서버의 트래픽을 덜어주어 컨텐츠 제공자의 비용을 줄여준다. 추가로, CDN은 대규모 분산 서버 장비로 공격 
트래픽을 완화할 수 있으므로 컨텐츠 제공자에게 DoS 공격에 대해서 어느정도 보호해 줄 수 있다. 초기 대부분의 CDN은 CDN이 소유하고 
동작하는 서버를 사용하는 컨텐츠만 서비스하였으나 최신 트랜드는 P2P기술을 이용하는 하이브리드 모델을 사용하는 것이다. 하이브리드 모델에서 
컨텐츠는 지정된 서버 그리고 주변 컴퓨터(peer-user-owned)를 모두 사용한다.
---
## CDN이란

CDN(콘텐츠 전송 네트워크)은 **지리적으로 분산된 여러 개의 서버**입니다. 웹 콘텐츠를 **사용자와 가까운 곳에서 전송함으로써 전송 속도를 높입니다.** 
전 세계 데이터센터는 파일 복사본을 임시로 저장하는 프로세스인 캐싱을 사용합니다. 따라서 사용자는 가까운 서버를 통해 웹 활성화 디바이스 또는 
브라우저에서 인터넷 콘텐츠에 빠르게 접속할 수 있습니다. CDN은 웹 페이지, 이미지, 비디오 등의 콘텐츠를 사용자의 물리적 위치와 가까운 프록시
서버에 캐싱합니다. 이렇게 하면 콘텐츠가 로딩될 때까지 기다릴 필요 없이 영화 감상, 소프트웨어 다운로드, 은행 잔고 확인, 소셜 미디어 
포스팅, 구매 등의 작업을 할 수 있습니다.

CDN을 마치 ATM처럼 생각해도 좋습니다. 여러 곳에 ATM을 설치해 놓으면 사용자가 빠르고 효율적으로 현금을 찾을 수 있습니다. 은행에서 
긴 줄을 서서 기다릴 필요 없이 가까운 곳에 있는 ATM을 바로 사용하면 됩니다.

인터넷으로 그래픽과 비디오 등 용량이 큰 웹 콘텐츠를 전송하면 트래픽이 폭주할 때처럼 네트워크 혼잡 문제가 발생할 수 있습니다. CDN 
서비스는 이러한 문제를 해결하기 위해 개발되었습니다. 중앙 서버에서 개별 사용자에게 콘텐츠를 전송하려면 시간이 너무 오래 걸렸습니다. 
이제 CDN은 텍스트, 그래픽, 스크립트, 미디어 파일부터 소프트웨어 다운로드, 문서, 포털, 이커머스, 라이브 스트리밍 미디어, 온디맨드 
비디오 스트리밍 미디어, 소셜 미디어 사이트에 이르기까지 모든 것을 처리합니다.

출처 : https://ko.wikipedia.org/wiki/%EC%BD%98%ED%85%90%EC%B8%A0_%EC%A0%84%EC%86%A1_%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC, https://www.akamai.com/ko/our-thinking/cdn/what-is-a-cdn