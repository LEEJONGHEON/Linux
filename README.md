# Linux


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
5) 설정 파일
1 패키지 설치는 /dev/sr0 마운트해서 /Packages 폴더에서 관련 파일  찾아서 rpm으로 설치
2,3번은 firewall-cmd 방화벽관련 명령어로 해결
4 데몬실행 systemctl start (데몬이름)
5 번 설정파일 설정,데이터 수정할때마다 데몬 재실행해줘야함

# NFS
개요 : 네트워크를 이용한 파티션 공유서비스(Network File System)
장점 : 상대방 PC의 공간을 할당받아 사용가능
단점 : 서버전원이 꺼저있을경우 데이터 접근불가능
응용 : 파티션에 NFS적용시에는 해당 파티션 용량만큼만 할당가능
설치 내용 :
1)패키지 : nfs
2)포트 : 2049/tcp
3)서비스 : nfs
4)데몬 : nfs
5)설정파일 : /etc/exports

# DNS
개요 : Domain Name Server, 도메인주소를 IP주소로 변환해주는 서버, 원래 사이트접속시 IP주소를 통한 접근을해야하지만 여러가지이유로 IP대신 Domain주소로 사이트접속을 하고 이러한 Domain과 IP를 맵핑해주는 서버가 DNS 서버 만약 DNS서버가 고장나면 www.naver.com통한 네이버접속이 불가능하고, 직접적인 네이버 IP입력을통한 접근만가능.
설치 내용 :
1)패키지 : bind
2)포트 : 53/tcp, 53/udp
3)서비스 : dns
4)데몬 : named
5)설정 파일 : 
/etc/named.conf : 53번 포트 접속설정 등
/etc/resolv.conf : DNS 서버 설정
/etc/named.rfc1912.zones : DNS 파일 설정
/var/named : named.rfc1912.zones에 설정한 파일있는곳


