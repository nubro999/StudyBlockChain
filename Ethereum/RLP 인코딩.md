[[What is Ethereum]]
##  **RLP란?**

- **RLP**는 **Recursive Length Prefix**의 약자입니다.
- 이더리움에서 **데이터(특히 트랜잭션, 블록, 리스트 등)를 직렬화(serialize)할 때 사용하는 표준 인코딩 방식**입니다.
- 목적: 데이터를 **간단하면서도 효율적으로** 바이너리로 변환하여 저장/전송할 수 있게 함

---

## 2. **RLP의 기본 원리**

RLP는 **두 가지 타입**만 지원합니다:

1. **바이트 배열(Byte string)**
2. **리스트(List)** (리스트 안에 또 리스트가 들어갈 수 있음 = 재귀적)

각 데이터는 **"prefix(접두사)" + "내용"** 구조로 인코딩됩니다.

---

## 3. **RLP 인코딩 규칙**

### **(1) 단일 바이트 (0x00 ~ 0x7f)**

- 값이 0x00~0x7f(0~127)이면, **그대로 1바이트로 인코딩**  
    (예: 0x05 → 0x05)

### **(2) 짧은 문자열 (0~55바이트)**

- 길이가 1~55바이트라면,  
    **0x80 + 길이** + 내용  
    (예: "dog" → [0x83, 'd', 'o', 'g'])

### **(3) 긴 문자열 (56바이트 이상)**

- 길이가 56바이트 이상이면,  
    **0xb7 + 길이 정보 길이** + 길이 + 내용

### **(4) 리스트**

- 리스트 전체 인코딩 길이가 0~55바이트:  
    **0xc0 + 길이** + 인코딩된 리스트 내용
- 56바이트 이상:  
    **0xf7 + 길이 정보 길이** + 길이 + 내용

---

## 4. **예시**

### **문자열 예시**

- "cat" (ASCII):
    1. 길이 = 3
    2. 0x80 + 3 = 0x83
    3. 인코딩: [0x83, 0x63, 0x61, 0x74] (0x63='c', 0x61='a', 0x74='t')

### **리스트 예시**

- ["cat", "dog"]
    1. "cat" → [0x83, 0x63, 0x61, 0x74]
    2. "dog" → [0x83, 0x64, 0x6f, 0x67]
    3. 두 개 합쳐서: [0x83, 0x63, 0x61, 0x74, 0x83, 0x64, 0x6f, 0x67]
    4. 전체 길이 = 8
    5. 0xc0 + 8 = 0xc8
    6. 최종 인코딩: [0xc8, 0x83, 0x63, 0x61, 0x74, 0x83, 0x64, 0x6f, 0x67]

---

## 5. **RLP의 특징**

- **재귀적**: 리스트 안에 또 리스트가 들어갈 수 있음
- **간단함**: 데이터 타입 구분 없이 길이와 값만으로 구조 표현
- **이더리움 표준**: 트랜잭션, 블록, 컨트랙트 주소 생성 등에 필수

---

## 6. **정리**

- **RLP**는 이더리움에서 데이터 직렬화에 사용되는 간단한 바이너리 인코딩 방식
- **접두사(Prefix) + 내용** 구조로, 문자열과 리스트를 효율적으로 표현
- 컨트랙트 주소 생성, 트랜잭션, 블록 등 다양한 곳에 사용됨