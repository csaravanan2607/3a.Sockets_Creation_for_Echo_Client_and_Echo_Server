# CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS
## AIM :
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.
## ALGORITHM :
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.
## PROGRAM :
client 
```
import socket
def start_server(host='127.0.0.1', port=65432):
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind((host, port))
    server_socket.listen(1)
    print(f"Server listening on {host}:{port}")

    while True:
        conn, addr = server_socket.accept()
        print(f"Connected by {addr}")

        try:
            while True:
                data = conn.recv(1024)
                if not data:
                    break  

                print(f"Received: {data.decode()}")

                
                conn.sendall(data)
        finally:
            conn.close()
if __name__ == "__main__":
    start_server()
```
server
```
import socket

def start_client(host='127.0.0.1', port=65432):
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect((host, port))

    try:
        message = "Hello, Server!"
        print(f"Sending: {message}")
        client_socket.sendall(message.encode())
        data = client_socket.recv(1024)
        print(f"Received: {data.decode()}")
    finally:
        client_socket.close()

if __name__ == "__main__":
    start_client()
```
## OUPUT :
![Screenshot 2024-10-04 205520](https://github.com/user-attachments/assets/0cae1718-d354-4a51-aff1-1a6a123f9cf7)

## RESULT :
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
