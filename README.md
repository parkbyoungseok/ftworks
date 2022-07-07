혁신 기술 개발 국책과제를 위한 기본 Repo 입니다.

특별한 Code는 없을 예정이며,

각 프로젝트에서 필요한 서버 API 들에 대한 내용만 있을 것입니다.

각 프로젝트의 소스 코드는 별도의 Repo를 만들어서 진행할 예정입니다.

서버 API 는 3가지 입니다.

## Login
- UserID / PWD 를 사용해서 로그인하는 기능
- URL : http://3.35.213.205/api/ft/login.php
- Request Param : GET, POST 모두 가능
  - userid : 사용자 User ID
  - passwd : 사용자 Password
- Response Json :
  - code : Integer 
    - 200 : 정상
    - 500 : 에러
    - 기타 필요할 경우 추가 예정
  - msg : String
    - 응답 코드에 대한 Message
  - username : String
    - 직원의 이름
  - sessionid : Integer
    - 로그인 이후, Header 에 넣어서 보내줘야 할 Session ID
    - Header 이름은 X-FT-Header 의 값으로 보내주시면 됩니다.
- PWD 는 사용자의 NFC Tag ID 와 동일하게 맞출 예정.
- Test 의 편의성을 위해서 현재 등록되어있는 Test 계정은 3개로,
  - ID : test / PWD : test
  - ID : test2 / PWD : test2
  - ID : admin / PWD : admin
  - 3개의 계정이 등록되어서 테스트가 가능한 상태.


## Order List
- 주문 건들에 대한 상세 리스트를 볼 수 있는 API
- URL : http://3.35.213.205/api/ft/orderlist.php
- Request Param : GET, POST 모두 가능
  - order_id : 원하는 주문 ID가 있을 경우, order_id 를 넘겨주면 해당하는 주문건에 대한 정보만 리턴해 줌. orderid 가 없으면 전체 주문 정보가 리턴 됨.
- Response Json :
  - id : String
    - order_id 로 사용하면 됨.
  - status : String
    - 주문 건에 대한 현재 상태
    - "0" : 주문 완료 상태
    - "100" : 작업자 할당 완료 상태
    - "200" : 패킹 작업 진행 상태
    - "300" : 패킹 완료 상태
  - company_name : String
    - 주문자(식당) 이름
  - company_address : String
    - 주문자 주소
  - company_address_extra : String
    - 주문자 상세 주소
  - company_contact : String
    - 주문자 전화 번호
  - basket_items : Array
    - product_id : String
      - 상품 고유 번호
    - name : String
      - 상품 이름
    - amount : String
      - 상품 수량

## Order Status 변경
- 주문 건에 대한 상태를 변경하는 API
- URL : http://3.35.213.205/api/ft/orderstatus.php
- Request Param : GET, POST 모두 가능
  - order_id : 변경하려는 주문 ID
  - status : 변경하려는 주문 ㄴ
  - order_id : 변경하려는 주문 상태
  - order_id : 변경하려는 주문 ID
