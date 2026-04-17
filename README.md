# hafta11
#mertcankati
import socket
import json
ip="10.17.31.237"
port=14146
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect((ip,port))


request = {
    "func": "carp",
    "a": 5,
    "b": 3
}

client.send(json.dumps(request).encode())

data = client.recv(1024)
response = json.loads(data.decode())

print("Sonuc:", response["result"])
client.close()
