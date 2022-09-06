### fatal: 정방향이 불가능하므로, 중지합니다.  

도대체가 매 프로젝트때마다 만난다. 

원인은, 리모트 저장소가 로컬보다 앞서있을때 머지를 하려고 하면 충돌이 일어나서 안된다는 것으로   
아래와 같이 git config pull option을 설정해주면 된다고 한다. 

```
git pull --rebase

git config --unset pull.ff
// 또는
git config --unset --global pull.ff
```
충돌이 일어나도 오토 머지를 하거나 알아서 재구성해준다.   
고 하는데 되질 않는다. 😵‍💫

---

내 에러 내용 ⤵️   

<img width="607" alt="스크린샷 2022-08-12 15 48 15" src="https://user-images.githubusercontent.com/92393851/184366975-b3b42d87-6538-47e5-8981-8deefac9d5bc.png">
원격 저장소의 develop 브랜치에서 로컬 저장소의 FETCH_HEAD를 merge하는 것이 거부되었다.  
commit 히스토리가 서로 관련이 없다는 뜻이다.  

* pull명령어는 fetch + merge 작업을 한꺼번에 처리하는 명령어로, 지금 상황은 fetch만 되고 merge는 되지 않았다는 뜻이다.  
merge는 원격 저장소와 로컬 저장소가 공통으로 가지고 있는 commit지점이 존재해야 하는데, 공통으로 가지고 있는 commit지점이 존재하지 않으니 merge이 안된다.  

* FETCH_HEAD는 이름 없는 브랜치로 원격저장소에 있는 커밋을 로컬로 가져온다 

* Pull 명령어  
원격 저장소에 있는 내용을 가져올 뿐만 아니라, 자동으로 로컬 저장소에 merge. 
git pull  == git fetch + merge FETCH_HEAD

> 해결하려면 아래 두 방법 중 하나를 택한다.   
git clone 명령어를 통해 원격 저장소를 복제해온다.   
pull 명령어에 옵션을 추가해 강제로 pull 한다.    ```git pull origin (branchname) --allow-unrelated-histories```

--

### 현재 브랜치의 끝이 리모트 브랜치보다 뒤에 있으므로 업데이트가 거부되었습니다.  
푸시하기 전에 ('git pull ...' 등 명령으로) 리모트 변경 사항을 포함하십시오.  
자세한 정보는 'git push --help'의 "Note about fast-forwards' 부분을 참고하십시오.  

이것도 정방향 에러와 번갈아서 나오는 단골 에러
ㅗ 

```
git push -f -u origin <name of branch>
```
이걸로 하니 됐다. 

<img width="612" alt="스크린샷 2022-08-17 05 59 53" src="https://user-images.githubusercontent.com/92393851/185049639-fb1f42ab-9dca-4621-b543-842003401ca7.png">

https://stackoverflow.com/questions/20467179/git-push-rejected-non-fast-forward


---

### gitignore 적용

이미 깃에 올라간 파일을 추후에 .gitignore에 추가하려고 하면 적용이 안된다!  
숨기고 싶은 파일은 깃허브에서 지우고, 로컬는 있는 상태에서 .gitignore에 추가하고 add, commit, push 하면 숨겨진채로 잘 반영된다!  

혹은 

```
//git의 캐시가 문제가 되는거라 아래 명령어로 캐시 내용을 전부 삭제후 다시 add All해서 커밋하시면 됩니다

git rm -r --cached .
git add .
git commit -m "fixed untracked files"
```
간단히 끝 ⭐️

---

### git conflict 해결 후 (vsc)
```
git add 충돌파일
git merge --contine
```

참조: https://velog.io/@younoah/git-conflict-%EC%B6%A9%EB%8F%8C-%ED%95%B4%EA%B2%B0%ED%95%98%EA%B8%B0
