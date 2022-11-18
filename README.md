# turtlebot3-foxy-yolo-pub-sub-
11/6 slam/navi 작동

노트북 캠: ros2 run usb_cam usb_cam_node_exe
rasicam-pub_tb3_pose2d.py-img_compressed2raw.py-aruco_node.py-track_maker2.


11/7 cv_bridge 이용한 ros2 pub,sub 작성 
    
  ![publishing](https://user-images.githubusercontent.com/112480482/202604095-989429ab-2b45-4b3f-bee4-ec449c8dae09.png)

    
11/8 노트북캠에 완성한 pub, sub에 yolo를 추가하여 구동 성공
    -robot_ws/src/cv_basics/pub,sub


11/9 인식한 객체를 둘러쌓은 박스의 크기(1m기준)를 기준으로 크기(픽셀)에 비례하여 거리를 측정할려하였으나 박스인식이 유동적이여서 처음 객체를 인식했을 때 정중앙의 좌표를 구해 그 방향으로 터틀봇3의 각도를 돌려놓고 라이다로 거리 측정 후 특정 위치까지 전진 후 매니퓰레이터 작동해야겠다 구상


11/10 터틀봇3와 ros2 sub 구동 성공
    -robot_ws/src/cv_basics/pub,sub 수정
    
    11~18일 stereo camera 예제 실행 실패
    
