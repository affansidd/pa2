# Programming Assignment 2: Bufferbloat

All files required to run this program are included in the zipped submission. The only import added to bufferbloat.py was helper.py in order to calculate average and standard deviation. 

To run the code, inside the mininet VM, after uncompressing the submission files into a directory, navigate to the directory and simply run the shell command ```sudo ./run.sh```

Upon completion, the plots will be located in the bb-q20 and bb-q100 directories. 

Questions: 

1. Why do you see a difference in webpage fetch times with small and large router buffers?

Statistics: 

For one of the queue-size 20 runs:
- Average: 0.502270833333 
- Standard Deviation: 0.150690734561 

For one of the queue-size 100 runs:
- Average: 1.11775
- Standard Deviation: 0.580212383289

We see a difference in times due to the size of the buffer. The TCP congestion control algorithm keeps increasing the congestion window until a packet is dropped. A packet will be dropped when the buffer is filled up which takes a longer amount of time with a large buffer. Thus, TCP keeps sending more and more packets which are placed at the end of the queue and must wait a longer amount of time before being sent to the next hop resulting in a longer average fetch time. With a smaller buffer size, TCP packets will be dropped more often and regulates the size of the congestion window, allowing for better TCP congestion contol. 

2. Bufferbloat can occur in other places such as your network interface card (NIC). Check the output of ifconfig eth0 on your VirtualBox VM. What is the (maximum) transmit queue length on the network interface reported by ifconfig? For this queue size and a draining rate of 100 Mbps, what is the maximum time a packet might wait in the queue before it leaves the NIC?

txqueuelen:1000

The maximum transmission unit (MTU) is 1500 bytes. 

(1000 packets * 1500 bytes * 8 bits)/(100Mbps) = 12 000 000 / 100 * 10^6 = 0.12 seconds


3. How does the RTT reported by ping vary with the queue size? Write a symbolic equation to describe the relation between the two (ignore computation overheads in ping that might affect the final result).

When analyzing the plots generated, we can see that RTT is proportional to the queue size. As the queue size grows, RTT grows as well. Therefore the following symbolic equation demonstrates the relation between RTT and Queue size.

RTT = k * queue_size, where k is a constant of proportionality. From visual observation, it appears that k ~= 2.5-3.

4. Identify and describe two ways to mitigate the bufferbloat problem.


