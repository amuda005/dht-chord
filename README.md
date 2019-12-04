# dht-chord
### A book finder system using Distributed Hash Table(DHT)
* There are 2 main components of Distributed Hash Table in the design: 1)
Supernode and 2) DHT Node. A circular key space ranging from
0 to 2^m(1<=m<=64) is used.
* A unique random id is assigned to each node joining the DHT by hashing the
node ip and port combination and divide the key space among the joining
nodes.
* **Hash Function**: We are using **MD5** hash to create the node id and key for the
book title. We are using a key space of 2^m and hence we take modulus of
resulted hash bytes with 2^m. This result could potentially cause collisions. As the
node id should be unique, therefore we are rehashing till we get the node id which
is not in the system.
* The request for setting and getting book genre is passed using the algorithm
defined in the [Chord: A Scalable peer-to-peer Lookup Service for Internet
Applications](https://pdos.csail.mit.edu/papers/chord:sigcomm01/chord_sigcomm.pdf)

![Architecture](/dhtchord.png)

#### To run the code, follow the steps:
1. Compile the code using makefile:
  * Command: make
  * Result - A jar file “dht-chord-0.0.1-SNAPSHOT-jar-with-dependencies.jar” will be created inside target directory.\
2. Configuration file: 
  * ensure to keep the superNodeIP and superNodePort to be same ip and port on which supernode is running
  * superNodeIP and superNodePort will be used by client and new node joining the DHT
3. Virtual Arguments:
  * configFile - Path of configuration file as described above
  * port - Port on which multithreaded Supernode server will run
