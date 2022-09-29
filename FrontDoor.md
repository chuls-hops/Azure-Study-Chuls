## Azure Front Door 서비스 테스트 
### 시나리오 
### Blob 스토리지를 활용하여 정적웹 사이트 2개를 만들고, 1번 사이트는 index.htm 으로 홈을 구성하고, 2번 사이트는 index.html로 구성하였다, App Service를 활용하여 3번째 기본이미지를 통해 사이트를 만들었다. 
### RuleSet에 2개의 규칙을 추가한다. 
### rule1은 확장자가 html인경우 2번째 사이트로 보낸다. rule2는 모바일에서 접속시 3번째 사이트가 열리도록 한다. 

### 1번 사이트 주소(blob 정적웹) : https://strgacc10565kc.z12.web.core.windows.net/
### 2번 사이트 주소(blob 정적웹) : https://strgacc10565kc.z12.web.core.windows.net/
### 3번 사이트 주소(app service) : https://webappkctest.azurewebsites.net 
### 각각의 사이트 모양은 이러하다 
### 1번 사이트 
![image](https://user-images.githubusercontent.com/98098974/193055078-e8ca5788-cbbc-42e9-91e2-bd0f0d2d4c48.png)
### 2번 사이트 
![image](https://user-images.githubusercontent.com/98098974/193055183-4b6979a3-8a3a-4313-8b3b-b1f54949543c.png)
### 3번 사이트 
![image](https://user-images.githubusercontent.com/98098974/193055216-fa63bb3b-5969-44a7-92d9-f84cddd98416.png)

