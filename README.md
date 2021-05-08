# Real-Time-Streaming-Video-Simulator
A simple program simulates streaming video server and client that communicate using the Real-Time Streaming
Protocol (RTSP) and send data using the Real-time Transfer Protocol (RTP).


## Description
1. Client, ClientLauncher

The ClientLauncher starts the Client and the user interface which you use to send RTSP
commands and which is used to display the video. The Client class performs actions
that are taken when the buttons are pressed.

2. ServerWorker, Server

These two modules implement the server which responds to the RTSP requests and streams back the video.
The RTSP interaction is already implemented and the ServerWorker calls methods from the RtpPacket class
to packetize the video data.

3. RtpPacket

This class is used to handle the RTP packets. It has separate methods for handling the received packets at the
client side and you do not need to modify them. The Client also de-packetizes (decodes) the data.

4. VideoStream

This class is used to read video data from the file on disk. You do not need to modify this class.

## Server

Server will receive RTSP packet which stores the request from client, then return the state of the
request or the video's frame to display in client side.

Start the server with the command:

```python
#python Server.py server_port
```

Where: server_port is the port that server listens to for incoming RTSP connections. It should be larger than 1024.

## Client

Client will send request to the server, include:
  * SETUP: create RTP socket to receive video's frame.
  * PLAY: receive frame, play the video.
  * PAUSE: pause the video.
  * TEARDOWN: stop the video and disable RTP connection.

You'll need to install a module that helps displaying UI for interaction:

```python
#pip install tkinter
```

Start the client with the command: 

```python
#python ClientLauncher.py server_host server_port RTP_port video_file
```

Where:
  * server_host: IP address of the server
  * server_port: RTSP port number of the server
  * RTP_port: port number where the RTP packets are received
  * video_file: name of the video file you want to request 


