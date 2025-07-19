
1. DID(분산 신원인증)이란?

DID(Decentralized Identifier)는 중앙기관(정부, 기업 등)에 의존하지 않고, 사용자가 자신의 신원 정보를 직접 생성하고 관리할 수 있도록 하는 분산 신원 식별자입니다. 즉, 내 신원은 내가 소유하고, 내가 통제한다는 자기주권 신원(Self-Sovereign Identity, SSI)의 핵심 기술입니다.

![[Pasted image 20250710055340.png]]
![[Pasted image 20250709191637.png]]

RWA (real world asset)

블록체인에 올라와 있는 실물 자산 > 토큰화 > nft발행
funzable token / token이란 - 장부


2. DID의 구조

DID의 형식  
DID는 URL과 유사한 고유 식별자입니다.  
예시: did:example:123456789abcdefghi  
여기서 did는 스킴, example은 DID 메소드, 123456789abcdefghi는 고유 식별자입니다.

DID 문서(DID Document)  
DID가 가리키는 신원 정보와 공개키, 서비스 엔드포인트 등을 담은 JSON 문서입니다.  
주요 요소로는 공개키(Public Key), 인증 메커니즘(Authentication, 서명 방식 등), 서비스(Service Endpoints)가 있습니다.

3. DID의 동작 방식

1단계. DID 생성  
사용자가 블록체인 또는 분산원장에 DID를 등록하여 고유한 DID를 발급받습니다.

2단계. DID 문서 등록  
DID와 연결된 DID Document(공개키 등)를 분산원장에 등록합니다.

3단계. 신원 증명  
서비스 이용 시, DID와 관련된 전자서명을 통해 신원을 증명합니다. 검증자는 블록체인에서 DID Document를 조회하고, 공개키로 서명을 검증합니다.

4단계. 신원 정보 관리  
사용자는 자신의 DID, 키, 속성(자격증, 학위 등)을 직접 관리하며, 필요 시 신원 증명서(Verifiable Credential)를 제3자 기관으로부터 받아 보관합니다.

4. 주요 기술 요소

블록체인 또는 분산원장: DID 등록, DID Document 저장, 불변성과 신뢰성 확보  
공개키 기반 구조(PKI): DID 소유권 증명, 서명 및 검증  
Verifiable Credential(VC, 검증 가능한 증명서): 신원 정보(학위, 자격증 등)를 표준화된 방식으로 발급 및 검증  
DID 메소드: DID 생성, 해석, 관리 방식을 정의하는 표준(예: did:ethr, did:sov, did:key 등)  
지갑(Wallet): DID, VC, 개인키 등을 안전하게 저장하고 관리하는 앱 또는 서비스

5. DID의 장단점

장점  
자기주권 신원: 사용자가 신원정보를 직접 소유하고 통제할 수 있음  
프라이버시 보호: 필요한 정보만 선택적으로 공개 가능  
상호 운용성: 표준화된 방식으로 다양한 서비스와 플랫폼에서 활용 가능  
보안성: 블록체인 기반 불변성, 위변조 방지  
사용자 경험 개선: 반복적인 인증 및 회원가입 절차 간소화

단점  
도입 초기 단계: 생태계 및 표준화가 진행 중이라 대중적 확산은 제한적  
키 관리 부담: 사용자가 개인키를 잃어버리면 신원 복구가 어려움  
규제 및 법적 이슈: 각국 신원 인증 관련 법률과의 정합성 문제  
서비스 연동 한계: 기존 중앙집중식 시스템과의 연동 및 호환성 문제

6. DID 활용 사례

디지털 신분증(모바일 운전면허증, 학생증, 사원증, 주민등록증 등)  
금융 인증(비대면 실명 인증, KYC, 계좌 개설 등)  
공공 서비스(정부 민원, 투표, 의료 정보 관리 등)  
교육(학위 및 자격증 증명, 이력 관리 등)  
기업 서비스(B2B 인증, 출입 통제, 공급망 신원관리 등)

7. DID 관련 표준 및 오픈소스

W3C DID 표준  
주요 오픈소스: Hyperledger Indy, Aries, Ursa, uPort, Sovrin, Microsoft ION, DIDKit 등

1. 공개키 기반 암호(PKI, Public Key Infrastructure)  
    DID의 소유권 증명, 인증, 메시지 서명 등에 사용됩니다.  
    비대칭키 쌍(공개키/개인키)을 생성하고, DID 문서에 공개키를 등록합니다.  
    대표 알고리즘으로는 ECDSA(Elliptic Curve Digital Signature Algorithm), EdDSA(Edwards-curve Digital Signature Algorithm, Ed25519 등), RSA(최근에는 덜 사용됨)가 있습니다.
    
2. 디지털 서명(Digital Signature)  
    DID 소유자가 자신임을 증명하고, 데이터의 위변조 방지 및 무결성을 보장하는 데 사용됩니다.  
    VC(Verifiable Credential) 서명, DID Document 업데이트 요청 서명 등에 활용됩니다.
    
3. 해시 함수(Hash Function)  
    데이터의 무결성 검증과 프라이버시 보호(데이터를 직접 공개하지 않고 해시값만 공개)에 사용됩니다.  
    SHA-256, SHA-3 등이 대표적인 해시 알고리즘입니다.
    
4. 암호화(Encryption)  
    DID Document 내 일부 데이터의 암호화, 프라이버시 보호, 민감 정보 비공개 처리에 사용됩니다.  
    대칭/비대칭 암호 모두 사용될 수 있습니다.
    
5. 키 교환(Key Exchange)  
    DID 소유자 간 안전한 통신 채널을 생성하기 위해 사용됩니다.  
    대표적으로 Diffie-Hellman(ECDH 등) 방식이 사용됩니다.
    
6. 제로 지식 증명(Zero-Knowledge Proof, ZKP)  
    사용자가 자신의 속성을 증명하되, 실제 정보는 공개하지 않는 방식입니다.  
    프라이버시 강화와 선택적 공개에 활용되며, Verifiable Credential의 selective disclosure(선택적 공개) 등에 사용됩니다.  
    zk-SNARK, zk-STARK 등이 대표적인 예입니다.
    
7. DID Document 내 키 관리 메커니즘  
    키 회전(Key Rotation): 키가 유출되거나 만료될 경우 새로운 키로 교체합니다.  
    다중 서명(Multisig): 여러 키로 공동 관리할 수 있도록 합니다.

|       |      |               |       |                        |
| ----- | ---- | ------------- | ----- | ---------------------- |
| ECDSA | 높음   | 짧음(256bit 등)  | 빠름    | 비트코인, 이더리움 등 블록체인      |
| EdDSA | 더 높음 | 더 짧음(Ed25519) | 매우 빠름 | DID, 최신 블록체인, SSH, GPG |
|       |      |               |       |                        |

---

요약 표

암호학 매커니즘 : 주요 역할/사용처 : 대표 알고리즘  
공개키 암호 : 소유권 증명, 인증, 서명 : ECDSA, EdDSA, RSA  
디지털 서명 : 데이터 무결성, 인증 : ECDSA, EdDSA  
해시 함수 : 무결성 검증, 프라이버시 보호 : SHA-256, SHA-3  
암호화 : 데이터 보호, 프라이버시 : AES, RSA, ECC  
키 교환 : 안전한 통신 채널 : ECDH  
제로 지식 증명 : 정보 비공개 상태에서의 증명 : zk-SNARK, zk-STARK  
키 관리 : 키 교체, 다중 서명 : 해당 없음

[[What is Blockchain Security]]

## DID 실제 적용사례
- **Microsoft ION**: DID 기반 분산 신원 네트워크(비트코인 위)
- **유니세프 Giga**: 학교 인터넷 연결 DID 인증
- **삼성, SKT, LGU+**: PASS 앱 기반 DID 신분증
- **유럽연합 eIDAS**: 유럽 디지털 신원 프레임워크
- **메타마스크, Unstoppable Domains**: Web3 DID 로그인
    - [[PASS원리]]