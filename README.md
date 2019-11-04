# SLAM-Sim
Custom API designed to simplify usage of V-Rep to develop and evaluate SLAM algorithms

First of all, install the latest version of V-Rep available on Coppelia Robotics official web-site (http://www.coppeliarobotics.com/).

Next, clone this repository by clicking "Clone or download" button or using git client of your choice.

Make sure, you have Python 3 installed on your computer. If not, install it from https://www.python.org/downloads/. If you use Ubuntu or Debian Linux, you can install it from terminal using `sudo apt install python3` and `sudo apt install python3-dev`.

## Windows
You need to have Python 3 and Pip installed on your computer. If you don't have it, folow one of the many instructions of how to install this software from the Internet (for example this one https://www.liquidweb.com/kb/install-pip-windows/ and https://www.howtogeek.com/197947/how-to-install-python-on-windows/).

Next, use the folowing steps:

1. Open Command line (push Win+R and type "cmd");
2. Navigate to SLAM-Sim folder (you can use `cd` command. For more details folow the link https://ss64.com/nt/cd.html);
3. If you don't have Virtualenv on your computer, you can easily install it using `pip install virtualenv`;
4. Type `venv\Scripts\activate`. If you made everything right, you will see `(venv)` in the begining of current line;
5. Type `python server.py`. You can use arguments `$ python3 server.py -p=19998 -i=127.0.0.1` to change port or ip address of V-Rep Remote API Server.

After this you will receive a message from server ending with: `* Running on http://127.0.0.1:5000/`.

## Linux (Debian/Ubuntu)
1. Open Terminal;
2. Navigate to SLAM-Sim folder;
3. If you don't have Virtualenv on your computer, you can easily install it using `pip install virtualenv`;
4. Type `source mypython/bin/activate`. If you made everything right, you will see `(venv)` in the begining of current line.
5. Type `python server.py`. You can use arguments `$ python3 server.py -p=19998 -i=127.0.0.1` to change port or ip address of V-Rep Remote API Server.

After this you will receive a message from server ending with: `* Running on http://127.0.0.1:5000/`.

## Resource components

Resource | Description
--------------------------|------------
`/start-v-rep-server?ip=<IP Address>&port=<Port>` | Connect to V-REP. Arguments: ip - ip address on which V-REP Remote API Server will be started. Port - on which V-REP Remote API Server will be started. Request method: POST. Example `http://127.0.0.1:5000/start-v-rep-server?ip=127.0.0.1&port=5000`.
`/start-simulation` | Start V-REP simulation. Request method: POST. Example: `http://127.0.0.1:5000/start-simulation`.
`/pause-simulation` | Pause V-REP simulation. Request method: POST.
`/stop-simulation` | Stop V-REP simulation. Request method: POST.
`/print-message?text=<Text>` | Print message to V-REP console. Request method: POST. Example: `http://127.0.0.1:5000/print-message?Some text message you want to be printed`.
`/load-scene?file-name=<FileName>` | Load existing scene. Method: POST. Don't forget to add `.ttt` extension to file name e.g. `http://127.0.0.1:5000/load-scene?scene=Simple.ttt`.
`/add-robot?model-name=<Model name>` | Add robot specified by model file name to the scene. Method: POST. Example: `http://127.0.0.1:5000/add-robot?model=KUKA YouBot.ttm`
`/forward?<Robot ID>&<Speed>` | Make UBot move forward with specified speed. Method: POST. Example: `http://127.0.0.1:5000/forward?robot-id=0&speed=0.5`.
`/ubotBackward/<Speed>` | Make UBot move backward with specified speed.
`/ubotStop` | Make UBot stop.
`/move/<distance>` | Move UBot on specified distance. E.g. `http://127.0.0.1:5000/move/-1.5`.
`/getPosition` | Returns current UBot global coordinates.
`/getAngle` | Returns current UBot angle about Z axis.
`/getLidarData` | Returns data from robot's LIDAR.
`/getRGB` | Returns image captured by built-in RGB camera.
`/getDepth` | Returns depth data measured using Kinect.
