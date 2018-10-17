# Scan-host-port
copy others code can't run   after enter host name
import socket
import subprocess
import sys
from datetime import datetime

subprocess.call('cls',shell=True)
remoteServer =input("Enter a remote host to SCAN:")
remoteServerIP=socket.gethostbyname(remoteServer)
print("-"*60)
print("please wait, scanning remote host",remoteServerIP)
print("-"*60)
t1=datetime.now()
try:
    for port in range(1,1025):
        sock=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
        result=sock.connect_ex((remoteServerIP, port))
        if result==0:
            print("port {0}:    Open".format(port))
        sock.close()
except KeyboardInterrupt:
    print("you press Ctrl+C")
    sys.exit()
except socket.gaierror:
    print("hostname could not be resolved.Exiting")
    sys.exit()
except socket.error:
    print("Could't connect to server")
    sys.exti()
t2=datetime.now()
total=t2-t1
print('Scanning Completed in',total)
