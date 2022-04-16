---
title: PostgreSQL Error
date : "2022-04-14"
categories:
- [Setting]
---
# postgreSQL connection error

VSCode에서 postgreSQL 실행 중에 갑자기 이런 에러를 만났다.  

> Failed to retrieve unit state: Connection reset by peer
Failed to get properties: Connection reset by peer
> 

  

다시 재부팅 후, update 및 upgrade를 진행해도 다음과 같이 connection refused되면서 에러가 발생한다....   

![](/images/postgreSQLError/Untitled.png)

  

다음 코드들을 실행하다 보면 문제가 해결이 됐다..  

이유는 나도 몰라  

다시는 마주치고 싶지 않을 뿐... 😭

```python
sudo apt-get update && sudo apt-get install -yqq daemonize dbus-user-session fontconfig

sudo daemonize /usr/bin/unshare --fork --pid --mount-proc /lib/systemd/systemd --system-unit=basic.target

exec sudo nsenter -t $(pidof systemd) -a su - $LOGNAME

snap version
```

나는 저 4개 중에 차례대로 하다가 마지막 **`snap version`**에서 에러가 잡혔다.  

(저게 다 해야 에러가 잡히는 건지 이것 중에 되는 게 있을 거야 인지 모르겠지만 혹시 지나가다가 제 글을 보고 이유를 아는 사람 있다면 제발 알려줘요,,)

참고 : [https://gist.github.com/alyleite/ca8b10581dbecd722d9dcc35b50d9b2b](https://gist.github.com/alyleite/ca8b10581dbecd722d9dcc35b50d9b2b)