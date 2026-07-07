# 🏠 Yanolja Reservation System 🏠
This is a **Yanolja Project** 
that implements the user's accommodation reservation system and the business operator's accommodation registration and management system.

**야놀자** 애플리케이션을 기반으로 `숙박예약 시스템`을 구현하는 프로젝트이다.

<br/>

## 🔊 개요
- 프로젝트명 : Yanolja Reservation Project
- 프로젝트 진행기간 : 2023.07.24 ~ 2023.08.28
- 프로젝트 맴버 : 김가영, 민OO, 박OO
  
![Yanolja1](./README_img/슬라이드1.png)

<br/>

## 👨 프로젝트 역할 분담
* 김가영(본인)
  * 사용자 회원가입 / 회원정보 수정 / 회원탈퇴
  * 사용자 숙소 예약
    * 장바구니 담기 / 장바구니 삭제
    * 결제하기 - `포트원 - KG 이니시스`
    * 예약 확인 / 예약 취소
  * 사용자 리뷰 작성 / 리뷰 수정 / 리뷰 삭제
   
* 민OO
  * 사업자 회원가입 / 회원정보 수정 / 회원탈퇴
  * 사업자 숙소 관리
    * 숙소 예약 현황 확인
    * 객실 체크인 / 체크아웃 등록
  * 사업자 리뷰 관리
    * 사용자 리뷰 확인 / 삭제
    * 사용자 리뷰 답변 달기 / 수정 / 삭제

* 박OO
  * 신규 숙소 등록
    * 숙소 대표이미지 등록
    * 객실 서비스 등록
  * 기존 숙소 관리

<br/>

## ⚙ Requirement
For building and running the applicaion you need:
* `Spring Tool Suite 4`
  * jdk1.8.0_361
  * JavaSE-17
  * STS4 3.1.3
* `HeidiSQL-12.5.0.6677`
  * MariaDB / MySQL

<br/>

## 🎮 기능
![Yanolja2](./README_img/슬라이드2.png)
![Yanolja3](./README_img/슬라이드3.png)

<br/>

## 🧾 DB Table
![Yanolja4](./README_img/슬라이드4.png)

```SQL
/* 회원정보 테이블 */
CREATE TABLE member(
	user_name VARCHAR(20),
	user_id VARCHAR(20),
	user_pw VARCHAR(60),
	user_mobile VARCHAR(60),
	user_dob VARCHAR(60),
	user_email VARCHAR(60),
	user_snsC VARCHAR(60),
	PRIMARY KEY(user_id,user_mobile)
)CHARSET=UTF8;

/* 사업자정보 테이블 */
CREATE TABLE admin(
	admin_location VARCHAR(60),
	region VARCHAR(50),
  	admin_pw VARCHAR(60),
  	business_number VARCHAR(60),
  	admin_mobile VARCHAR(20),
  	admin_id VARCHAR(20),
  	admin_name VARCHAR(20),
  	PRIMARY KEY (admin_location,region,business_number,admin_mobile,admin_id)
)CHARSET=UTF8;

/* 장바구니 관리 테이블 */
CREATE TABLE cart(
	rese_num VARCHAR(12),
	
	user_name VARCHAR(20),
	user_id VARCHAR(20) NOT NULL,
	user_mobile VARCHAR(60) NOT NULL,
		
	host_name VARCHAR(100),
	room_name VARCHAR(40),
	admin_name VARCHAR(20),
	region VARCHAR(40),
	room_info VARCHAR(400),
	id_select_lod VARCHAR(20),
	room_type VARCHAR(20),
	room_price VARCHAR(20),
	
	children VARCHAR(20),
	people VARCHAR(20),
	check_in VARCHAR(20),
	check_out VARCHAR(20),
	people_plus VARCHAR(20),
	PRIMARY KEY(user_id,room_name,check_in)	
)CHARSET=UTF8;

/* 숙소 관리 테이블 */
CREATE TABLE Rental(
	host_name VARCHAR(20),  /* 참조키 설정해주기 */
	room_name VARCHAR(40),
  	room_img VARCHAR(200),
   	region VARCHAR(50),
	min_people VARCHAR(50),
	max_people VARCHAR(50),
	room_pay VARCHAR(20),
	room_num VARCHAR(20),
	address VARCHAR(60),
	info VARCHAR(60),
	service VARCHAR(150),
	Rental_type VARCHAR(20),
	deadline_C VARCHAR(20),
	sleep_type VARCHAR(20),
	startTime VARCHAR(20), 
	endTime VARCHAR(20), 
	useTime VARCHAR(20),
	Representative_photo VARCHAR(150),
	admin_id VARCHAR(20),
	admin_name VARCHAR(20)
)CHARSET=UTF8;

/* 예약 관리 테이블 */
CREATE TABLE reservation(
	rese_num VARCHAR(12),
	user_name VARCHAR(20),
	user_id VARCHAR(20) NOT NULL,
	user_mobile VARCHAR(60) NOT NULL,
		
	host_name VARCHAR(100),
	room_name VARCHAR(40),
	admin_name VARCHAR(20),
	region VARCHAR(40),
	room_info VARCHAR(400),
	room_type VARCHAR(20),
	room_price VARCHAR(20),
	id_select_lod VARCHAR(20),
	
	representative_img VARCHAR(150),
	children VARCHAR(20),
	people VARCHAR(20),
	check_in VARCHAR(20),
	check_out VARCHAR(20),
	click_check_in VARCHAR(20),
	click_check_out VARCHAR(20),
	people_plus VARCHAR(20),	
	PRIMARY KEY(rese_num,room_name,check_in)
) CHARSET=UTF8;

/* 후기 관리 테이블 */
CREATE TABLE review(
	user_id VARCHAR(20),
	rese_num VARCHAR(20),
	room_name VARCHAR(40),
	host_name VARCHAR(100),
	content VARCHAR(100),
	write_date VARCHAR(60),
	review_point INT,
	admin_id VARCHAR(50),
	admin_content VARCHAR(50),
	admin_write_date VARCHAR(50)
)CHARSET=UTF8;

```

<br/>

## 🎞 DEMO

## 사용자 계정 관리
![Yanolja5](./README_img/슬라이드5.png)
![Yanolja6](./README_img/슬라이드6.png)
![Yanolja7](./README_img/슬라이드7.png)
![Yanolja8](./README_img/슬라이드8.png)

<br/>


## 사용자 숙소 예약
![Yanolja9](./README_img/슬라이드9.png)
![Yanolja10](./README_img/슬라이드10.png)
![Yanolja11](./README_img/슬라이드11.png)
![Yanolja12](./README_img/슬라이드12.png)
![Yanolja13](./README_img/슬라이드13.png)

<br/>


## 사업자 계정
![Yanolja14](./README_img/슬라이드14.png)
![Yanolja15](./README_img/슬라이드15.png)
![Yanolja16](./README_img/슬라이드16.png)
![Yanolja17](./README_img/슬라이드17.png)

