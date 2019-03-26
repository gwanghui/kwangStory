---
description: Secure Shell
---

# SSH

## 암호 기반 인증과 키 기반 인증

SSH는 서버와 클라이언트를 인증하는 여러 메커니즘을 제공하며, 일반적으로 사용되는 인증 메커니즘은 비밀번호 기반 및 키 기반 인증입니다. 암호 기반 인증도 안정적이긴 하나 키 기반 인증을 대신 사용하는 것이 좋다.

원격 로그인 프로그램이 가져야할 주요 특징

* 커뮤니케이션의 프라이버시 : 원격 셸 로그인을 제공하는 연결은 도청을 방지하기 위해 암호화 되어야 한다.
* 클라이언트 &lt;-&gt; 서버가 보내고 받는 데이터가 변경되지 않았는지 확인하는 메커니즘이 있어야한다. 무결성 검사가 필수이다.
* 서버와 클라이언트의 신원은 적절한 인증을 설정하기 위해 서로 주고 받아야 한다.

SSH가 제공하는 기능

* SSH 터널링
* TCP 포트포워딩

현대의 보안 시ㅌ스템은 통신 보안을 보장하기 위해 2가지 방법\(대칭키, 공개키\)을 모두 사용한다.

## SSH \(Secure Shell\) 프로토콜 버전 1의 워크 플로우

* 연결은 항상 클라이언트가 서버에 대해서 시작하며, 서버의 22번 포트에 대한 TCP 연결을 설정하는 것입니다. 서버는 응답으로 서버가 지원하는 프로토콜 버전과 SSH서버 패키지 버전을 준다. 이 시점에서 클라이언트가 해당하는 프로토콜을 지원한다면 계속 진행하고 그렇지 않으면 연결이 끊어진다.
* 클라이언트가 서버에 표시된 프로토콜 버전에 따라 계속할지 여부를 결정하면 서버와 클라이언트는 "Binary Packet Protocol"로 전환한다. 이 프로토콜은 32비트길이의 packet과 padding을 포함하고 있다.
* 서버는 중요한 정보 중 일부를 클라이언트에 보낸다. 이 정보는 로그인 세션에서 사용된다.
  * 서버가 클라이언트에 ID\(RSA 공개키\)를 공개한다. 이 키는 대게 해당 서버 위치에 저장된다. 클라이언트는 서버에 처음 연결할때 하단의 경고를 받게 되며 첫 번째 연결 후, 이 서버의 키는 known\_hosts파일에 저장되어 나중에 서버를 연결할때 경고 메세지가 표시 되지 않는다.
  * 서버가 클라이언트에 서버키를 공개한다. 이 서버키는 서버에서 클아이언트로 교환되는 키이며 ssh 버전 2에서는 사용되지 않는다. 이 키는 기본 구성에 따라 매 시간마다 재생성되며, 기본 크기는 768비트 이다. 이 내용은 ssh 서버 설정 파일\(/etc/ssh/sshd\_conf\)에서 볼수 있다.
  * 8 랜덤 바이트는 체크 바이트로 불리워 집니다. 이는 클라이언트가 서버에 대한 회신을 할때 이 바이트를 보내야합니다.
  * 서버는 지원되는 모든 암호화 인증 방법을 제공합니다.

```bash
[root@slashroot1 ssh]# pwd
/etc/ssh
[root@slashroot1 ssh]# cat ssh_host_rsa_key.pub
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAxlwxaB4wKrFHGsqUYEzYtTIJWjgul8ML+bnnJIg0HER1wnW2QitRqDzw6f9cr3WKvwqAQh/Sf4bM0LqUAXZre+J6oiLY7X8V6NtEA8nHO1qryueNe44rI6HYunZ3yo4UAXUZqxhjer+tA8OCD6DLRfXOWIMsBUBXJuB+yl1/qGH2J0Kjrnpj17N0mPMqGmMb8+9EjV1Rs1aSDriIWjDsJIDd8fz4gRoelB5mFsEQ7rD+m/RNWxbAhkBoNcFadRg30LqhCtGYQsWADv0p4THCDVZxB3u9VSWK9qZRgF7LbGRdgiVgJjGDPqCO3cWlnQzxcZ9VdvKy+em1RB9BJ++kuw==
```

```text
[root@slashroot1 ~]# ssh 192.168.0.105
The authenticity of host '192.168.0.105 (192.168.0.105)' can't be established.
RSA key fingerprint is c7:14:f4:85:5f:52:cb:f9:53:56:9d:b3:0c:1e:a3:1f.
Are you sure you want to continue connecting (yes/no)?
```

```text
# 임시 버전 1 서버 키의 수명 및 크기 
#KeyRegenerationInterval 1h 
#ServerKeyBits 768
```

4.  서버가 지원하는 알고리즘 목록에 따르면 클라이언트는 무작위 대칭키를 생성하고 해당 대칭 키를 서버에 보냅니다. 클라이언트는 서버 ID로 첫번째 암호화를 수행하고 두번째 암호화는 1시간마다 변경되는 서버 키로 암호화 합니다. 이중 암호화는 보안성을 높이기 위해 사용하며 어떤 누군가가 호스트의 서버의 private key를 가지고 있을 경우에도 메세지를 decrypt할 수 없도록 하기 위함입니다. 이중 암호화 된 세션 키와 클라이언트는 3단계에서 서버가 제시한 알고리즘 목록에서 선택한 항목을 전송합니다.

5. 아직 클라이언트는 서버를 인증한것이 아닙니다. 그것은 단지 서버 호스트 키의 형태로 서버에 의해 주어진 서버의 Identity를 가지고 있는 것입니다., 서버를 인증하기 위해서는 클라이언트는 서버가 세션 키 전송을 해독 할 수 있는지 확인해야 합니다. 세션키\(이중암호화된 데이터\)를 보낸 후 클라이언트는 서버로부터 확인 메세지를 기다립니다. 서버에서 보낸 확인 메세지는은 클라이언트가 보내는 대칭 세션 키로 암호화해야 합니다 이 확인 메세지를 기다리는 단계는 클라이언트에게는 굉장히 중요한 단계입니다. 왜냐하면 클라이언트는 올바른 서버가 ID를 준지 모르기 때문입니다.













