---
title: 깃허브 블로그 - GA , 댓글 기능, 이메일 기능 추가
categories:
- Github_Blog
excerpt: |
  지킬 기능 추가하기 - Alembic Theme
feature_text: |
  ## 지킬 테마 Alembic에 기능 추가하기
  나만의 블로그 만들기 위한 두번째 이야기
feature_image: "https://user-images.githubusercontent.com/18584136/107729908-79daaa80-6d35-11eb-95aa-41ab8624639b.jpg"
image: ""
---

안녕하세요! 하파카입니다.

지킬테마 적용 이후 홈페이지 내에 있는 기능들을 사용 할 수 있도록 설정 해주는 법을 알려드릴게요. 

아래 내용들은 공통으로 적용될 수 도 있지만, alembic 테마 기준으로 알려드리니 다른 테마의 경우 약간 다를 수 있다는 점! 유의해주세요 :)

첫번째 이야기를 잘 따라오셨다면 아마 소스를 로컬에 받으셨을 거에요! 
소스를 잘 보시다보면, 구글 통계 추가하는 부분이랑 댓글 추가 하는 기능, 메일 보내는 form 등을 확인하셨을 거에요. 전부 개인 계정을 가지고 설정을 해줘야 블로그에 적용 시킬 수 있습니다. 구글 통계 연결 부터 볼게요.

# 구글 애널리틱스 추가

구글 통계 추가하는 법은 생각보다 어렵지 않아요. 요약하자면 계정 만들고, config.yml 파일에 아이디 값을 입력해주시면 됩니다:) 

1. 우선 [구글 애널리틱스](https://www.google.com/analytics/web/?hl=ko&pli=1)에 들어가세요.
2. 사용할 계정을 가지고 로그인을 한 후 무료로 계정 만들기를 해줍니다. 
3. 이름을 설정 하고 나면 id를 발급 받으실 수 있습니다. 
4. 발급받은 id를 가지고 config.yml 파일내에 `google_analytics: "ID"` 항목에 넣어 주시면 됩니다.
5. 그 밑에 항목의 경우 `google_analytics_anonymize_ip: "false"` 로 설정해 주시면 됩니다. 
6. 이렇게 설정을 하고 나면 이전에 만든 구글 애널리틱스 계정 안에서 통계가 잡히는 것을 확인 하실 수 있습니다.

id를 가지고 편하게 구글 통계를 이용해보세요! 개인적으로 네이버 애널리틱스보다는 구글 애널리틱스가 간편하고 상세한것 같네요.. ㅎㅎ 지킬테마의 경우 구글 애널리틱스를 지원해주고 있기 때문에 선택의 여지가 없을 것 같네요.

# 댓글 기능 추가

댓글 기능을 추가해주기 위해서는 disqus에 가입하고, 사이트 도메인을 입력해 주시면 됩니다. disqus 는 무료로 사용 가능하기 때문에 왠만하면 설정해주시는게 좋을 것 같습니다. 

1. 우선 [disqus](https://disqus.com/)에 가입해주세요.
2. 가입시 사이트 도메인와 shortname 을 등록하게 됩니다.
3. 이때 등록한 shortname을 가지고 config.yml 파일에 입력해줍니다.
4. 커맨드 아웃된 부분 중 `disqus: "shortname"` 부분이 있으니 해당 부분에 등록한 shortname을 입력해주시면 됩니다.
5. 그리고 나서 config.yml 파일내에  `# 6. Jekyll collections settings` 부분에 가면, 댓글을 사용하는 페이지 설정쪽에 `comments: true` 항목을 추가해주시면됩니다.
   ```
   defaults:
  - scope:
      path: ""
      type: "posts"
    values:
      layout: post # Set the default layout for posts
      comments: true
    ```
6. 이렇게 설정해주시면 아래처럼 댓글 기능을 사용하실 수 있습니다! :) 


# 이메일 기능 추가

이메일 기능은 Formspree를 사용하고 있다면 간단한 계정 생성으로 사용이 가능합니다. alembic 테마의 경우 제 블로그의 [Contact](http://hapakacode.com/elements/) 페이지처럼 메일을 남기는 용도로 사용하고 있습니다. 

1. 우선 [Formspree](https://formspree.io/)에 들어가 계정을 만들어줍니다.
2. +New Form 을 눌러 사이트에서 쓸 form을 생성해줍니다. 
3. Formspree에서 기능을 사용할 도메인와 target email을 등록해줍니다.
4. 생성된 From Details 에서 Integration을 누르면 자신의 form의 endpoint를 확인 할 수 있습니다.
5. 이 endpoint를 가지고 _includes/site-form.html 에 입력해줍니다.
6. 파일을 열게되면 제일 마지막 부분 script 내  `form.setAttribute("action", "https://formspree.io/" + unraveledEmail);`에 자신의 endpoint값으로 교체해주시면 됩니다. 
7. 여기까지 마무리하시면 이메일 보내기 기능까지 추가가 완료됩니다!

위에 단계들을 다 따라오셨다면, 블로그 내에 활용 가능한 기본 기능들은 거의 다 완료하게됩니다. 

# 결론

오늘은 지킬테마에 내장된 기본 기능들에 대해 추가 해봤습니다. 기능 중에 제대로 구현되지 않는 부분이 생기면 다음에서 사이트 등록을 할때 거절당할 수 있기 때문에 만약 위의 기능들을 사용할 예정이시라면 꼭 설정 해주시고 다음 단계로 넘어가시길 추천드릴게요. 

다음 글은 검색 최적화에 대한 이야기를 나눌까 합니다. 구글, 네이버, 다음 사이트에서 사이트 등록하면서 생긴 에피소드 및 주의사항 전달해드릴게요. 

기대해주세욧 -! :) 


from 하파카

<br>