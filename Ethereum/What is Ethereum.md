---
tags:
  - Ethereum
---


## 이더리움 개요

**이더리움(Ethereum)**은 비트코인이 화폐 거래에 초점을 맞춘 반면, **스마트 컨트랙트(Smart Contract)** 기능을 도입하여 블록체인의 활용 범위를 획기적으로 확장한 플랫폼입니다. '제2세대 블록체인'이라고도 불리며, 프로그래밍 가능한 블록체인으로 이해할 수 있습니다.

### 주요 특징

- **스마트 컨트랙트**: 미리 정의된 조건이 충족되면 자동으로 실행되는 프로그램입니다. 중개자 없이 신뢰할 수 있는 방식으로 계약을 이행할 수 있게 해주며, 이더리움 블록체인 위에 배포되어 모든 참여자가 그 실행을 검증할 수 있습니다. DApp의 핵심 구성 요소입니다.
    
- **분산형 애플리케이션(DApp)**: 이더리움 블록체인 위에서 스마트 컨트랙트를 기반으로 동작하는 애플리케이션입니다. 중앙 서버 없이 분산된 네트워크에서 운영되므로 검열 저항성, 투명성, 불변성 등의 특징을 가집니다. Geth를 통해 개발하려는 것이 바로 이 DApp입니다.
    
- **이더(Ether, ETH)**: 이더리움 네트워크의 네이티브 암호화폐입니다. 주로 스마트 컨트랙트 실행에 필요한 **가스(Gas)** 비용을 지불하는 데 사용됩니다. 트랜잭션을 처리하고 네트워크를 유지하는 채굴자들에게 보상으로 지급되기도 합니다.
    
- **이더리움 가상 머신(Ethereum Virtual Machine, [[What is EVM]])**: 이더리움 네트워크의 핵심 구성 요소로, 스마트 컨트랙트를 실행하는 런타임 환경입니다. 모든 이더리움 노드는 EVM을 포함하고 있어 스마트 컨트랙트 코드를 실행하고 동일한 결과를 얻을 수 있도록 보장합니다.
    
- **합의 알고리즘**: 이더리움은 한때 **작업 증명(Proof of Work, PoW)** 방식인 Ethash를 사용했지만, 2022년 9월 '더 머지(The Merge)' 업그레이드를 통해 **지분 증명(Proof of Stake, PoS)** 방식인 Casper로 전환했습니다. PoS는 PoW보다 에너지 효율적이며, 네트워크 보안에 기여하는 방식이 다릅니다.
    

### 이더리움과 Geth

**Geth(Go Ethereum)**는 이더리움 프로토콜의 Go 언어 구현체로, 이더리움 노드를 실행하는 데 가장 널리 사용되는 클라이언트 중 하나입니다. Geth를 통해 다음과 같은 작업을 수행할 수 있습니다.

- **이더리움 노드 실행**: 이더리움 블록체인 전체를 다운로드하고 동기화하여 네트워크에 참여할 수 있습니다.
    
- **계정 관리**: 이더리움 주소를 생성하고 관리할 수 있습니다.
    
- **트랜잭션 전송**: 이더를 보내거나 스마트 컨트랙트와 상호작용하는 트랜잭션을 생성하고 서명하여 네트워크에 전송할 수 있습니다.
    
- **스마트 컨트랙트 배포 및 상호작용**: 스마트 컨트랙트를 컴파일하고 이더리움 네트워크에 배포하며, 배포된 컨트랙트의 함수를 호출하여 상호작용할 수 있습니다.
    
- **DApp 개발 환경 제공**: JavaScript 콘솔이나 RPC(Remote Procedure Call) 인터페이스를 통해 Geth 노드와 상호작용할 수 있으므로, DApp 백엔드를 개발하고 테스트하는 데 필수적인 환경을 제공합니다.
    

### [[Dapp]] 개발 로드맵 (Geth 중심)

Geth를 사용하여 DApp을 만드는 목표를 달성하기 위해 일반적으로 다음과 같은 단계를 거치게 됩니다.

1. **개발 환경 설정**: Geth 설치 및 프라이빗 이더리움 네트워크 또는 테스트넷(예: Sepolia) 동기화.
    
2. **Solidity 학습**: 이더리움 스마트 컨트랙트를 작성하는 데 사용되는 프로그래밍 언어인 Solidity를 익힙니다.
    
3. **스마트 컨트랙트 개발**: DApp의 핵심 로직을 Solidity로 구현합니다.
    
4. **컨트랙트 컴파일 및 배포**: 개발한 스마트 컨트랙트를 컴파일하고 Geth 노드를 통해 이더리움 네트워크에 배포합니다.
    
5. **프론트엔드 개발**: 웹3(Web3.js 또는 Ethers.js와 같은 라이브러리)를 사용하여 스마트 컨트랙트와 상호작용하는 사용자 인터페이스(UI)를 개발합니다. 이 프론트엔드가 Geth 노드와 통신하며 블록체인의 데이터를 읽고 쓸 수 있게 합니다.

Ethereum is a blockchain with a computer embedded in it. It is the foundation for building apps and organizations in a decentralized, permissionless, censorship-resistant way.

In the Ethereum universe, there is a single, canonical computer (called the Ethereum Virtual Machine, or EVM) whose state everyone on the Ethereum network agrees on. Everyone who participates in the Ethereum network (every Ethereum node) keeps a copy of the state of this computer. Additionally, any participant can broadcast a request for this computer to perform arbitrary computation. Whenever such a request is broadcast, other participants on the network verify, validate, and carry out ("execute") the computation. This execution causes a state change in the EVM, which is committed and propagated throughout the entire network.

Requests for computation are called transaction requests; the record of all transactions and the EVM's present state gets stored on the blockchain, which in turn is stored and agreed upon by all nodes.

Cryptographic mechanisms ensure that once transactions are verified as valid and added to the blockchain, they can't be tampered with later. The same mechanisms also ensure that all transactions are signed and executed with appropriate "permissions" (no one should be able to send digital assets from Alice's account, except for Alice herself).