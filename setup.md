

# Setup Guide

## Prerequisites
- Ensure you have a keyboard, mouse, and monitor connected to the Raspberry Pi (if available).

## Raspberry Pi Setup

1. **Turn on your phone's hotspot**  
   - Connect the Raspberry Pi to your phone's hotspot network.

2. **Open Terminal on Raspberry Pi**

3. **Navigate to the Project Directory**
   ```bash
   cd Desktop/SteerClear/mycar
   ```

4. **Start the Drive Command**
   ```bash
   python3 manage.py drive
   ```

a command to debug pins
```bash
donkey calibrate --pwm-pin=PCA9685.1:40.14 (or type 1:40.15)
```

5. **Expose the Raspberry Pi using Ngrok**

   - Run:
     ```bash
     ngrok tcp 22
     ```
   - Note the generated IP address; this will be used to connect remotely.
   - Ensure you've added your Ngrok authtoken (code in Slack #cmd-dump)
     ```bash
     ngrok config add-authtoken <your_authtoken>
     ```

6. **Connect via SSH**  
   - Use the IP from the previous step to SSH into the Raspberry Pi (url given from ngrok):
     ```bash
     ssh raspberrypi@2.tcp.ngrok.io -p <ngrok_port>
     ```

7. **Open a Local Tunnel**

   - On the Raspberry Pi terminal, run:
     ```bash
     lt --port 8887
     ```
   - This command will expose a network address. Use this address with `http` on your computer.

8. **Accessing the Tunnel**

   - When prompted for a password, enter the following command on the Raspberry Pi:
     ```bash
     curl https://loca.lt/mytunnelpassword
     ```
   - Copy the password displayed on the Raspberry Pi and enter it on your computer.
