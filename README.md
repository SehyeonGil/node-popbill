# node-popbill
팝빌 node.js SDK v1.54.1에서 MMS로 이미지 전송을 시도하는데, binary로는 전송이 불가능하고 로컬 파일 전송만 가능하여 binary 전송을 추가함.

lib/MessageService.js만 수정했음.

v1.54.1 MMS 전송 함수
```js
messageService.sendMMS(CorpNum, Sender, Receiver, ReceiverName, Subject, Contents, FilePaths, reserveDT, adsYN, requestNum, success, error)
```

위에서 Prameter에 BinaryFiles만 추가함
```js
messageService.sendMMS(CorpNum, Sender, Receiver, ReceiverName, Subject, Contents, FilePaths, BinaryFiles, reserveDT, adsYN, requestNum, success, error)
```

BinaryFiles는 배열을 값으로 받으며, 그 배열은 아래의 json을 값으로 갖는다.
```json
{
    fileName:"파일명",
    fileData:binary(buffer)
}
```

BinaryFiles가 존재하지 않을경우, 기존과 같이 FilePaths로 이미지 전송함.