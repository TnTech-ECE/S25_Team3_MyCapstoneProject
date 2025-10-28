## Running the Capture Program
1. Enter the desired folder: cd Downloads/unix_rid_capture (I think... double check file path)
2. Compile any helper programs that have been updated: g++ -o data_forwarder data_forwarder.cpp
3. Run one of the following lines to start scan:
* To run just the bluetooth capture: sudo ./rid_capture -w bluetooth-monitor -x
* To run the bluetooth capture with data forwarder: sudo ./rid_capture -w bluetooth-monitor -x | python3 forward_rid.py
* To run the wifi and bluetooth capture: sudo ./rid_capture -x wlan1 -w wlan0mon
* __To run the wifi and bluetooth capture with data forwarder: sudo ./rid_capture -x wlan1 -w wlan0mon | ./data_forwarder__

## Running the Server
cd projects/drone_server  
gcc -o drone_server server.c -lpthread -lsqlite3  
./drone_server

## More Useful Commands
* To disable ethernet prioritization: sudo ip route del default dev eth0
* To see wifi networks: nmcli dev wifi
* To show list of networks: ip link
* To show list of devices: iw dev
* To start network manager: sudo systemctl start NetworkManager
* To send information using socat (example): echo “D1,op123,DJI,Phantom,2025-09-15T12:12:00,36,3,-85.6,100,10,90,GPS” | socat - TCP:10.104.132.84:5000

## Other Notes
* Server Pi IP Address: 10.104.132.84 and 149.149.48.36
* Client Pi IP Address: 149.149.48.33 and 149.149.50.40
