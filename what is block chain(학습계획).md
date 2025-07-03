
# 1. **기초 개념 및 원리 이해**

### 1) 블록체인의 기본 구조와 작동 원리

- 블록, 트랜잭션, 체인, 해시 함수, 머클 트리
- 분산 원장, 탈중앙화, P2P 네트워크 구조
- 블록 생성과 연결, 데이터 불변성

[[What is bitcoin]]

### 2) 암호학 기초

- 해시 함수(SHA-256 등), 공개키/개인키 암호화, 디지털 서명
- 머클 트리, 난이도 조정, 논스(nonce)

[[What is Blockchain Security]]

### 3) 합의 알고리즘

- Proof of Work (PoW), Proof of Stake (PoS), 기타 합의 방식(BFT, DPoS 등)

---

# 2. **대표적인 블록체인 시스템 분석**

### 1) 비트코인

- 비트코인 트랜잭션 구조
- UTXO 모델 
- 채굴 및 보상 시스템 [[가장긴체인]]

### 2) 이더리움

- 스마트 컨트랙트, EVM(Ethereum Virtual Machine) [[What is EVM]] [[SmartContract]]
- 계정 모델(Account Model)
- Solidity(스마트 컨트랙트 언어) 기초

---

# 3. **실습 중심의 블록체인 개발**

### 1) 개발 환경 구축

- **비트코인/이더리움 노드 설치 및 동작 확인**
- **Metamask, Ganache(로컬 이더리움 네트워크)**

### 2) 스마트 컨트랙트 개발

- **Solidity 언어 학습**
- Remix IDE 또는 Hardhat/Truffle로 스마트 컨트랙트 작성/배포
- 간단한 토큰(ERC-20), NFT(ERC-721) 구현

### 3) DApp(Decentralized App) 개발

- Web3.js, Ethers.js 등으로 프론트엔드와 블록체인 연동
- React 기반 간단한 DApp 만들기

---

# 4. **블록체인 심화 주제**

### 1) 블록체인 보안

- 51% 공격, 이중지불, Sybil 공격 등
- 스마트 컨트랙트 취약점(재진입 공격, 오버플로우 등)

### 2) 확장성 문제와 해결책

- 샤딩, 레이어2(플라즈마, 롤업 등), 사이드체인

### 3) 최신 동향 및 응용

- DeFi(탈중앙화 금융), NFT, DAO, DID(분산 신원 인증)
- 프라이버시 강화 기술(영지식증명, 믹싱 등)

---

# 5. **추천 학습 자료**

|단계|자료명/강의명|형태|비고|
|---|---|---|---|
|기초|[모두의 블록체인](https://www.inflearn.com/course/%EB%AA%A8%EB%91%90%EC%9D%98-%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8)|온라인 강의|한글, 입문|
|기초|[Bitcoin Whitepaper](https://bitcoin.org/bitcoin.pdf)|논문|원문|
|응용|[이더리움 공식 문서](https://ethereum.org/ko/developers/docs/)|웹 문서|공식|
|실습|[CryptoZombies](https://cryptozombies.io/)|실습 게임|스마트 컨트랙트|
|실습|[Dapp University 유튜브](https://www.youtube.com/c/DappUniversity)|유튜브|실전 개발|
|심화|[Mastering Bitcoin](https://github.com/bitcoinbook/bitcoinbook)|도서|영어, 심화|
|심화|[Mastering Ethereum](https://github.com/ethereumbook/ethereumbook)|도서|영어, 심화|

---

# 6. **예시 커리큘럼 플로우**

1. **블록체인 기초 이론** (2주)
2. **암호학 및 합의 원리** (1주)
3. **비트코인/이더리움 구조 분석** (2주)
4. **스마트 컨트랙트 프로그래밍** (3주)
5. **DApp 개발 실습** (2주)
6. **보안/확장성/최신 동향** (2주)
7. **프로젝트/응용 사례 구현** (2주)

---

# 7. **학습 팁**

- **실습과 이론을 병행**하세요.  
    (직접 블록체인 노드를 설치하고, 스마트 컨트랙트를 배포해보세요.)
- **공식 문서와 오픈소스 코드**를 적극적으로 참고하세요.
- **커뮤니티(예: Stack Overflow, GitHub, 디스코드)에서 질문/토론에 참여해보세요.
- **최신 트렌드**를 꾸준히 팔로우하세요(DeFi, NFT 등).