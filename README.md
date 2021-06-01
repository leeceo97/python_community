# 캠퍼스픽 API (Django REST Framework)

### ✏ Description

- (세션을 이용한)유저의 회원가입, 로그인 기능
- 게시판(글쓰기, 읽기)
- 댓글(ForeignKey사용)
- 순수하게 장고에 처음 제공되는 기능만을 사용하여 복습용으로 제작하였습니다.


### Model Composition

```python
User {
	id: number;        // 숫자, 자동 생성
	username: string;     // 문자열, 필수값
	useremail: string;     // 문자열(이메일 형식), 필수값
  password: string;  // 문자열, 필수값
  created_at: date;  // 날짜형, 생성된 시간(자동 생성)
}

Board {
    id: number;        // 숫자, 자동 생성
    contents: string;   //문자열, 필수값, 게시판 내용
    title: string;    // 문자열, 필수값, 게시판 제목
    writer:; // 외래키, 'accounts.User', 게시판 작성자
    tags:; // 외래키, 'tag.Taf', 게시글 태그
    created_at: date; //날짜형, 생성된 시간(자동 생성)
    updated_at: date; //날짜형, 수정된 시간(자동 생성)
}

Comment{
    id: number;     //숫자, 자동생성
    author:;      //외래키, 댓글 작성자
    post:;    //외래키, 댓글 작성 게시판
    comment: string;   //문자열, 필수값, 댓글 내용
    created_at: date; //날짜형, 생성된 시간(자동 생성)
}

Tag{
    id: number; //숫자, 자동생성
    name:string; //문자열, 태그명
    created_at: date; //날짜형, 생성된 시간(자동생성) 
}

```

### ⚙ Envirionments (python 3.8.0)

> pip install django==3.1.7


❗ And, you have to create `.env` file in root.

```
Project tree
------------
root
├── venv
├── README.md
├── community
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── db.sqlite3
├── manage.py
└── accounts
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── forms.py
    ├── tests.py
    ├── urls.py
    └── views.py
└── boards
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── forms.py
    ├── tests.py
    ├── urls.py
    └── views.py
└── tag
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── tests.py
    └── views.py
```

<br>



### ▶ Execution

> pip install httpie

```python
python manage.py makemigrations

python manage.py migrate

# execute django web server
python manage.py runserver

# if you see error "No such table Todo",
## python manage.py makemigrations todo
## python manage.py migrate
## python manage.py runserver

""" in another cmd """
# please user httpie for test

```

<br>


### ▶ 후기
django의 기본적인 데이터 구조를 제대로 학습하지 않고 따라치다가 
djangorestframework학습중 간단한 부분에서 버벅이는 나를보고
초심을 되찾을겸 블로그 게시와 함께 복습을 했는데 생각보다 어려움을
느끼는 나를 보고 역시 공부에 왕도는 없다는 생각을 하게 되었다...
기존에 구현하지 않았던 댓글까지 구현하며 그래도 장고의 순수한 로직을
다시한번 느끼고 얼마나 많은것을 제공해주는 좋은 프레임워크라는것을
다시한번 알게된 소중한 기회였다!! 
