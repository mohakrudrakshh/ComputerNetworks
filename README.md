# Internet-Radio-Multicasting-multimedia-over-IP
This project will work as mentioned below.First, Client will send a join request to the server to join the multicast group.After that Server will provide station list, site info to the client through TCP. Then whichever station it selects from the station list, it is connected to that station.All the stations are sending data, irrespective of client is connected or not. This functionality is incorporated to relate more with real life situation, e.g Tv/radio sends data even though there is no receiver connected.Whenever receiver connects to a particular station, it starts receiving live-streaming videos from that station. Receiver can pause, resume, change station or even terminate at any given time from GUI using thread.

# Internet Television Project

## Guru Nanak Dev University - Computer Network Course

**Group**
- Dr. Jagmohan Mago
- Rudraksh Gupta - 10722132919
- Yuvraj Sachdeva - 10722132933
- Gishika Gupta - 10722132920

## Project Files

### Server
- **server.c**
    ```bash
    gcc server.c
    ./a.out
    ```

### Stations
- **station1.c**
    ```bash
    gcc station1.c
    ./a.out 239.192.4.1
    ```
- **station2.c**
    ```bash
    gcc station2.c
    ./a.out 239.192.4.2
    ```

### Client
- **client.c**
    ```bash
    gcc `pkg-config --cflags gtk+-3.0` -o client client.c `pkg-config --libs gtk+-3.0`
    sudo ./client <IP-ADDRESS of the server>
    ```

### Receiver
- **receiver.c**  
  Compiled and executed by the client.

## Execution Steps
1. The client sends a join request to the server.
2. The server provides station and site information via TCP.
3. The client connects to the selected station.
4. Stations broadcast data continuously, mimicking real-life TV/radio broadcasts.
5. The client receives live-streaming videos from the selected station.
6. The media player used is `ffplay`, and videos are converted using `ffmpeg` to make them streamable:
    ```bash
    ffmpeg -i inputfile.mp4 -f mpegts streamable_output.mp4
    ```

### GUI Controls
- **Pause**: Temporarily stop receiving data from the sender.
- **Resume**: Resume receiving data from the same station.
- **Change Station**: Disconnect from the current station and connect to a new one.
- **Terminate**: Disconnect from the current station and exit the application.

### Multithreading
- A thread is used to run the GUI and socket programming simultaneously.

## Design Configurations
- **Client to Server**: TCP is used for one-to-one connection.
- **Sender to Receiver**: UDP is used for multicast live-streaming.
- **GUI**: Implemented using `gtk`.

## Station Information
- **Station 1**: F.R.I.E.N.D.S, Multicast Address: 239.192.4.1, Port: 5432
- **Station 2**: H.I.M.Y.M, Multicast Address: 239.192.4.2, Port: 5432

## Features
- Audio and video are received without data loss through UDP.
- Both stations send data on the same port but have different IP addresses.

### Buffer Calculation
- The buffer size is calculated based on the bit-rate and time for each station. Example buffer size: 64000.

## Screenshots
- Compilation of all files.
- Site and station information at the client side.
- Station selection GUI window.
- Station 1 (F.R.I.E.N.D.S) GUI.
- Station 2 (H.I.M.Y.M) GUI.

![Site Info](path/to/site_info_image.png)
![Station Info](path/to/station_info_image.png)
![Station 1](path/to/station1_image.png)
![Station 2](path/to/station2_image.png)

## Individual Contributions
- **Server, Sender Code**: Rudraksh Gupta, Yuvraj Sachdeva
- **Client, Receiver Code**: Rudraksh Gupta, Gishika Gupta
- **GUI Creation**: Dr. Jagmohan Mago
- **GUI & Socket Integration**: Rudraksh Gupta, Yuvraj Sachdeva
- **Debugging & Report Creation**: All members

