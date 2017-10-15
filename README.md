# data-exchange
A way to exchange data for money using payment channels


Let the data collection to be exchanged be: 

D= {d1,d2, di...,dN} where N === Number of elements required by the analyst; 0<i<N


For each record, the user defines a secret, defined as: 

S= {s1,s2, si...,sN} where N === Number of elements required by the analyst; 0<i<N

Let the price of each record be p (defined by the market), and the price of the total data collection be P=N*p. 

The following schemas based on the creation of a **payment channe**l and mixed with hash revealing procedures is proposed as an example of a simple but base case way to do it:


1. Analyst opens a payment channel on Ethereum, using  X= (n+1)*p ETH protected with hash-lock.
2. Analyst sets a timeout of T enough to get all the data
3. Client checks in the Smart Contract that the funds are locked.
4. Client starts sending records.
5. For each record requested, Analyst sends  a signature(contract_address, value)  to the Client via Whisper where value= i*X/N
6. Client can decide to stop in every moment, by submitting his own signature(contract_address, value)t to the channel that will verify signature using ecrecover
7. The last portion of the payment is received when the analyst receives the last data element, in order to ensure the payment after receiving all the data.

