# movie-web
nomadcoder - ReactJS로 영화 웹사이트 만들기

React-router-dom v6로 업데이트 됨에 따라 
1. <Switch /> 대신 <Route /> 사용
2. component 속성 대신 element 속성 사용 (element는 JSX 형태로 태그와 함께 사용 ex. <Route path="/" element={<Home />} /> )
3. exact 사용X. exact가 기본값으로 exact의 사용이 필요하지 않다. exact 없이 url 형식을 구성하기 위해서는 *을 사용하도록 권고함
```
<Route path="member/*" element={<Member />} />
```
4. Redirect 사라지고 Routes 안에는 Route만 넣을 것을 권고. element의 컴포넌트 태그에 replace 속성과 to="url" 속성을 줘서 redirect를 설정한다.
```
<Route path="/" element={<Navigate replate to="/login/" />} />
```
5. 중첩라우팅 사용 가능.
```
//v5
<Switch>
  <Route path="/member" />
  <Route path="/member/:memberId" />
</Switch>

//v6
<Routes>
  <Route path="/member">
    <Route path=":memberId" /> // /member/:memberId
  </Route>
</Routes>
```

6. 레이아웃 설정이 간단해짐. 중첩 라우팅이 구성되면 Outlet을 통해서 상위 컴포넌트를 레이아웃화 할 수 있게 됨
```
<Routes>
  <Route path="/member" element={<Member />}>
  	<Route path=":memberId" element={<MemberInfo />} />
  </Route>
</Routes>


{/* Member */}
<div>
  <header>Member</header>
  <Outlet />  {/* MemberInfo의 component가 Outlet의 위치에 위치하게 된다. */}
</div>
```

https://reactrouter.com/docs/en/v6/upgrading/v5#upgrading-from-v5
