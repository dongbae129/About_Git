# About_Git

<h1>목차</h1>
<ul>
  <li>1.기본 원리 </li>
  <li>2.사용될 명령어들 </li>
  <li>3.시나리오 실행 </li>
</ul>

<h2>git 원리(흐름)</h2>
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
