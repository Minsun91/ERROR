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




