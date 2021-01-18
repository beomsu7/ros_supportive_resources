## ㄱㄱ


 이건 쥬피터 노트북이라고해서 간단한 파이썬 형태의 코드를 바로 실행해 볼수 있는 환경이에요.
 
 코드가 있는줄에 커서를 두고 'ctrl + Enter' or 'shift + Enter' 을 누르면 실행이 됩니다.
 다만 저희가 파이썬 코딩을 하는건 아니니까 ros 에서 사용된 명령어같은걸 아래와 같은 명령줄에 넣어서 조금 구분을 해보았어요. 그러니까 밑에 print 문 말고는 다른 코딩 라인을 실행시켜봤자 에러밖에 안나올지도
 
 그래고 표윤석 박사님의 동영상을 기준으로 작성되었습니다.


```python
print '아무튼 ROS 강의 ch1 ~ ch 6 까지에 대한 간단 리뷰 및 복습 같은겁니다'#shift + Enter
```

    아무튼 ROS 강의 ch1 ~ ch 6 까지에 대한 간단 리뷰 및 복습 같은겁니다



```python
ctrl + alt + t #커맨더, 터미널 실행
ctrl + shift + c #터미널에서의 복사
ctrl + shift + v #터미널에 붙여넣기
clear #터미널 정리
```


---------------------------------------
---------------------------------------
ch3. ROS 개발환경 구축
=============

ch1, 2 는 그냥 넘어가요. 이론적인거니까요

 리눅스 환경이 익숙하지 않아 많은 명령어들이 무슨말인지 모르고 그냥 하라는대로 한게 많을꺼에요. 그래서 간단하게 하나씩 설명만 덧붙일께요.
 뭐 외우거나 그럴필요 없는데 실행시키고 할때 대충 의미라도 알아서 나쁠건 없으니까요.


```python
# 1:00 - ROS 1줄 설치 방법
wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh
    && chmod 755 ./install_ros_kinetic.sh && bash ./install_ros_kinetic.sh

```


      File "<ipython-input-9-6d279dc76cc4>", line 2
        wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh
                 ^
    SyntaxError: invalid syntax



wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh
>로보티즈의 깃허브(코드 저장소)에 저장된 파일을 복사해오기


&&
>command 에서 명령어를 실행시킬때 한번에 이어서 실행되게


chmod 755 ./install_ros_kinetic.sh
>wget .. 으로 다운받은 배시파일(.sh)을 실행시키기 위한 권한 부여하기
분명 내컴퓨턴데 왜 내가 권한을 부여해야하는거지 싶지만 컴퓨터란 그렇습니다
자세히 따지면 755 라는 숫자가 리드 라이트 실행 등등 뭐 많은데 이건 궁금하면 찾아보길
그냥 뭐 실행 권한이 없다 그런말 나오면 'chmod 777 실행시킬파일이름' 이런식으로 하면 깔끔


bash ./install_ros_kinetic.sh
>wget 으로 다운 받았고, chmod로 실행시킬수있는 권한을 얻었으니 이제 배시파일(.sh)을 실행한다.


https://github.com/ROBOTIS-GIT/robotis_tools/blob/master/install_ros_kinetic.sh
해당 주소로 들어가보면 위에서 실행시킨 install_ros_kinetic.sh 에 무슨 내용이 담겨있는지 볼수 있습니다.




```python
# 4:13 - ros 환경 설정
gedit ~/.bashrc
alias eb='gedit ~/.bashrc'
source ~/.bashrc
sudo apt-get install
cd ~/catkin_ws
```

~/
>저희가 윈도우를 쓸때는 바탕화면에서 대부분의 작업을 하였는데
우분투는 user 위에 home 이 있고, home 위에 desktop(바탕화면) 이 있어요
해당 표시는 home 을 가리켜요


'ctrl + alt + t' 를 눌러 명령창을 실행시키면
username:~$
로 나오는데 현재 위치는 home 이라는 거죠

gedit
>텍스트 편집기를 실행시키는 명령어에요 혹시 gedit 가 없다고 표시되면
'sudo apt-get install gedit' 로 설치할수 있어요
gedit 말고도 vim 이라던가 nano 등의 텍스트 편집기 들도 있어요
메모장 같은거죠


sudo ~~
>명령어를 실행시키다보면 앞쪽에 sudo 라는게 많이 보여요
윈도우로 치면 관리자 권한으로 실행하기랑 비슷한거에요
그냥 바로 접근하는것을 막아놓은, 내부의 수치가 바뀌면 좀 크리티컬 할수있는, 잠겨있는 것들에대한 접근을 위해서 추가적으로 붙이는 명령어에요


.bashrc
>컨 알 티 를 눌러 커맨트 창을 실행신키게 될때, 자동으로 실행되는 배시파일 이에요
쉽게 표현하면 기본 설정들을 적어놓는 파일인셈이죠

gedit ~/.bashrc
>위의 내용을 정리하면 home 폴더에 있는 기본설정들이 적혀있는 파일인 .bashrc 를 편집하기 위해 메모장을 실행시키는 명령어에요
만약 본인의 컴퓨터에서의 실행하는게 아니라 현재 이 rosds 환경에서 해보려고 하면
여긴 gedit 이나 nano가 설치되어 있지 않고 설치가 되지 않아요 그래서
vim ~/.bashrc 를 쳐야하는데 vim 이 또 안익숙할거라서 치지 마요 좀 이상해
그리고 커맨드 실행시키면 이미 home 이기에, 현재 home 에서는
'gedit .bashrc' 라고 쳐도 똑같이 실행될거에요


ctrl + h
>파일을 실행시키면 Home 폴더가 나와요 여기서 'ctrl+h' 를 누르면 숨겨진 파일들이 표시됩니다. 그럼 '.bashrc'를 볼수 있어요. 이걸 더블 클릭하면 편집 가능하고요.


alias eb='gedit ~/.bashrc'
>.bashrc는 기본 설정을 모아 놓는 파일이라고 했는데요. 여기에 gedit 으로 들어와서
'alias eb='gedit ~/bashrc' 를 입력해놓으면 단축키 설정이 가능해요
이젠 커맨드 창에서 eb 라고만 입력해도 .bashrc 편집기나 나와요

cd
>폴더 이동

ls
>현재 폴더의 내용물 확인

source
>실행 이라고 생각하면 편해요

#export
>변수에 대한 선언 정도로 하죠


```python
# 5:45 - ROS 동작 테스트
roscore
rosrun turtlesim turtlesim_node
rosrun turtlesim turtle_teleop_key
rosrun rqt_graph rqt_graph
```

이번 명령 4줄은 지금 이 rosds 환경에서 실행가능합니다.
좌측 아래의 >_ 모양을 누르거나 확장된 창에서 + 를 누르면 터미널들이 실행되고요
터미널을 여러개 띄워도 되고 터미널 상단의 + 를 눌러 창을 확장해도 됩니다

roscore
>일단 ros1 에서 암튼 표박사님이 설명 했겠죠

rosrun turtlesim turtlesim_node
>터틀심 노드 실행
다만 이놈은 하단의 컴퓨터 모양 'graphic tools' 눌러야 볼수있음
본인 컴퓨터의 리눅스 환경에서 실행하면 바로 창이 뜰거임

rosrun turtlesim turtle_teleop_key
>터틀심을 키보드로 조종하는 노드 실행
이제 키보드 방향키 누르면 거북이 움직임
다만 노드 자체가 방향키 누르면 일정 시간인가 거리를 움직이게 프로그래밍 되어있어 맘대로 움직이게 하긴 어려울꺼임

rosrun rqt_graph rqt_graph
>노드, 토픽의 현재 상황을 볼수있는 프로그램 실행
이놈도 하단의 컴퓨터 모양 'graphic tools' 눌러야 볼수있음
본인 컴퓨터의 리눅스 환경에서 실행하면 바로 창이 뜰거임

ctrl + c
>터미널 창에서 복사는 컨 쉬 c 이고
걍 컨 c 는 실행 프로그램 종료 입니다
컨 z 는 중단이고
왠만하면 컨 c 로 끝내는게 좋음


```python
# 6:01 - 이상한 검은 창 나뉘는 터미널
sudo apt-get install terminator
```

sudo apt-get install terminator
>terminator 이라는 프로그램을 설치합니다
해당 프로그램이 설치되면 기본 터미널이 터미네이터로 바뀌고
창 분할이 가능한 6:00 에 나오는 꽤 편리한 터미널이에요
사용법은
https://harryp.tistory.com/630
여기서 확인하시길



```python
# 11:47 - 통합 개발 환경
```

밑에 <> 'ide' 누르면 비쥬얼 스튜디오 같은거 나옴


---------------------------------------
---------------------------------------
ch4. ROS의 중요 컨셉
============
--------------------------
45:45 네임
뒤에서 다룬다고는 다는데 일단 저희는 터틀심 노드를 실행시켜서 거북이를 띄우고
텔레포트로 거북이를 움직여 봤어요 여기에 간단 예습 느낌으로 해보자고요       
<br/>
* 1번 터미널

   user:~$ roscore  
   <br/>
* 2번 터미널

   user:~$ rosrun turtlesim turtlesim_node  
   <br/>
* 3번 터미널

   user:~$ rosrun turtlesim turtlesim_node   
   <br/>
   
2번 터미널에서 터틀심을 실행시키면 거북이가 나와요.   
3번 터미널에서 터틀심을 한번 더 실행시키면 또 다른 거북이가 나왔으면 하지만   
기존의 거북이가 사라지고 새로운 거북이가 나옵니다. 이는 같은 이름의 노드를 실행시켰기에 이런 문제가 발생하고 네임을 변화시켜 주면 두마리의 거북이를 뽑을 수 도 있습니다.

--------------------------
* 1번 터미널

   user:~$ roscore  
   <br/>
* 2번 터미널

   user:~$ rosrun turtlesim turtlesim_node  
   <br/>
* 3번 터미널

   user:~$ rosrun turtlesim turtlesim_node /turtlesim:=/another_turtlesim
   <br/>
* 4번 터미널

   user:~$ rosrun turtlesim turtle_teleop_key
   <br/>
   
4번 터미널에 의한 텔레포트를 하면 두마리의 거북이가 다 움직일꺼에요
텔레포트 노드가 /cmd_vel(정확히는 /turtle1/cmd_vel)을 발행하고
터틀 노두 둘다 같은 토픽을 수신해서 같은 움직임을 보이죠
거북이를 각각 움직이게 하고 싶다면 터틀노드 실행시 수신받는 토픽의 이름도 바꾸면 가능하답니다


---------------------------------------
---------------------------------------
ch6. ROS 도구
============
--------------------------

자 여기서부터 rosds의 편리함이 나옵니다.
4:36 에 뎁스카메라라는 카메라를 이용하여 그 카메라가 찍어내는 결과물을 rviz 라는 툴을 이용하여 시각화 해줍니다.   
저런것을 실제로 한번 해보려고 하면 첫째로 해당 센서나 카메라가 있어야하고요   
둘째로 해당 센서나 카메라를 컴퓨터와 적절히 연결을 해서 통신이 되어야 해요   
당장 이런 실습을 위해서 20만원짜리 카메라를 살순 없죠
<br/>

------------------------------

* 가제보

<br/>
아래쪽에서 네번째에 있는 상자모양에 마우스를 가져다 대면 가제보 라는게 실행 가능해요

>'select a simulation'  
choose a robot : turtle bot   
choose a world : ware house   

<br/>
이러고 좀... 음 2~3분? 정도 기다리면 로봇이 물류창고에 있는 시뮬레이션 창이 뜹니다.   
실제 로봇을 가지고 테스트 해보고 하면 좋지만 그렇긴 힘들기에 그나마 차선의 방법입니다.   실물 로봇이 없어도 실물 로봇과 거의 동일하게 센서 값을 받아올수도 있고, 제어할수도 있습니다.
<br/>
* rviz
<br/>
터미널에 rviz 입력하고 엔터치면 rviz 가 실행됩니다...만 rosds의 경우 'graphical tools' 실행해서 창의 띄워줘야 보입니다.   
<br/>
일단 그냥 따라해보세요 모든걸 다 설명할순없는 현실이랄까

>창의 상단바를 더블클릭해서 화면을 좀 맞춰주고   
<br/>
(좌측 하단)Add -> by display type 에서 커서 내디라보면 rviz 아래에)RobotModel 더블클릭 -> 그럼 하얀 이상한게 보일꺼에요   
<br/>
좌측상단의 Fixed Frame 에 우측의 값이 map 로 되어있을건데 이것을 확장시켜서 base_footprint 로 바꿔주세요   
<br/>
이제야 정상적으로 로봇이 보이네요   
<br/>
Add-> By topic -> /camera/depth/image_raw/Camera 더블클릭   
<br/>
드디어 우리도 뎁스카메라가 어떻게 보이나 하는걸 직접 볼수있네요 시뮬레이션이지만   


근데 이걸 움직여봐야 재미있는데 그건 한번 알아서 해보는것도
간단히 움직일라면
새로운 터미널에   
>rosrun turtlesim turtle_teleop_key /turtle1/cmd_vel:=/cmd_vel

해주면 움직여 볼수있어요. 다만 대충 매칭시켜준거라 좌 우 방향키만 쓰는거 추천   
뭔가를 더해보고싶다하면 차라리 질문으로... ㅎ   
<br/>
해당 환경, rviz 에서 라이다 값도 볼수 있어요 위와 비슷한 방법으로   
음 더이상은 체력에 무리가 와서   
ㅈㅅ   
<br/>


```python

```
