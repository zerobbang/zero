---
title: 크롤링 기초 - BeautifulSoup4
date : "2022-04-24"
categories:
- [Python]
tags:
- [Crawling]
---


📖 [공식문서](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#quick-start)

- 사전 세팅

    ```powershell
    # 가상 환경 설정
    virtualenv venv
    source venv/Scripts/activate
    
    # 라이브러리 설치
    pip install beautifulsoup4
    pip install numpy pandas matplotlib seaborn
    pip isntall requests
    
    ```

  

- 크롤링할 페이지 선택 (예시 네이버)
- 우클릭 → 검사 → Network 에서 Request Method :  GET 형태의 홈페이지 가능 (GET이 아닐 경우 다른 공부가 필요)

![](/images/crawling/Untitled.png)

  

- referer 과 user-agent 를 복사하기
![](/images/crawling/Untitled1.png)
![](/images/crawling/Untitled2.png)
나는 정상적인 브라우즈를 활용해서 접근했다고 알려주기 위하함.

- 기본 코드

    ```python
    # 라이브러리 불러오기
    import requests
    from bs4 import BeautifulSoup
    
    def main():
        HEADER = {
            'referer' : '위에서 복사'
            'user-agent' : '위에서 복사'
        }
        
        url = ''
        req = requests.get(url=url, headers=HEADER)
        # check
        # print(req.status_code)
    
        soup = BeautifulSoup(req.text, 'html.parser')
    
        함수(soup)
    
    if __name__=="__main__":
        main()
    ```

  

soup를 통해서 해당 웹 페이지에서 text를 가져온다.  

가져온 다음 원하는 데이터를 뽑는 함수를 만들어 적용하면 된다.  

  

  

---

  

## Quick Start 실습 해보기 (공식 문서)

- index 파일 만들기

    ```python
    <!DOCTYPE html>
    <html>
    <head>
        <title>The Dormouse's story</title>
    </head>
    <body>
    <p class="title"><b>The Dormouse's story</b></p>
    
    <p class="story">Once upon a time there were three little sisters; and their names were
        <a href="http://example.com/elsie" class="sister" id="link1">Elsie</a>,
        <a href="http://example.com/lacie" class="sister" id="link2">Lacie</a> and
        <a href="http://example.com/tillie" class="sister" id="link3">Tillie</a>;
        and they lived at the bottom of a well.</p>
    
    <p class="story">...</p>
    ```

  

### 간단히 실습하기
- 기본 코드
    ```python
    # 기본 코드 및 전체 불러오기
    from bs4 import BeautifulSoup
    
    soup = BeautifulSoup(open("review.html"), "html.parser")
    
    # html 파일 전체
    print(soup.prettify())
    ```

.prettify( ) : index 파일의 내용을 전체 불러온다.  

- title 추출 → class 등 가능

    ```python
    #title
    
    # title tag 전체
    print(soup.title)
    
    # title tag 객체 이름
    print(soup.title.name)
    
    # title 문자열
    print(soup.title.string)
    
    # 상위 tag 이름
    print(soup.title.parent.name)
    ```

- tag a or p

    ```python
    # body tag
    
    # p tag 전체 ( 맨 위 )
    print(soup.p)
    
    # p tag의 class 이름 ( 맨 위 )
    print(soup.p['class'])
    
    # a tag 전체 ( 맨 위 )
    print(soup.a)
    
    # 맨 위에만 불러오기 싫으면 find_all 사용 하거나 find 이용 해서 특정한 값만 가져 오기.
    
    # a tag 전체 find_all
    print(soup.find_all('a'))
    
    # a tag 특정 id
    print(soup.find(id='link3'))
    
    # p find 이용 해보기
    print(soup.find_all('p'))
    print(soup.find('p',class_='story'))
    ```

- 부분 불러와서 원하는 값 추출

    ```python
    for link in soup.find_all('a')
        print(link.get('href'))
    
    # text만 추출
    print(soup.get_text())
    ```
  
---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**