1) docker 설치 
(https://docs.docker.com) 

2) wsl2 설치(윈도우 리눅스 커널 ) 
  -> 윈도우에서 리눅스 os커널을 사용하게 도와주는 패키지
  2.1 WSL 설치
  ```
  dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart 
  ```

  2.2 Virtual 활성화

  ```
  dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
  ```


3) oracle 이미지 설치 

  3.1 ) oracle 이미지 다운 
      ```
     docker pull oracleinanutshell/oracle-xe-11g


     docker run -d -p 1521:1521 -p 1599:8080 oracleinanutshell/oracle-xe-11g

     http://localhost:1599/apex/apex_admin
      admin/Tlqkf123!

      ```
  3.2 ) root 권한으로 로그인( su oracle)
  3.3 ) DCL로 권한추가 


https://kitty-geno.tistory.com/93 참고 
