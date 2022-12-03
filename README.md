# Programming Assignment 2: Bufferbloat

All files required to run this program are included in the zipped submission. The only import added to bufferbloat.py was helper.py in order to calculate average and standard deviation. 

To run the code, inside the mininet VM, after uncompressing the submission files into a directory, navigate to the directory and simply run the shell command ```sudo ./run.sh```

Upon completion, the plots will be located in the bb-q20 and bb-q100 directories. 

Statistics: 

For one of the queue-size 20 runs:
- Average: 0.502270833333 
- Standard Deviation: 0.150690734561 

For one of the queue-size 100 runs:
- Average: 1.11775
- Standard Deviation: 0.580212383289

Questions: 

1. Why do you see a difference in webpage fetch times with small and large router buffers?



2.Bufferbloat can occur in other places such as your network interface card (NIC). Check the output of ifconfig eth0 on your VirtualBox VM. What is the (maximum) transmit queue length on the network interface reported by ifconfig? For this queue size and a draining rate of 100 Mbps, what is the maximum time a packet might wait in the queue before it leaves the NIC?



3. How does the RTT reported by ping vary with the queue size? Write a symbolic equation to describe the relation between the two (ignore computation overheads in ping that might affect the final result).



4. Identify and describe two ways to mitigate the bufferbloat problem.
