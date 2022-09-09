### 1. ERR_HTTP_HEADERS_SENT: Cannot set headers after they are sent to the client

Cannot set headers after they are sent to the client Here You Need To use **return** statement to solve this error.  

Error Is occurs Because Of Your **res.status(400)** . json is executing and then your function is not going to stop.  
So that Just _add return statement_ in your request handler function Just like This: 

#### return res.status(400).json

---

### 2. ENOENT: no such file or directory

파일 경로가 잘못됐을때 나는 에러다. 
multer를 통해 이미지 올릴 때 났던 에러인데, 하도 안올려져서 결국엔 
```javascript
destination: (req, file, cb) => {
    fs.mkdir('./uploads/',(err)=>{
      cb(null, './uploads/');
   })},
```

fs.mkdir 을 이용해 폴더를 새로 생성했다.  
너무 말을 안들으면 이렇게 해봐도 좋을듯!
   
