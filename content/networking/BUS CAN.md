## Controller Area Network (CAN) Bus

### **Definition:**

The Controller Area Network (CAN) bus is a robust and widely-used network protocol in the field of automotive and industrial applications. It was originally developed by Robert Bosch GmbH in the 1980s and has since become a de facto standard for in-vehicle networking and industrial automation.

### **Key Characteristics:**

- **Two-Wire Bus:** CAN is a two-wire bus system, consisting of a twisted pair of wires: CAN High (CAN-H) and CAN Low (CAN-L). This differential signaling allows for noise immunity, making it suitable for noisy environments.
    
- **Broadcast Communication:** CAN is a broadcast-based communication protocol. Messages, also known as frames, are broadcasted to the entire network. Each device on the bus decides whether to accept or ignore a message based on its unique identifier.
    
- **Message Prioritization:** Messages on the CAN bus are prioritized using identifiers. Lower identifier values indicate higher priority. This allows critical messages, like those related to safety, to take precedence.
    
- **Deterministic:** CAN offers deterministic communication, meaning that message transmission times are predictable and consistent. This is crucial for real-time applications.
    
- **Error Detection and Handling:** CAN provides built-in error detection and handling mechanisms. Devices can detect errors like bit errors, frame errors, and more. In case of errors, devices can request retransmission.
    
- **Multi-Master:** CAN supports a multi-master architecture, allowing any device on the bus to initiate communication. Collision avoidance mechanisms are in place to ensure smooth bus operation.
    
- **Data Length:** CAN supports both standard and extended frames. Standard frames have 11-bit identifiers, while extended frames use 29-bit identifiers. This allows for flexibility in data length and addressing.
    
- **Bit Rate:** CAN bus systems can operate at various bit rates, from a few kilobits per second (Kbps) to several megabits per second (Mbps), depending on the specific application requirements.
    

### **Transmission of Data:**

CAN data transmission involves the following steps:

1. **Message Creation:** A device, known as a node, creates a message and assigns it a unique identifier.
    
2. **Message Arbitration:** The node checks the bus for ongoing transmissions. If the bus is idle, the node starts transmitting immediately. If the bus is busy, the node waits for an appropriate time to start transmission based on priority.
    
3. **Message Broadcasting:** The node broadcasts the message on the bus. Other nodes on the bus receive the message and determine if they should act upon it based on the identifier.
    
4. **Error Detection:** All nodes monitor the bus for errors during transmission. Common errors include bit errors and frame errors.
    
5. **Message Acknowledgment:** If a receiving node successfully receives a message without errors, it sends an acknowledgment (ACK) bit. If no ACK is received, the sender may retry transmission.
    
6. **Message Reception:** The receiving node processes the message based on its identifier. If the message is relevant to the node, it takes appropriate actions.
    
7. **Error Handling:** If errors are detected, devices can request retransmission, ensuring data integrity.
    

### Limit
1. The number of nodes is limited to 50
2. The length of wire, go to only 200m

The Controller Area Network (CAN) bus is highly reliable, efficient, and well-suited for real-time applications in automotive, industrial automation, and other fields where robust and deterministic communication is essential.