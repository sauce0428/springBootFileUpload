🛒 Item Management System (Spring MVC)

Spring MVC 기반의 상품 관리 웹 애플리케이션입니다.
상품 등록 / 조회 / 수정 / 삭제(CRUD) 와 이미지 파일 업로드 및 출력 기능을 제공합니다.

📌 주요 기능

📦 상품 등록 (이미지 업로드 포함)

📄 상품 목록 조회

🔍 상품 상세 조회

✏️ 상품 수정 (이미지 변경 가능)

❌ 상품 삭제 (이미지 파일 함께 삭제)

🖼️ 이미지 스트리밍 출력 (ResponseEntity<byte[]>)

🛠️ 기술 스택
구분	기술
Backend	Spring MVC
ORM	MyBatis
Database	Oracle
View	JSP, JSTL
File Upload	MultipartFile
Connection Pool	HikariCP
Logging	SLF4J
Build Tool	Maven
Server	Apache Tomcat
📂 프로젝트 구조
com.zeus
 ├─ controller
 │   └─ ItemController.java
 ├─ service
 │   └─ ItemService.java
 │   └─ ItemServiceImpl.java
 ├─ mapper
 │   └─ ItemMapper.xml
 │   └─ ItemMapper.java
 ├─ domain
 │   └─ Item.java
 └─ resources
     └─ application.properties

📑 주요 URL 매핑
Method	URL	설명
GET	/item/createForm	상품 등록 화면
POST	/item/create	상품 등록 처리
GET	/item/list	상품 목록
GET	/item/detail?id={id}	상품 상세
GET	/item/display?id={id}	상품 이미지 출력
GET	/item/updateForm?id={id}	상품 수정 화면
POST	/item/update	상품 수정 처리
GET	/item/delete?id={id}	상품 삭제
🖼️ 이미지 처리 방식

이미지 파일은 외부 디렉토리에 저장

DB에는 UUID 기반 파일명만 저장

/item/display 요청 시 이미지 스트리밍 제공

@ResponseBody
@GetMapping("/display")
public ResponseEntity<byte[]> itemDisplay(Item item)


지원 이미지 포맷:

JPG

PNG

GIF

📁 파일 업로드 경로 설정

application.properties

upload.path=D:/upload


⚠️ 서버에 해당 디렉토리가 반드시 존재해야 합니다.

🔐 보안 처리

파일 삭제 시 Path Traversal 공격 방지

if (fileName.contains("..")) {
    throw new IllegalArgumentException("잘못된 경로 입니다.");
}

🔄 상품 수정 로직 요약

새 이미지 업로드 시

기존 이미지 파일 삭제

새로운 파일 저장

이미지 미업로드 시

기존 이미지 유지

📌 예외 처리

이미지 출력 실패 시 400 BAD_REQUEST 반환

DB 처리 결과에 따라 성공 / 실패 페이지 분기

🚀 실행 방법

프로젝트 클론

git clone https://github.com/your-id/item-management.git


Oracle DB 설정 및 테이블 생성

application.properties DB & upload.path 설정

Tomcat 실행

브라우저 접속

http://localhost:8080/item/list

📸 화면 예시 (선택)

여기에 상품 등록 / 목록 / 수정 화면 캡처 추가하면 완성도 👍

✍️ 작성자

Zeus

Spring MVC / MyBatis 기반 웹 프로젝트
