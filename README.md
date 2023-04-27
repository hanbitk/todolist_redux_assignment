### [과제] 숙련주차 과제 답


<h2>1. 추가하기 버튼을 클릭해도 추가한 아이템이 화면에 표시되지 않음.</h2>

<p>AS-IS</p>
<img width="497" alt="image" src="https://user-images.githubusercontent.com/89821162/234738668-95ca91c8-60fe-4b94-b8e9-95b1e74fed28.png">

- 추가하기 버튼 클릭시 아이템이 화면에 표시되지 않은 이유는 dispatch 훅으로 Redux Store에 상태 변화를 일으키는 action을 전달 안 해서 발생.

<p>TO-BE</p>
<img width="497" alt="image" src="https://user-images.githubusercontent.com/89821162/234739038-e3285c26-f52c-482b-9011-f6c8e785f9ab.png">

- Redux useDispatch hook을 사용해서 Redux Store에서 함수를 가져와 사용 후, Redux Store에 상태 변화를 하도록 action 전달. 인자로 todo와 id를 받음. <br/><br/>

<h2>2. 추가하기 버튼 클릭 후 기존에 존재하던 아이템들이 사라짐.</h2>

<p>AS-IS</p>
<img width="368" alt="Screenshot 2023-04-27 at 10 55 34" src="https://user-images.githubusercontent.com/89821162/234740532-01d778b3-3722-4f55-b429-70a2b034e045.png">

- ADD_TODO 액션 핸들러에서는 전달받은 action.payload 값을 새로운 배열로 return하여 todos 배열에 todo를 추가하는게 아니라 기존에 존재하던 아이템들이 사라짐. 

<p>TO-BE</p>
<img width="389" alt="image" src="https://user-images.githubusercontent.com/89821162/234740721-af7607b3-4817-4c70-906b-5eb53464f1cc.png">

- ADD_TODO 액션 핸들러에 todos 배열을 복사해서 action.payload(todo) 객체를 추가해줘야 함. <br/><br/>


<h2>3. 삭제 기능이 동작하지 않음.</h2>

<p>AS-IS</p>
<img width="233" alt="image" src="https://user-images.githubusercontent.com/89821162/234741721-e1097753-6e60-46af-ae38-e0b9a85b1a47.png">
<img width="378" alt="image" src="https://user-images.githubusercontent.com/89821162/234741810-7b779be3-c665-4183-8770-fe03cb82cb60.png">

- DELETE_TODO라는 액션 핸들러가 없어서 삭제 기능이 동작하지 않음. 

<p>TO-BE</p>
<img width="538" alt="image" src="https://user-images.githubusercontent.com/89821162/234742058-48fdd0a0-cc94-4bea-9846-1fe626ac9342.png">

- switch case에 DELETE_TODO 액션 핸들러 추가. action payload로 받아온 id와 todos id와 같지 않은 데이터들을 새 배열로 return <br/><br/>

<h2>4. 상세 페이지에 진입 하였을 때 데이터가 업데이트 되지 않음.</h2>

<p>AS-IS</p>
<img width="414" alt="image" src="https://user-images.githubusercontent.com/89821162/234742809-fd960c9e-8d80-4ca3-a081-2848cb028c44.png">

- getTodoByID 액션 생성자 함수에서 payload로 id를 전달하지 않아서 상세 페이지 진입할 때 데이터 업데이트 되지 않음. 

<p>TO-BE</p>
<img width="241" alt="image" src="https://user-images.githubusercontent.com/89821162/234742921-bb880382-f993-4251-b7d0-9285eecc00db.png">

- 컴포넌트가 마운트될 때 useEffect 훅이 실행되어 getTodoByID 액션 생성자 함수가 dispatch되고, id에 해당하는 todo가 상태에 저장됨. <br/><br/>


<h2>5. 완료된 카드의 상세 페이지에 진입 하였을 때 올바른 데이터를 불러오지 못함. </h2>

<p>AS-IS</p>
<img width="439" alt="image" src="https://user-images.githubusercontent.com/89821162/234743346-8bd713c7-4625-466f-bdf9-422913fd32c2.png">

- todo의 id가 아닌 배열의 index로 되어 있어 올바른 데이터 불러오지 못함.

<p>TO-BE</p>
<img width="453" alt="image" src="https://user-images.githubusercontent.com/89821162/234743577-882c11cc-4128-4fed-9569-45ab5b53d381.png">

- todo.id로 경로 변경

<h2>6. 취소 버튼 클릭시 기능이 작동하지 않음. </h2>
<img width="284" alt="image" src="https://user-images.githubusercontent.com/89821162/234744069-7eee4a22-aa93-42f4-99d9-63fc5d04904c.png">
<img width="418" alt="image" src="https://user-images.githubusercontent.com/89821162/234743892-dad04e45-b25f-43b0-b677-5f771ed1c741.png">

- onToggleStatusTodo 인자로 id를 받아서 dispatch로 넘기고 있지만, onClick에서는 id를 넘겨주지 않아서 취소 버튼이 잘동하지 않음.

<p>TO-BE</p>
<img width="439" alt="image" src="https://user-images.githubusercontent.com/89821162/234744296-60816574-2e81-4642-bc36-78270dc7ce37.png">

- onToggleStatusTodo 함수에 인자로 id 전달

