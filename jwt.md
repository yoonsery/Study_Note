## Sessions, Cookies, Token

### Cookies

서버는 쿠키를 이용해서 브라우저에 데이터를 넣을 수 있다 - 해당 유저를 기억하기 위해서

사이트에 방문하면 브라우저는 서버에 요청을 보낸다  
-> 서버는 이에 응답하고 response에는 데이터와 찾던 페이지 정보가 있다, 이 응답에는 브라우저에 저장하고자하는 쿠키가 있을 수도 있다  
유저가 브라우저에 쿠키를 저장한 후, 해당 웹사이트에 방문할 때마다 브라우저는 해당 쿠키도 요청과 함께 보내게 된다

쿠키는 도메인에 따라 제한된다 - 유튜브가 준 쿠키는 유튜브에만 보내지게 된다  
쿠키는 유효기간이 있다 - 서버가 정한 기간에 따라 정해진다  
쿠키는 인증뿐만 아니라 여러가지 정보를 저장할 수 있다

- 예: 웹페이지의 언어설정을 변경하면 서버는 변경된 언어를 쿠키에 저장해서 준다 - 다음에 해당 웹사이트 방문시 쿠키에 설정된 언어로 페이지를 제공

### Token

서버가 기억하는 랜덤하게 생긴 텍스트로 ID카드처럼 서버에게 보여줘야 한다

### Sessions

Stateless는 서버로 가는 모든 요청이 이전 리퀘스트와 독립적으로 다뤄진다는 뜻

유저가 갖고 있는 것은 session ID 이고, 쿠키는 session ID를 전달하기 위한 매개체일 뿐이다  
session을 이용해 iOS, Android 앱을 만들 수 있지만, 쿠키는 사용할 수 없다(브라우저에만 있음)  
그래서 네이티브앱의 경우에는 token을 이용한다  
서버는 session DB에서 해당 token과 일치하는 유저를 찾는다 (요청이 있을 때마다 DB를 찾고 유저를 확인한다)  
즉, 유저가 늘어남에 따라 DB 리소스가 더 필요하다

👍

- 서버는 로그인 된 유저의 모든 정보를 저장하고 이를 이용하면 새로운 기능들을 추가할 수 있다
- 특정 유저를 쫓고 싶으면 sessions를 삭제하면 된다
- 로그인 된 모든 디바이스를 보여주고 특정 디바이스에서 강제 로그아웃을 할 수 있다 (예\_ 인스타그램)
- 계정 공유 숫자를 제한 할 수 있다 (예\_ 넷플릭스)
- 왜냐면! 서버가 누가 로그인했는지 저장했고, session DB가 있기 때문에 가능하다

💩

- DB를 사고 유지해야한다
- 유저가 늘어날수록 DB도 커져야 한다 (주로 redis를 사용)

### JWT

정보를 갖고 있는 토큰, DB없이 검증할 수 있다

JWT는 token 형식인데 이걸로 유저 인증을 처리하면, session DB를 가질 필요가 없고,  
서버는 유저를 인증하기위해 많은 일을 하지 않아도 된다

쿠키는 공간제약이 있지만 JWT는 제약이 없어서 아주 많이 길어도 된다  
JWT는 토큰을 사인하고 이를 통해 유효한지 검증한다  
JWT는 암호화되어있지 않아서 누구나 열어서 해당 컨텐츠를 볼 수 있다  
JWT는 생성된 토큰을 추적하지 않는다, 서버가 아는 것은 토큰이 유효한가의 여부

👍

- DB를 따로 살 필요가 없다
- QR 체크인 기능 사용할 수 있다

💩

- sessions에 있는 인스타나 넷플릭스의 강제 로그아웃 기능이나 계정 당 유저 수 제한 기능을 사용할 수 없다  
  토큰이 만료되기 전까지는 유효하므로