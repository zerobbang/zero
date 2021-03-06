---
title: PostgreSQL (WSL2)
date : "2022-04-13"
categories:
- [Setting]
---

π [μ°Έκ³  λΈλ‘κ·Έ](https://dschloe.github.io/sql/postgreslq_wsl2/)  

  

- WSL ν°λ―Έλμμ μ§ν
- Ubuntu ν¨ν€μ§ μλ°μ΄νΈ λ° μκ·Έλ μ΄λ μ§ν

    ```powershell
    sudo apt-get update && sudo apt-get upgrade
    ```
    
    ---

  

- PostgreSQL μ€μΉ

    ```powershell
    sudo apt install postgresql postgresql-contrib
    
    # λ²μ  νμΈ
    psql --version
    ```

- DBμ μ κ·Ό κ°λ₯νλλ‘ νμ±ν

    ```powershell
    # μν νμΈ
    sudo service postgresql status
    
    # νμ±ν
    sudo service postgresql start
    
    # μ’λ£
    sudo service postgresql stop
    ```

- μ¬μ©μ κ³μ  μ€μ 

    ```powershell
    sudo passwd postgres
    ```

---

   

### pgAdmin μ€μΉ

- [pgAdmin](https://www.pgadmin.org/download/pgadmin-4-windows/) β μ΅μ  λ²μ  pgAdmin 4 v6.8
- μ€μΉ μ κ΄λ¦¬μλ‘ μ€ν λ° **install for all users**λ‘ μ€μΉ μ§ν
- μλ² μ€μ νκΈ°
    - Servers β Register β Server...
    
    ![](/images/PostgreSQL/Untitled.png)
    
    - General Tab β test
        
        ![](/images/PostgreSQL/Untitled%201.png)
        
    - Connection β Password μλ ₯, Host name 127.0.0.1
        
        ![](/images/PostgreSQL/Untitled%202.png)
        
        λ§μ½ μλ¬κ° λλ€λ©΄ λ€μκ³Ό κ°μ΄ μ§ννλ€.  
          
        service νμ±νλ μνμμ λ€μ μ½λ μλ ₯
        
        ```powershell
        $ sudo -u postgres psql -c "ALTER USER postgres PASSWORD '<new-password>';"
        ```
        
        new-password μ μμ μ λΉλ° λ²νΈ μλ ₯  
          
        λ€μ λ°κΎΌ λΉλ°λ²νΈ μλ ₯νκ³  save
        
        ![](/images/PostgreSQL/Untitled%203.png)
        

  

### DB μμ± λ° νμΈ

- Database μ°ν΄λ¦­ β Create

![](/images/PostgreSQL/Untitled%204.png)

![](/images/PostgreSQL/Untitled%205.png)

- dataengineering λΈλ β shemas β public β Tables μ°ν΄λ¦­ β Create - Table μ ν
    - General λ€μκ³Ό κ°μ΄ μ€μ 
        
        ![](/images/PostgreSQL/Untitled%206.png)
        
    - Columns λ€μκ³Ό κ°μ΄ μ€μ 
        
        ![](/images/PostgreSQL/Untitled%207.png)
        

### psql μμ μΏΌλ¦¬ μ€ν

- psql μ€ννλ©΄ λ€μκ³Ό κ°μ΄ λλ€.
    
    ```powershell
    $ sudo -u postgres psql
    psql (12.9 (Ubuntu 12.9-0ubuntu0.20.04.1))
    Type "help" for help.
    
    postgres=#
    ```
    
- DB μ‘°ν

    ```powershell
    postgres=# \l
    
    List of databases
          Name       |  Owner   | Encoding | Collate |  Ctype  |   Access privileges
    -----------------+----------+----------+---------+---------+-----------------------
     dataengineering | postgres | UTF8     | C.UTF-8 | C.UTF-8 |
     postgres        | postgres | UTF8     | C.UTF-8 | C.UTF-8 |
     template0       | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +
                     |          |          |         |         | postgres=CTc/postgres
     template1       | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +
                     |          |          |         |         | postgres=CTc/postgres
    (4 rows)
    ```

- DB μ°κ²° ν νμ΄λΈ μ‘°ν

    ```powershell
    postgres=# \c dataengineering
    You are now connected to database "dataengineering" as user "postgres".
    
    dataengineering=# \dt
             List of relations
     Schema | Name  | Type  |  Owner
    --------+-------+-------+----------
     public | users | table | postgres
    ```


---
**_<span style="color:#4682B4;"> μ΄ λΈλ‘κ·Έλ νΌμ κ³΅λΆνλ©° κΈ°λ‘νλ λΈλ‘κ·Έλ‘ μλͺ»λ μ λ³΄μ λν μκ²¬μ κ²©νκ² νμν©λλ€.π€© </span>_**