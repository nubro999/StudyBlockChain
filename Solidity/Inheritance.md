# Inheritance

Solidity는 **상속(Inheritance)** 과 **다형성(Polymorphism)** 을 지원한다.  
이를 통해 코드를 재사용하고, 상속 계층에서 유연하게 동작을 정의할 수 있다.

---

## 1. 기본 상속
- **Parent Contract**의 함수와 상태변수를 **Child Contract**에서도 사용할 수 있다.
- `is` 키워드로 상속받는다.

```solidity
// parent contract Parent1
contract Parent1{
  // 컨트랙트 내용
}

// child contract Child1
contract Child1 is Parent1{
  // 컨트랙트 내용
}

```

---

## 2. Multiple Inheritance
- Solidity는 하나의 **Child Contract**가 여러 개의 **Parent Contract**로부터 상속을 받을 수 있는 **다중 상속**을 지원한다.

### 주의!
- 다중 상속 시 **Diamond Problem(충돌 문제)** 가 발생할 수 있다.
- 이를 해결하기 위해 Solidity는 **C3 Linearization** 방식을 사용한다.

```solidity
// parent contract Parent1
contract Parent1{
  // 컨트랙트 내용
}

// parent contract Parent2
contract Parent2{
  // 컨트랙트 내용
}

// 다중 상속을 하는 경우
// child contract Child2
contract Child2 is Parent1, Parent2{
  // 컨트랙트 내용
}

```
---
## C3 Linearization
- **C3 Linearization**은 다중 상속에서 함수 호출 순서를 정리하는 **알고리즘**이다.
- Solidity는 오른쪽에서 왼쪽, **DFS(Depth-First-Search)** 방식으로 상속 순서를 처리한다.
```solidity
contract A {}
contract B is A {}
contract C is A {}
contract D is B, C {}
```
### 상속 계층
- B는 A를 상속받아 `[B, A]`라는 상속 계층을 갖고 있다.
- C는 A를 상속받아 `[C, A]`라는 상속 계층을 갖고 있다.
- D는 `[B, A]`와 `[C, A]`를 병합하여 상속 계층을 형성한다.

### 기본 규칙
1. **선택하려는 요소가 모든 리스트의 첫 번째 원소보다 뒤에 있으면 안 된다.**  
    즉, 어떤 리스트에서라도 첫 번째 원소보다 뒤에 있는 요소를 선택할 수 없다.
2. **왼쪽 우선 깊이 탐색**에 따라 리스트를 병합한다.

## 병합 과정
### a. 초기화 상태 
`listB = [B, A]` `listC = [C, A]` `Result = []`

---
### b. 첫번째 요소 선택 (listB의 첫 번째 요소 : `B`)
- `B`는 `listC`에 없으므로 선택 가능.
- `listB`와 `listC`에서 `B` 제거.  
현재 상태 : `Result = [B]` `listB = [A]` `listC = [C, A]`
---
### c. 다음 요소 선택 (listB의 첫 번째 요소: `A`)
- `A`는 `listC`에서 `C` 뒤에 있으므로 아직 선택할 수 없음.
- 대신, `listC`의 첫 번째 요소 `C`를 확인.
- `C`는 `listB`에 없으므로 선택 가능.
- `listB`와 `listC`에서 `C` 제거  
현재 상태 : `Result = [B, C]` `listB = [A]` `listC = [A]`
---
### d. 마지막 요소 선택 (listB와 listC의 첫 번째 요소: `A`)
- `A`는 모든 리스트의 첫 번째 요소이므로 선택 가능.
- `Result = [B, C, A]`  
---
> 결과 : **D의 상속 계층은 D→B→C→A** 이다.
---

## 3. 다형성(Polymorphism)
- 함수를 **재정의(override)** 했을 때, 상속 계층에서 가장 마지막에 정의된(파생된) 함수가 호출된다.

---

## 4. Overriding
- **Parent Contract**의 함수를 **Child Contract**에서 Overriding(재정의)할 수 있다.
![[Pasted image 20250718210355.png]]
### 규칙
1. **Parent Contract** 함수는 `virtual`로 선언되어야 한다.
2. **Child Contract** 함수는 `override` 키워드를 사용해야 한다.
3. **Visibility**는 `external → public` 방향으로만 변경할 수 있다.
4. **Mutability**는 제한적인 방향으로만 변경할 수 있다:
   - `view → pure`
   - 단, `payable`은 변경 불가.
```solidity
// parent contract Parent1
contract Parent1{
  function foo() public virtual returns (string memory){
    return "A";
  }
}
// child contract Child1
contract Child1 is Parent1{
  function foo() public override returns (string memory){
    return "B";
  }
}
```
- Parent1 컨트랙트는 상속할 수 있는 function foo를 `virtual` 키워드와 함께 정의하고있다.
- Child1 컨트랙트는 Parent1를 상속받아 function foo를 `override`키워드와 함께 재정의하고있다. 
---

## 5. Shadowing
- 상태변수는 **오버라이딩할 수 없다**.
- Overriding이 함수 재정의에 대한 것이었다면, shadowing은 상태변수를 부모계약과 동일한 이름으로 자식계약에서 다시 선언하는 것을 말한다. 
- **Parent Contract**에서의 상태변수와 동일한 이름의 상태변수를 **Child Contract**에서 선언하면 오류가 발생한다.

### 상태변수를 재정의하려면?
- **Constructor(생성자)** 를 통해 초기화해야 한다.
- 모든 부모 계약의 생성자는 자동으로 호출 되지 않기 때문에 **명시적으로 호출**해야 한다.  
    명시적으로 호출하지 않으면 컴파일 에러가 난다. 
- 상속 계층에서의 생성자는 **C3 Linearization** 순서에 따라 실행된다.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract A {
    constructor(string memory _name) {
        // A의 생성자
    }
}

contract B is A {
    constructor(string memory _name) A(_name) {
        // B의 생성자
    }
}

contract C is A {
    constructor(string memory _name) A(_name) {
        // C의 생성자
    }
}

contract D is B, C {
    constructor(string memory _name) B(_name) C(_name) {
        // D의 생성자
    }
}
```
C3 Linearization에 의해 컨트랙트D 의 **상속계층은 D -> B -> C -> A** 이다. 
- D는 B를 먼저 상속받으므로, B의 생성자가 호출된다. 그러나 B는 A를 상속받기 때문에, B의 생성자를 실행하기 전에 A의 생성자가 먼저 실행된다. **(A 생성자 실행-> B 생성자 실행)**
- D는 B 다음으로 C를 상속받는다. C의 생성자는 실행되기 전에 C가 상속받은 A의 생성자가 실행되어야하지만, A의 생성자는 이미 실행되었으므로 중복 실행되지 않는다. **(C 생성자 실행)**
- 마지막으로 **D 생성자가 실행**된다. 

---

## 6. Super
- 다중 상속 **C3 Linearization** 알고리즘에 따라 정해진 상속계층에 따라 parent contract를 호출한다.
- `super` 키워드를 통해 상속 계층의 다다음 컨트랙트를 불러올 수 있다. 
- 다다음 컨트랙트가 없으면, 바로 다음 컨트랙트의 함수가 호출된다. 


### 다중 상속 예시 코드 (D -> B -> C -> A)
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract A {
    function foo() public virtual returns (string memory) {
        return "A";
    }
}

contract B is A {
    function foo() public virtual override returns (string memory) {
        return "B";
    }
}

contract C is A {
    function foo() public virtual override returns (string memory) {
        return "C";
    }
}

contract D is B, C {
    function foo() public override(B, C) returns (string memory) {
        return super.foo();
    }
}
```

상속 계층이 D -> B -> C -> A 일 때, D에서 `super`를 호출하면 D의 다다음인 C가 호출된다.  

---

### 단일 상속 예시 코드 ()
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract A {
    function foo() public virtual returns (string memory) {
        return "A";
    }
}

contract C is A {
    function foo() public override returns (string memory) {
        return super.foo();
    }
}
```
상속 게층이 C -> A 일 때, C에서 `super`를 호출하면 다다음 컨트랙트가 없으므로 바로 다음인 A가 호출된다. 

---
