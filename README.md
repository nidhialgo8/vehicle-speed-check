# Vehicle Speed Detection

![output.gif](output.gif)

Technologies used :
- Python
- opencv
- dlib
<br>

Tasks breakdown
1. Vehicle Detection
    - We are using Haarcascade classifier to identify vehicles.
2. Vehicle Tracking - ( assigning IDs to vehicles )
    - We have used corelation tracker from dlib library.
3. Speed Calculation
    - We are calculating the distance moved by the tracked vehicle 
		  in a second, in terms of pixels, so we need pixel per meter
		  to calculate the distance travelled in meters.
	- With distance travelled per second in meters, we will get the 
		  speed of the vehicle.

#### How to run project? 

Follow steps:

1. Clone repo :
`git clone https://github.com/kraten/vehicle-speed-check`

2. cd (change directory) into vehicle-speed-check
`cd vehicle-speed-check`

3. Create virtual environment
`python -m venv venv`

4. Activate virtual environment
`./venv/bin/activate`

5. Install requirements
`pip install  -r requirements.txt`

6. run speed_check.py script
`python speed_check.py`



#### Note: 


The estimation of these values has been done manually for the current road to calculate pixels per metre(ppm). Therefore, the value will vary from road to road and have to be adjusted to be used on any other video. 

For estimation of ppm, we need to know the actual width in metres of the road(you can use google to find the approximate width of the road in your country). Also, they have taken the video frame and calculated the width of the road in pixels digitally. Now, they have the width of the road in metres from the real world and in pixels from our video frame. To map the distances between these two worlds, we have calculated pixels per metre by dividing distance of road in pixels to metres.

d_pixels gives the pixel distance travelled by the vehicle in one frame of our video processing. To estimate speed in any standard unit first, we need to convert d_pixels to d_metres.

Now, we can calculate the speed(speed = d_meters * fps * 3.6). d_meters is the distance travelled in one frame. We have already calculated the average fps during video processing. So, to get the speed in m/s, just (d_metres * fps) will do. We have multiplied that estimated speed with 3.6 to convert it into km/hr.

