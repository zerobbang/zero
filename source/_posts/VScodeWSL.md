---
title: Install VScode (wsl)
date : "2022-04-19"
categories:
- [Setting]
---


π [μ°Έκ³  λΈλ‘κ·Έ](https://dschloe.github.io/settings/vscode_wsl2/)  

  

- [vs code μ€μΉ](https://code.visualstudio.com/download) (**System Installer**λ‘ μ€μΉ)
- μ€μΉ μ νκ²½ λ³μ μ²΄ν¬ νμΈ
    
![](/images/VScodeWSL/Untitled.png)
    
- μ€μΉ μλ£ ν **μ¬λΆν** νμ.

---

### Remote WSL μ°λ

- Extention λ²νΌ ν΄λ¦­ β  Remote WSL κ²μ ν μ€μΉ
    
![](/images/VScodeWSL/Untitled%201.png)
  
- μ€μ§ μλ£ μ  λ€μ μ¬ν­λ€μ λͺ¨λ μ²΄ν¬ ν Mark Done ν΄λ¦­
    
![](/images/VScodeWSL/Untitled%202.png)

- Open Foler β airflow_test ν΄λ μ€ν ( WSLμμ μ€μΉνλ νμΌ )
- Menu β Terminal β WSL μ ν
    
![](/images/VScodeWSL/Untitled%203.png)
    
- μλ² λλ €λ³΄κΈ° (airflow)
    
    ```powershell
    # κ°μ νκ²½ μ€μ 
    source venv/bin/activate
    # μλ² μ€ν
    airflow webserver -p 8081
    ```
    
![](/images/VScodeWSL/Untitled%204.png)

---
**_<span style="color:#4682B4;"> μ΄ λΈλ‘κ·Έλ νΌμ κ³΅λΆνλ©° κΈ°λ‘νλ λΈλ‘κ·Έλ‘ μλͺ»λ μ λ³΄μ λν μκ²¬μ κ²©νκ² νμν©λλ€.π€© </span>_**