---
title: Docker μ€μΉ
date : "2022-04-12"
categories:
- [Setting]
---


π [μ°Έκ³  λΈλ‘κ·Έ](https://dschloe.github.io/settings/windows_docker_install/)  

  

- Windows PowerShell β κ΄λ¦¬μ κΆνμΌλ‘ μ€ν
- wsl2κ° μ€μΉλμ΄ μμ΄μΌ νλ€. [λ€μμ μ°Έκ³ ](https://www.lainyzine.com/ko/article/how-to-install-wsl2-and-use-linux-on-windows-10/)

```powershell
wsl --set-default-version 2
```

wsl λ²μ  2 νμΈνκ³  Doker μ€μΉ μμνκΈ°  

---

  

### Docker  λ€μ΄

[μ¬κΈ°](https://www.docker.com/products/docker-desktop/)μμ λ€μ΄ μμ  

![](/images/Docker_set/Untitled.png)

μμ  νκ²½κ³Ό λ§λ λ²μ μ λ€μ΄ λ°λλ€. (λλ Windows μ§ν)  

Docker Desktop Installer.exe μ€ννμ¬ μ€μΉλ₯Ό μ§ννλ€.  

**Configuration** μ°½μμ Install required Windows components for WSL 2 μ Add shortcut to desktop μ²΄ν¬νμ¬ μ€μΉλ₯Ό κ³μ μ§ννλ€.  

μ€μΉκ° μλ£ λλ©΄ μ¬ μμμ μ§ννλ€.  

μ¬ μμ ν, μ¬ μ μ νλ©΄ μ½κ΄ λμ μ°½μ΄ λνλκ³  λμ μ²΄ν¬ ν Accept λλ¬ μ€μΉλ₯Ό μλ£νλ€.

   

---

  

### Docker μ΄κΈ° μ€μ 

νμ κ°μ ν Docker μ€ννμ¬ Start λλ¬ Tutorial μ§ν  

Proceed to Docker Desktop λλ¬ Docker μ€ν  

- μ€λ₯Έμͺ½ μλ¨ βοΈ νκ²½ μ€μ 

General β Use the WSL 2 based engine  βοΈ  β Appply & Restart  

![](/images/Docker_set/Untitled%201.png)

Resource β WSL Integration β Enable Integration with my default WSL distro βοΈ β Apply & Restart  

![](/images/Docker_set/Untitled%202.png)

  

---

  

### Docker μ€μΉ νμΈ

- Windows PowerShell β κ΄λ¦¬μ κΆνμΌλ‘ μ€ν
- λ€μ μ½λλ‘ Docker μ μ© λ¨Έμ  μ€ν νμΈ

```powershell
$ wsl -l -v
```

![](/images/Docker_set/Untitled%203.png)

- Docker μλ²μ ν΄λΌμ΄μΈνΈ μ λ³΄ νμΈ

```powershell
$ docker version
```

![](/images/Docker_set/Untitled%204.png)

- Docker μ€ν μ€μΈ μ»¨νμ΄λ νμΈ
    - μ€ν μ€μΈ μ»¨νμ΄λκ° μλ κ²½μ°
    
    ```powershell
    $ docker ps
    CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
    ```
    
    - μ€ν μ€μΈ μ»¨νμ΄λκ° μλ κ²½μ°(nginx μ€ν)
    
    ```powershell
    $ docker ps
    CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                  NAMES
    762037058fc4   nginx:latest   "/docker-entrypoint.β¦"   3 seconds ago   Up 2 seconds   0.0.0.0:4567->80/tcp   serene_lalande
    ```

  

- Docker μ€ν μ€μΈ μ»¨νμ΄λ μ­μ   
    -f λ€μμ μμ μ CONTAINER ID μλ ₯  

    ```powershell
    $ docker rm -f 762037058fc4
    762037058fc4
    ```

  
  
---

**_<span style="color:#4682B4;"> μ΄ λΈλ‘κ·Έλ νΌμ κ³΅λΆνλ©° κΈ°λ‘νλ λΈλ‘κ·Έλ‘ μλͺ»λ μ λ³΄μ λν μκ²¬μ κ²©νκ² νμν©λλ€.π€© </span>_**