## Azure Front Door 서비스 테스트 
### 시나리오 
### Blob 스토리지를 활용하여 정적웹 사이트 2개를 만들고, 1번 사이트는 index.htm 으로 홈을 구성하고, 2번 사이트는 index.html로 구성하였다, App Service를 활용하여 3번째 기본이미지를 통해 사이트를 만들었다. 
### RuleSet에 2개의 규칙을 추가한다. 
### rule1은 확장자가 html인경우 2번째 사이트로 보낸다. rule2는 모바일에서 접속시 3번째 사이트가 열리도록 한다. 

- 1번 사이트 주소(blob 정적웹) : https://strgacc10565kc.z12.web.core.windows.net/
- 2번 사이트 주소(blob 정적웹) : https://strgacc10565kc.z12.web.core.windows.net/
- 3번 사이트 주소(app service) : https://webappkctest.azurewebsites.net 
-  각각의 사이트 모양은 이러하다 
- 1번 사이트 
![image](https://user-images.githubusercontent.com/98098974/193055078-e8ca5788-cbbc-42e9-91e2-bd0f0d2d4c48.png)
- 2번 사이트 
![image](https://user-images.githubusercontent.com/98098974/193055183-4b6979a3-8a3a-4313-8b3b-b1f54949543c.png)
- 3번 사이트 
![image](https://user-images.githubusercontent.com/98098974/193055216-fa63bb3b-5969-44a7-92d9-f84cddd98416.png)

### Front Door 셋팅 
- Front door를 만들어 준다. 이름오류는 이미 만든상태에서 캡쳐 해서 그렇다.
![image](https://user-images.githubusercontent.com/98098974/193056334-9929dece-88ae-4cf1-8eb9-0b44aa86a93d.png)
- 생성하면 아래와 같은 화면을 볼수 있다. 
![image](https://user-images.githubusercontent.com/98098974/193056833-505fd891-98f2-4972-a9d2-ae3ed7c05d6d.png)
- 초기 생성할때 입력한 정보로 엔드포인트, 경로, 원본그룹이 하나씩 만들어 진다. 
- 엔드포인트로 접속해보면 1번사이트가 잘 열린다. 
- 이제 2번째 사이트, 3번째 사이트를 위한 원본그룹을 생성하면 된다.
- 원본그룹 탭으로 가서 추가를 누르면 아래와 같은 화면이 나온다. 이미 만들어진 상태지만, 원본추가 버튼을 누른다. 
 ![image](https://user-images.githubusercontent.com/98098974/193057904-1b238935-e44f-4c35-a169-09c53ecab167.png)
- 2번째 사이트는 스토리지 Blob 정적웹이므로 "스토리지(정적 웹사이트)" 를 선택하고 생성한 스토리지를 선택하면 된다. 
 ![image](https://user-images.githubusercontent.com/98098974/193058325-138dc8fd-471f-46fd-8e70-9d8eb561fd78.png)
- 동일한 작업으로 3번째 원본그룹도 생성하고 원본은 앱서비스를 선택해서 만들어 준다 
 ![image](https://user-images.githubusercontent.com/98098974/193058707-741fda27-b227-4a42-ac97-5caee4eca49f.png)
- 2번째 3번째 원본그룹에 경로를 연결할 필요는 없다. 아래 화면 처럼 
 ![image](https://user-images.githubusercontent.com/98098974/193059001-f3377572-e77a-4862-a8c6-e89a8596c585.png)
- 이제 규칙집합 탭으로 가서 규칙집합을 생성 해준다. 
![image](https://user-images.githubusercontent.com/98098974/193061913-0fe2f1bf-4026-448b-886e-3a3d8ed7775a.png)

- 확장자명이 html이면 2번째 원본그룹으로 보내고, 접속 디바이스가 모바일이면 3번째 그룹으로 보내도록 설정하고 저장한다. 
 ![image](https://user-images.githubusercontent.com/98098974/193059665-f954e6eb-bae5-4d69-a159-fbdf886dc5dc.png)
- 그 후 경로연결을 눌러 default-route 경로와 룰셋을 연결 해준다. 
 ![image](https://user-images.githubusercontent.com/98098974/193059911-50d444cc-444a-4b26-b3dc-2f40364c8e9d.png)
- 이제 접속 테스트를 해보자
### 접속 테스트 
##### 1. https://ep-test01-gthjcvg7g5hxhudz.z01.azurefd.net/ 을 입력 
![image](https://user-images.githubusercontent.com/98098974/193060516-5f560da9-415f-4799-9eae-1150895ff318.png)
##### 2. https://ep-test01-gthjcvg7g5hxhudz.z01.azurefd.net/index.html 을 입력
![image](https://user-images.githubusercontent.com/98098974/193060821-febb702a-7a30-40b4-b30f-3a74dfaff83d.png)
##### 3. 핸드폰에서 접속 https://ep-test01-gthjcvg7g5hxhudz.z01.azurefd.net/ 
![image](https://user-images.githubusercontent.com/98098974/193061364-15b478f0-c6a7-4219-95da-603cc1b77e6c.png)




