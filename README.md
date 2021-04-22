# About_Git

<h1>목차</h1>
<ul>
  <li>1.기본 원리 </li>  
  <li>2.시나리오 실행 </li>
</ul>

<h2>1. git 원리(흐름)</h2>
    <p>git은 크게 4가지의 저장소로 분리되어 있다.</p>
    <ul>
        <li>workspace : 현재 작업중인 장소(코딩하고 있는곳)</li>
        <li>staging area : workspace에서 commit하기 이전에 거쳐가는 장소</li>
        <li>local repository : staging area에 있는 파일을 commit을 통하여 버전을 만든 장소</li>
        <li>remote repository : local이 아닌 원격 저장소</li>
    </ul>
    <br>
    <p>git의 흐름 : workspace --add--> staging area --commit--> local repository --push--> remote repository</p>
    <p>remote repository --clone or pull --> local repository</p>
    <br>
    <p>git의 사용 목표로는 workspace에서 작업을 하여 add를 통하여 staging area에 등록을 시킨다. 그 후 commit을 통하여 local repository에 등록
        하는데 이를 <strong>버전을 만들었다고 한다.</strong> 버전에서 다음 버전으로 계속 나아가며 특정 버전으로 이동을 할수 있기때문에 git의 주 사용이유
        는 <strong>버전관리에 있다.</strong> push를 통해 버전들을 remote repository로 등록할수 있으며 이를 <strong>백업했다고 표현한다.</strong><br>
        다른 사람이 fork나 clone을 통하여 해당 remote나 local repository를 가져와 작업을 하여 pull request를 통하여 작업에 기여를 한다.<br>
        이를 <strong>협업 한다고 한다.</strong><br>
        <strong>즉 git은 버전관리, 백업, 다수와의 협업을 위하여 사용된다.</strong>
  </p>
  <hr>
  <h2>2. 시나리오</h2>
    <ul>
        <li>1. Admin remote repository의 master를 기준으로 개발자들은 fork하여 사용한다</li>
        <li>2. 개발자 A는 master 브랜치에서 devel 브랜치를 만들어 기능에 따라 세부적으로 작업한다.</li>
        <li>3. devel 브랜치에서 여러 기능에따라 브랜치를 새로 만들었지만 conflict 발생(kdiff3 mergetool 사용).</li>
        <li>4. devel에서 파생된 브랜치들을 merge하고 Admin으로 pull request.</li>
        <li>5. Admin과 local의 pull을 통한 연동</li>
    </ul>

<p><strong>Admin : bae0258, fork 사용자 : dongbae129</strong></p>


![K-005](https://user-images.githubusercontent.com/36911316/115716711-6b9faf00-a3b4-11eb-819e-196a59070c6e.png)
<p><strong>1. Admin repository에서 git-flow-test 저장소를 fork 하였습니다. </strong> </p><br><br>

![K-006](https://user-images.githubusercontent.com/36911316/115716988-bcafa300-a3b4-11eb-9622-47551ed12a46.png)<br>
<strong>2. code에서 url을 받아와 clone하고 vscode에서 열어줍시다. </strong><br><br><br>

![K-007](https://user-images.githubusercontent.com/36911316/115716994-bf11fd00-a3b4-11eb-9d38-da40647caa74.png)<br>
<strong>3. clone으로 받아올경우 자동으로 origin이라는 이름으로 연결됩니다. 나중에 원본 저장소랑 맞추기 위해 real이라는 이름으로
        원본저장소도 remote add 해줍시다.</strong>
 <br><br><br>
![K-008](https://user-images.githubusercontent.com/36911316/115717048-c76a3800-a3b4-11eb-937a-f31f83fea9e0.png)<br>
<strong>4. main 브랜치에서 devel 브랜치를 생성하여 이동후 devel.js라는 파일을 다음과 같이 작성하고 add,commit까지 해줍니다.</strong>
 <br><br><br>
![K-009](https://user-images.githubusercontent.com/36911316/115717049-c802ce80-a3b4-11eb-904f-09b17df9cd0a.png)
<br><br><br>

![K-010](https://user-images.githubusercontent.com/36911316/115717053-c802ce80-a3b4-11eb-9d82-7ce642a35296.png)<br>
<strong>5. 개발도중 afunc라는 기능이 필요해져 devel에서 a_func 브랜치를 생성하여 이동 후 다음과 같이 작성하였습니다. add,commit까지 해줍니다 <br><br><br></strong>

![K-011](https://user-images.githubusercontent.com/36911316/115717056-c89b6500-a3b4-11eb-8858-d1554e22057b.png)
<br><br><br>
![K-012](https://user-images.githubusercontent.com/36911316/115717059-c89b6500-a3b4-11eb-9f36-4c007d27090e.png)<br>
<strong>6. 갑자기 bfunc라는 기능이 필요해서 devel에서 b_func 브랜치를 생성하여 다음과 같이 작성 후 add,commit까지 해줍니다. <br><br><br></strong>

![K-013](https://user-images.githubusercontent.com/36911316/115717062-c933fb80-a3b4-11eb-931e-24e28d9f3414.png)<br>
<strong>7. afunc가 bfunc보다 먼저 개발이 완료됐고 더 시급하여(가정입니다) afunc를 먼저 devel에서 merge를 해줍니다. <br><br><br></strong>
 
![K-014](https://user-images.githubusercontent.com/36911316/115717023-c3d6b100-a3b4-11eb-91c9-ddb23fa93188.png)<br>
<strong>8. 그 후 bfunc 개발이 완료되어 devel에서 b_func를 merge를 하지만 conflict가 발생합니다. <br><br><br></strong>

![K-015](https://user-images.githubusercontent.com/36911316/115717028-c46f4780-a3b4-11eb-80ca-91ce785e7b18.png)<br>
<strong>9. mergetool인 kdiff3을 이용하여 conflict를 해결해 보겠습니다. <br>
        conflict는 devel.js에서 발생하였습니다. A는 기존 devel.js(a_func와 merge하기 전), B는 a_func와 merge한 devel.js, C는 merge 하려고 하는
        b_func의 devel.js. 셋 중에 하나를 선택해도 되지만 B와 C를 적절히 합칠수 있기 때문에 output에서 다음과 같이 수정하였습니다. 그 후 ctrl+s 저장 후 닫아주면
        conflict가 해결됩니다. <br><br><br></strong>
 
![K-016](https://user-images.githubusercontent.com/36911316/115717031-c46f4780-a3b4-11eb-9715-eb980442707c.png)<br>
<strong>10. orig파일은 conflict난 원본 파일이며 필요없으니 삭제 해줍시다. <br><br><br></strong>
 
![K-017](https://user-images.githubusercontent.com/36911316/115717035-c507de00-a3b4-11eb-8b95-61174df238ee.png)<br>
<strong>11. conflict 해결했으니 다시 commit을 해줍니다. <br><br><br></strong>

![K-018](https://user-images.githubusercontent.com/36911316/115717039-c5a07480-a3b4-11eb-9db5-571c3578f28b.png)<br>
<strong>12. 이제 remote에 백업하고 Admin으로 pull request를 해줍시다. push 할때는 자신의 remote로 devel 브랜치를 push 합니다. <br> <br><br></strong>

![K-019](https://user-images.githubusercontent.com/36911316/115717040-c5a07480-a3b4-11eb-8ba9-388b19cf18ca.png)<br>
<strong>13. 원격저장소를 확인하면 다음과 같이 Compare & pull request 버튼이 활성화 됩니다. 클릭해줍시다. <br><br><br> </strong>

![K-020](https://user-images.githubusercontent.com/36911316/115717041-c5a07480-a3b4-11eb-9a52-3790b1f466d3.png)<br>
<strong>14. fork 저장소의 devel 브랜치를 Admin 저장소의 main에 pull request를 보내는 것입니다. 설명 적어주고 요청 보냅시다. <br><br><br></strong>

![K-028](https://user-images.githubusercontent.com/36911316/115717044-c6390b00-a3b4-11eb-8710-8b623360b66f.png)<br>
<strong>15. dongbae129(fork 사용자) 에서는 다음과 같이 conflict 여부와 commit 사항을 보여줍니다. <br><br><br></strong>

![K-029](https://user-images.githubusercontent.com/36911316/115717045-c6390b00-a3b4-11eb-8a67-c18a17dc6907.png)<br>
<strong>16. bae0258(Admin) 에서는 다음과 같이 pull request한것을 merge할지 여부를 물어봅니다.(main --merge-- devel). 클릭해주고 confirm 해줍니다. <br><br><br></strong>

![K-031](https://user-images.githubusercontent.com/36911316/115717046-c6d1a180-a3b4-11eb-8b9e-5c8f147afeeb.png)<br>
<strong>17. pull request가 성공적으로 완료되어 Admin 저장소에 main으로 devel 브랜치가 merge 되었습니다. <br><br><br></strong>

![K-032](https://user-images.githubusercontent.com/36911316/115717047-c76a3800-a3b4-11eb-8440-16f9721c978c.png)<br>
<strong>18. 마지막으로 local로 돌아가서 Admin의 main 브랜치를 pull하여 local main과 동기화 해줍니다. <br><br><br></strong>

        -끝-
        
