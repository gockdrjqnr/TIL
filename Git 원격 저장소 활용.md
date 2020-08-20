# Git 원격 저장소 활용

Git 원격 저장소 기능을 제공 해주는 서비스를 gitlab, bitbucket, github 등이 잇다.

# 0. 원격 저장소 설정

```bash
$ git remote add origin {url}
$ git remote add origin http://github.com/gockdrjqnr/TIL.git
```

* git, 원격 저장소를 추가하고(`add`)하고 `origin`이라는 이름으로 `url`으로 설정

  git아 원격 저장소를 추가해줘 origin이라는 이름으로 url을

* 설정된 저장소를 확인하기 위해서는 아래의 명령어를 실행

```bash
$ git remote -v
origin  https://github.com/gockdrjqnr/TIL.git (fetch)
origin  https://github.com/gockdrjqnr/TIL.git (push)
```

원격 저장소에 push

```bash
$ git push origin master
```

