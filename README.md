# turtlebot3-foxy-yolo-pub-sub-
11/6 slam/navi 작동

노트북 캠: ros2 run usb_cam usb_cam_node_exe
rasicam-pub_tb3_pose2d.py-img_compressed2raw.py-aruco_node.py-track_maker2.


11/7 cv_bridge 이용한 ros2 pub,sub 작성 
    
![Screenshot from 2022-11-18 11-38-49](https://user-images.githubusercontent.com/112480482/202604390-327d1f9c-015f-42d2-871f-b223c8b27095.png)
publising
![Screenshot from 2022-11-18 11-39-30](https://user-images.githubusercontent.com/112480482/202604399-17a192cd-c418-4142-a64e-fa17a9695889.png)
subsribe
![video](https://user-images.githubusercontent.com/112480482/202604423-f87d1d74-d445-42a3-a207-0e5c9bc8cff9.png)
video 출력
    
11/8 노트북캠에 완성한 pub, sub에 yolo를 추가하여 구동 성공



11/9 인식한 객체를 둘러쌓은 박스의 크기(1m기준)를 기준으로 크기(픽셀)에 비례하여 거리를 측정할려하였으나 박스인식이 유동적이여서 처음 객체를 인식했을 때 정중앙의 좌표를 구해 그 방향으로 터틀봇3의 각도를 돌려놓고 라이다로 거리 측정 후 특정 위치까지 전진 후 매니퓰레이터 작동해야겠다 구상


11/10 터틀봇3와 ros2 sub 구동 성공
    -robot_ws/src/cv_basics/pub,sub 수정
![Screenshot from 2022-11-18 11-57-00](https://user-images.githubusercontent.com/112480482/202607015-10e69a95-898f-4686-a4fd-a681f1a8aeb4.png)

    
