# **Basic UDP Client in Python**  

A simple **UDP client** using Python's `socket` module. The client sends a message (`"AAABBBCCC"`) to a server running on `127.0.0.1` (localhost) at port `80` and then waits for a response.  

---

### **How to Run the Code:**  
1. Ensure Python (`Python 3.x` recommended) is installed.  
2. Save the script as `udp_client.py`.  
3. Before running the script, ensure a **UDP server** is listening on `127.0.0.1:80` to receive and respond to messages.  
4. Run the script using:  
   ```bash
   python3 udp_client.py
   ```

---

### **Python Code:**
```python
import socket  # Import socket module for network communication

# Define the target server (localhost) and port
target_host = "127.0.0.1"  # Localhost (loopback address)
target_port = 80  # Port to send data (ensure a server is listening here)

# Create a socket object using:
# AF_INET -> IPv4
# SOCK_DGRAM -> UDP (User Datagram Protocol)
client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

# Send data to the target server
client.sendto(b"AAABBBCCC", (target_host, target_port))

# Receive response data (up to 4096 bytes) from the server
data, addr = client.recvfrom(4096)

# Close the socket after communication is done
client.close()

# Print the received response
print(data)
```

---

### **Explanation of Key Concepts:**  
1. **Sockets:** Used for network communication between devices.  
2. **UDP (User Datagram Protocol):** Unlike TCP, UDP is **connectionless** and **faster** but **unreliable** (data may be lost).  
3. **`sendto()` Method:** Directly sends data to the specified server without establishing a connection.  
4. **`recvfrom()` Method:** Receives response data along with the sender's address.  
5. **Localhost (`127.0.0.1`)** is used for testing on the same machine.  

**Important Note:**  
- This script **requires a UDP server** running on `127.0.0.1:80`.  
- If there's no server, the script will hang or throw an error.  
- Change `target_port` to match the listening UDP server's port (e.g., `9999`).  
