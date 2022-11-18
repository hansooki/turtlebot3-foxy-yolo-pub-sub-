# turtlebot3-foxy-yolo-pub-sub-

노트북 캠: ros2 run usb_cam usb_cam_node_exe
 rasicam-pub_tb3_pose2d.py-img_compressed2raw.py-aruco_node.py-track_maker2.

   //Import the necessary libraries
   import rclpy # Python Client Library for ROS 2
   from rclpy.node import Node # Handles the creation of nodes
   from sensor_msgs.msg import Image # Image is the message type
   from cv_bridge import CvBridge # Package to convert between ROS and OpenCV Images
   import cv2 # OpenCV library

   class ImagePublisher(Node):
     """
     Create an ImagePublisher class, which is a subclass of the Node class.
     """
     def __init__(self):
       """
       Class constructor to set up the node
       """
       //Initiate the Node class's constructor and give it a name
       super().__init__('image_publisher')

       //Create the publisher. This publisher will publish an Image
       # to the video_frames topic. The queue size is 10 messages.
       self.publisher_ = self.create_publisher(Image, 'video_frames', 10)

       //We will publish a message every 0.1 seconds
       timer_period = 0.1  # seconds

       //Create the timer
       self.timer = self.create_timer(timer_period, self.timer_callback)

       //Create a VideoCapture object
       //The argument '0' gets the default webcam.
       self.cap = cv2.VideoCapture(0)

       //Used to convert between ROS and OpenCV images
       self.br = CvBridge()

     def timer_callback(self):
       """
       Callback function.
       This function gets called every 0.1 seconds.
       """
       //Capture frame-by-frame
       //This method returns True/False as well
       //as the video frame.
       ret, frame = self.cap.read()

       if ret == True:
         //Publish the image.
         //The 'cv2_to_imgmsg' method converts an OpenCV
         //image to a ROS 2 image message
         self.publisher_.publish(self.br.cv2_to_imgmsg(frame))

       //Display the message on the console
       self.get_logger().info('Publishing video frame')

   def main(args=None):

     //Initialize the rclpy library
     rclpy.init(args=args)

     //Create the node
     image_publisher = ImagePublisher()

     //Spin the node so the callback function is called.
     rclpy.spin(image_publisher)

     //Destroy the node explicitly
     //(optional - otherwise it will be done automatically
     //when the garbage collector destroys the node object)
     image_publisher.destroy_node()

     //Shutdown the ROS client library for Python
     rclpy.shutdown()

   if __name__ == '__main__':
     main()

11/7 cv_bridge 이용한 ros2 pub,sub 작성 
    -cv_basics_
    
    
11/8 노트북캠에 완성한 pub, sub에 yolo를 추가하여 구동 성공
    -robot_ws/src/cv_basics/pub,sub


11/9 인식한 객체를 둘러쌓은 박스의 크기(1m기준)를 기준으로 크기(픽셀)에 비례하여 거리를 측정할려하였으나 박스인식이 유동적이여서 처음 객체를 인식했을 때 정중앙의 좌표를 구해 그 방향으로 터틀봇3의 각도를 돌려놓고 라이다로 거리 측정 후 특정 위치까지 전진 후 매니퓰레이터 작동해야겠다 구상


11/10 터틀봇3와 ros2 sub 구동 성공
    -robot_ws/src/cv_basics/pub,sub 수정
    
    11~18일 실패
    
