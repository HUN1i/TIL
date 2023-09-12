<h1>multer란?</h1>
Multer는 파일 업로드를 위해 사용되는 Node.js의 미들웨어이다. <br>
multipart, form-data 형식으로 단일/다중 파일 업로드를 지원한다.<br>
Multer가 많이 쓰이는 이유는 형식 지원의 이유도 있지만 사실상 DB에 이미지 파일과 같이 용량이 큰 파일을 넣는다는 게<br>
쉽지 않고, DB에 악영향을 끼칠 수 있기 때문에 차라리 서버 내 폴더 안에 사용하는 것이 낫기 때문이라고 생각한다.

<h2>사용법</h2>

```
const multer = require('multer');
const fs = require('fs'); // 폴더를 사용해야 하기 때문에 fs(File System)도 함께 사용해야 합니다.

try {
	fs.readdirSync('폴더명'); // 자신이 원하는 폴더명
} catch(err) {
	console.error(' 폴더가 없습니다. 폴더를 생성합니다.'); // 폴더가 없을 경우 생성
    fs.mkdirSync('uploads'); 
}

const upload = multer({
    storage: multer.diskStorage({ // 저장공간 정보를 하드 디스크에
        destination(req, file, done) { // 저장 위치
            done(null, '폴더명/'); // 폴더 내에 저장
        },
        filename(req, file, done) { // 파일명을 어떤 이름으로 올릴지.
            const ext = path.extname(file.originalname); // 파일의 확장자
            done(null, path.basename(file.originalname, ext) + Date.now() + ext); // 저장하기
        }
    }),
    limits: { fileSize:  } // x메가로 용량 제한 (예: 5 * 1024 * 1024 ) 5메가.
});
```
<br>

또한, 백엔드에서 프론트에게 요청받은 사진 값을 넘겨주고 싶을 때는, express.static(파일명) 이라는 것을 사용해야 한다.<br>
express.static()이란, 내 정적 파일을 프론트에게 서비스하기 위해 사용한다. <br>
사용법은 간단하다. app.use()를 통해 원하는 도메인에 매핑시켜 주기만 하면 사용 가능하다. <br>
이후부터는 프론트가 get메서드를 통해 접근하면 원하는 이미지를 끌어다 쓸 수 있다.
2023/08/01
