# Server
 
Сервер запускается из кода Program.cs. В Main вызов Server.Start(макс. кол-во игроков, порт).<br/>
Для оптимизации работы Unity с сервером надо синхронизировать вызовы FixedUpdate и TPS сервера. TPS записан в константах, а Time Unity должен быть 1/TPS.<br/>
### Вид пакетов:<br/>
 Посылаемые на сервер:<br/>
  id пакета  &emsp;           метод приёма     _содержание_<br/>
  1 welcomeReceived  &emsp;   WelcomeReceived  _id клиента, username_<br/>
  2 playerGrid     &emsp;     PlayerGrid       _длинна массива(2 двумерных массива), массив int(вообще их 2, но записаны подряд)_<br/>
  3 cursorGrid    &emsp;      CursorGrid       _длинна массива(двумернq массив), массив int_<br/>
 Посылаемые сервером:<br/>
  id пакета        &emsp;     метод отправки    _содержание_<br/>
  1 welcome       &emsp;      Welcome  (tcp)    _строка, id клиента_<br/>
  2 spawnPlayer   &emsp;      SpawnPlayer(tcp)  _id клиента, username, vector3 pos, quaternion rot_<br/>
  3 gridBuilding   &emsp;     BuildingGrid(tcp) _id клиента, длинна массива, массив int_<br/>
  4 gridStage     &emsp;      StageGrid(udp)    _id клиента, длинна массива, массив int_<br/>
  5 gridCursor   &emsp;       CursorGrid(udp)   _id клиента, длинна массива, массив int_<br/>
