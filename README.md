# Linux
서버 구축전 필요지식(Centos 7 버전기반)
1) Vi 에디터 사용법
2) rpm 사용법
3) 사용자 계정
4) IP설정 : /etc/sysconfig/network-scripts/ifcfg-ens32(Centos 7) , Centos 8 부턴 ifcfg-ens160
5) 데몬
6) 시스템 응급 복구 
7) 방화벽 설정
8) 디스크 Mount
9) 상대경로,절대경로 , CD 명령어
10) 

# AutoMount
개요 : 리눅스 재부팅시 자동으로 Mount해주는기능
설정파일 : /etc/fstab
(파티션) (마운트포인트)  (파일시스템) (기능)
ex) /dev/sr0 /test defaults 1 1
주의사항 : 만약 오토마운트된 하드디스크가 제거되었을경우 실행오류발생함

# 서버관련파일 설정사항
1) 패키지 설치
2) 포트
3) 서비스
4) 데몬
5) 설정 파일 <br>
1 패키지 설치는 /dev/sr0 마운트해서 /Packages 폴더에서 관련 파일  찾아서 rpm으로 설치 <br>
2,3번은 firewall-cmd 방화벽관련 명령어로 해결 <br>
4 데몬실행 systemctl start (데몬이름) <br>
5 번 설정파일 설정,데이터 수정할때마다 데몬 재실행해줘야함 <br>

# NFS
개요 : 네트워크를 이용한 파티션 공유서비스(Network File System) <br>
장점 : 상대방 PC의 공간을 할당받아 사용가능 <br>
단점 : 서버전원이 꺼저있을경우 데이터 접근불가능 <br>
응용 : 파티션에 NFS적용시에는 해당 파티션 용량만큼만 할당가능 <br>
설치 내용 :
1) 패키지 : nfs
2) 포트 : 2049/tcp
3) 서비스 : nfs
4) 데몬 : nfs
5) 설정파일 : /etc/exports

# DNS
개요 : Domain Name Server, 도메인주소를 IP주소로 변환해주는 서버, 원래 사이트접속시 IP주소를 통한 접근을해야하지만 여러가지이유로 IP대신 Domain주소로 사이트접속을 하고 이러한 Domain과 IP를 맵핑해주는 서버가 DNS 서버 만약 DNS서버가 고장나면 www.naver.com통한 네이버접속이 불가능하고, 직접적인 네이버 IP입력을통한 접근만가능.
설치 내용 :
1) 패키지 : bind
2) 포트 : 53/tcp, 53/udp
3) 서비스 : dns
4) 데몬 : named
5) 설정 파일 : 
/etc/named.conf : 53번 포트 접속설정 등
/etc/resolv.conf : DNS 서버 설정
/etc/named.rfc1912.zones : DNS 파일 설정
/var/named : named.rfc1912.zones에 설정한 파일있는곳

# Web Server
개요 :
설치 내용 :
1) 패키지 : httpd
2) 포트 : 80/tcp
3) 서비스 : http
4) 데몬 : httpd
5) 설정 파일 : 
/etc/httpd/conf/httpd.conf : 해당위치에서 웹서버파일위치, 계정으로로그인(Alias)설정가능
6) 주의 사항 : 

# DNS, Web Server이용한실습
1. DNS와 Web Server IP를 192.168.111.128로해놓고 domain을 www.jong.com으로 설정 , window 사용자에서 접속확인되면 성공(DNS와 Web Server 미분리)
2. DNS를 192.168.111.128, Web Server 를 192.168.111.129 로 설정 domain www.jong.com , window 사용자에서 접속확인되면 성공(DNS와 Web Server 분리)
3. DNS를 192.168.111.128, Linux Web Server 를 192.168.111.129 , Window Web Server 192.168.111.130 으로 설정
www.jong.com : Linux Web Server , window.jong.com : Window Web Server , window 사용자가 각 서버 접속가능하면 성공






# DB Server
개요 : 사용자의 데이터를 보관하는 데이터서버로 Linux에서는 mariadb(Mysql)을 사용중이다



# SQL명령어
DB 구조 : 데이터베이스 > 테이블 > 필드 > 값 , DBMS안에는 여러가지 데이터베이스가 있는데 각 데이터베이스는 여러가지 테이블로 구성되었이며, 테이블은 여러가지 필드로 구성되있고 그 필드안에는 값이 할당되어있다.
1) create : 데이터베이스와 테이블 생성가능 create database (데이터베이스 이름) , create table (테이블이름) 
2) drop : 데이터베이스와 테이블 제거가능 drop database (데이터베이스 이름), drop table (테이블 이름)
3) insert : 테이블에 값입력기능 insert into (데이터베이스 이름) (필드1,필드2,...) values (값1,값2,...) , insert into (데이터에비스 이름) values (값1,값2,...)
4) update : 테이블에 있는 데이터수정기능 update (테이블이름) set (필드1)=(값), (필드2)=(값)
5) delete : 테이블에 있는 데이터삭제기능 delete from (테이블이름) where (조건)
6) alter : 
7) select : 테이블에 있는 데이터 조회기능 select (조회하고싶은 필드명) from (테이블이름)
8) show : 데이터베이스와,테이블확인가능 show database (데이터베이스 이름) , show table (테이블 이름)
9) use : 사용할 데이터베이스 선택가능 use mysql : mysql 데이터베이스를 사용하겠다는뜻
10) desc : 해당 테이블의 내용 요약확인가능 

