# 키친포스

## 요구 사항

### `상품`
- 상품을 생성할수 있다.
    - 상품 가격은 0원 이상이어야 한다.
- 상품 목록을 조회할 수 있다.
    
### `메뉴 그룹`
- 메뉴 그룹을 생성할 수 있다.
- 메뉴 그룹의 목록을 조회할 수 있다.
 
### `메뉴`
- 메뉴를 생성할 수 있다.
    - 메뉴 상품이 하나 이상 존재해야 한다.
    - 메뉴 가격은 0원 이상이어야 한다.
    - 메뉴 그룹이 등록되어 있어야 한다.
    - 메뉴 상품들이 모두 등록되어 있어야 한다.
    - 메뉴 가격이 메뉴 상품들의 가격 총합보다 비쌀 수 없다. 
- 메뉴의 목록을 조회할 수 있다.

### `주문`
- 주문을 생성할 수 있다.
    - 하나 이상의 주문 항목을 가져야 한다.
    - 모든 주문 항목의 메뉴가 등록되어 있어야 한다. 
    - 주문 테이블이 등록되어 있어야 한다.
    - 주문 테이블이 비어있는 경우 생성할 수 없다.
    - 주문 상태는 조리중으로 생성된다.
- 주문 목록을 조회할 수 있다.
- 주문의 상태를 변경할 수 있다.
    - 주문의 상태가 이미 완료된 경우 변경할 수 없다.
     
### `주문 테이블`
- 주문 테이블를 생성할 수 있다.
- 주문 테이블 목록을 조회할 수 있다.
- 주문 테이블의 등록 가능 상태를 변경할 수 있다.
    - 단체 지정이 되어 있다면 상태를 변경할 수 없다.
    - 주문이 조리 중이거나 식사 중일때는 상태를 변경할 수 없다.
- 주문 테이블에 손님 수를 등록한다.
    - 손님 수는 0명 이상이어야 한다.
    - 주문 등록 불가 상태인 주문 테이블인 경우 등록할 수 없다. 

### `단체 지정`  
- 단체 지정을 생성할 수 있다.
    - 주문 테이블이 2개 이상이어야 한다.
    - 주문 테이블들이 모두 등록되어 있어야 한다.
    - 주문 테이블이 주문 등록 가능 상태이거나 단체 지정이 되어 있으면 등록할 수 없다. 
- 단체 지정을 삭제할 수 있다.  
    - 주문 테이블이 조리 중이거나 식사 중일때는 단체 지정을 삭제할 수 없다. 

## 애그리거트 별 도메인 to-do 리스트

### 공통
- `금액(Money)`
    - [X] 금액은 0원 이상이다.
    - [X] 금액이 같으면 동등성을 보장한다.
    - [X] 금액을 더할 수 있다.
    - [X] 금액을 뺄 수 있다.
    - [X] 금액을 곱할 수 있다.

### 상품
- `상품(Product)`
    - [X] 상품을 생성한다.

### 메뉴 그룹
- `메뉴 그룹(MenuGroup)`
    - [X] 메뉴 그룹을 생성한다.
    
### 메뉴    
- `메뉴(Menu)`
    - [X] 메뉴를 생성한다.
    - [X] 메뉴 상품이 하나 이상 존재해야 한다.
    - [X] 메뉴 가격이 메뉴 상품들의 가격 총합보다 비쌀 수 없다.
- `메뉴 상품들(MenuProducts)`
    - [X] 메뉴 상품을 생성한다.
    - [X] 메뉴 상품들의 가격 총합을 구한다.
- `메뉴 상품(MenuProduct)`
    - [X] 메뉴 상품들을 생성한다.
    - [X] 상품의 가격과 개수를 반영하여 가격을 구한다.

### 주문 테이블
- `주문 테이블(OrderTable)`
    - [X] 주문 테이블을 생성한다.
    - [X] 손님 수는 0명 이상이어야 한다.
    - [X] 주문 테이블의 등록 가능 상태를 변경한다.
    - [ ] 주문 테이블의 주문이 조리 중이거나 식사 중일때는 상태를 변경할 수 없다.
    - [X] 단체 지정이 되어 있다면 상태를 변경할 수 없다.
    - [X] 주문 테이블에 손님 수를 변경한다.
    - [X] 손님 수 변경 시 0명 이상이어야 한다.
    - [X] 등록 불가 상태인 주문 테이블인 경우 손님 수를 변경할 수 없다.
    
### 주문
- `주문(Order)`
    - [ ] 주문을 생성한다.
        - [ ] 주문 상태는 조리중으로 생성된다.
    - [ ] 하나 이상의 주문 항목을 가져야 한다. 
    - [ ] 주문 테이블이 등록 불가 상태인 경우 생성할 수 없다.
    - [ ] 주문의 상태를 변경할 수 있다.
    - [ ] 주문의 상태가 이미 완료된 경우 변경할 수 없다.
- `주문 항목들(OrderLineItems)`
- `주문 항목(OrderLineItem)`

### 단체 지정    
- `단체 지정(TableGroup)`
    - [ ] 단체 지정을 생성한다.
    - [ ] 주문 테이블이 2개 이상이어야 한다.
    - [ ] 주문 테이블이 등록 가능 상태면 지정할 수 없다.
    - [ ] 이미 단체 지정이 되어 있으면 지정할 수 없다. 
    - [ ] 단체 지정을 삭제할 수 있다.  
    - [ ] 해당 주문 테이블이 조리 중이거나 식사 중일때는 단체 지정을 삭제할 수 없다. 

    
## 용어 사전

| 한글명 | 영문명 | 설명 |
| --- | --- | --- |
| 상품 | product | 메뉴를 관리하는 기준이 되는 데이터 |
| 메뉴 그룹 | menu group | 메뉴 묶음, 분류 |
| 메뉴 | menu | 메뉴 그룹에 속하는 실제 주문 가능 단위 |
| 메뉴 상품 | menu product | 메뉴에 속하는 수량이 있는 상품 |
| 금액 | amount | 가격 * 수량 |
| 주문 테이블 | order table | 매장에서 주문이 발생하는 영역 |
| 빈 테이블 | empty table | 주문을 등록할 수 없는 주문 테이블 |
| 주문 | order | 매장에서 발생하는 주문 |
| 주문 상태 | order status | 주문은 조리 ➜ 식사 ➜ 계산 완료 순서로 진행된다. |
| 방문한 손님 수 | number of guests | 필수 사항은 아니며 주문은 0명으로 등록할 수 있다. |
| 단체 지정 | table group | 통합 계산을 위해 개별 주문 테이블을 그룹화하는 기능 |
| 주문 항목 | order line item | 주문에 속하는 수량이 있는 메뉴 |
| 매장 식사 | eat in | 포장하지 않고 매장에서 식사하는 것 |
