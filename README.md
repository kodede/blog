# Kodede Blog generator by Hexo

> NodeJs 기반의 [Hexo.io](https://hexo.io/)로 작성된 static html generator 입니다. 이곳 솔루션을 이용해 [블로그](http://kodede.github.io/) 를 위한 static html 을 생성합니다. 기본 테마는 [여기](https://github.com/kodede/hexo-theme-overdose)를 사용합니다.

블로그 주소: [kodede.github.io/](https://kodede.github.io/)

## Quick Start

```
$ git clone https://github.com/kodede/blog.git
$ cd blog
$ yarn install
$ g submodule add git@github.com:kodede/hexo-theme-overdose.git themes/overdose
```

### Workflow

1.  실행 `yarn start`
2.  새글 작성 `yarn post <글 이름>`
3.  생성 `yarn gen`
4.  게시 `yarn deploy`

## 설치

기본적으로 dev 환경에서 node, yarn 이 설치되어 있어야 합니다. 다음과 같이 git 작업디렉토리를 내려받고 package 를 설치합니다.

```
$ git clone https://github.com/kodede/blog.git
$ cd blog
$ yarn install
```

패키지 설치가 완료되면 블로그에 사용할 theme 을 설치합니다. theme 은 git 의 submodule 로 `themes/overdose` 위치에 내려받습니다.

```
$ g submodule add git@github.com:kodede/hexo-theme-overdose.git themes/overdose
```

설치가 완료되면 다음과 같은 구조의 directory 가 생성됩니다. `source` 디렉토리에 새로운 글이 채워지고 `public`에 static html 이 생성됩니다.

```
blog
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── .gitmodules
├── _config.yml
├── themes
│   └── overdose
├── scaffolds
│   └── draft.md
│   └── page.md
│   └── post.md
├── public
└── source
    └── _posts
```

## 실행

현재 게시하려는 웹사이트를 확인할 수 있습니다.

```
$ yarn start

yarn run v1.3.2
$ hexo server
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```

## 새글 작성

`yarn post` 명령으로 글 제목을 입력하면 새글을 위한 mockdown templete 이 만들어 집니다. 이 파일을 편집하여 글을 작성합니다. 작성을 하면서 `yarn start` 명령으로 편집중인 페이지를 확인할 수 있습니다.

```
$ yarn post "글제목을 입력합니다"

yarn run v1.3.2
$ hexo new post '글제목을 입력합니다'
INFO  Created: ~/projects/blog/source/_posts/글제목을-입력합니다.md
✨  Done in 1.04s.
```

## 사이트 생성

글 작성이 완료되면 배포를 위해 `yarn gen` 명령으로 HTML 파일을 생성합니다. `public` 디렉토리에 정적인 파일이 생성되나, 해당 git repository 에는 `source` 폴더 아래로 생성된 글의 원본만 commit 합니다.

```
$ yarn gen

yarn run v1.3.2
$ hexo generate
INFO  Start processing
INFO  Files loaded in 976 ms
INFO  Generated: archives/index.html
INFO  Generated: 2018/04/26/hello-world/index.html

...

INFO  Generated: libs/spoqa-han-sans-kr/fonts/SpoqaHanSans/SpoqaHanSansThin.woff
INFO  146 files generated in 180 ms
✨  Done in 2.23s.
```

## 새글 게시

`yarn deploy`을 실행하여 `public` 디렉토리의 내용을 kodede.github.io 의 master branch 로 commit 해줍니다. commit 하면 github page 에 작성한 내용이 반영됩니다. (약간의 지연이 있습니다.)

```
$ yarn deploy

yarn run v1.3.2
$ hexo deploy
INFO  Deploying: git
INFO  Setting up Git deployment...
Initialized empty Git repository in /Users/daesungkim/projects/blog/.deploy_git/.git/
[master (root-commit) 941dc1b] First commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 placeholder
INFO  Clearing .deploy_git folder
...
```
