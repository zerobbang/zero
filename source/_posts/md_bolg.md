---
title: git blog에 R 마크다운 올리기
date : "2022-04-09"
categories:
- [Setting]
---


- R studio에서 마크다운 파일 들어가기
- 다음 사진과 같이 output 설정을 해주기
    
    ![](/images/md_bolg/Untitled.png)
    

```r
output:
	html_document:
		keep_md: true
```

- 그리고 Knit 눌러주면 md파일이 만들어진 걸 확인할 수 있다.

- 그 다음 블로그 파일로 들어가서 다음과 같이 파일들을 넣어주기
1. md파일 source/_posts 밑으로 넣어주기
2. (파일명)_files파일을 source밑으로 images파일을 생성하여 넣어주기
    
    ![](/images/md_bolg/Untitled%201.png)
    
    ![](/images/md_bolg/Untitled%202.png)
    

- 그 다음 md파일로 가서 그림의 경로 앞에 “/images/” 넣어주기

![](/images/md_bolg/Untitled%203.png)

- 참고

[블로그](https://dschloe.github.io/settings/hexo_img/)