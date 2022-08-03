### 1. ERR_HTTP_HEADERS_SENT: Cannot set headers after they are sent to the client

Cannot set headers after they are sent to the client Here You Need To use **return** statement to solve this error.  

Error Is occurs Because Of Your **res.status(400)** . json is executing and then your function is not going to stop.  
So that Just _add return statement_ in your request handler function Just like This: 

#### return res.status(400).json

---

### 2. 
