<h1>백엔드 개발자를 꿈꾸는 강승훈입니다.</h1>
<br><br>
<h2>부산소마고에 재학 중이며, 열심히 살고 있어요:D</h2><br>

<h2>portfolio</h2><br />
한국어  - https://www.notion.so/s-backend-portfolio-1c5c8845b22347879ede91e9e6d19e21<br />
日本語　- <br />
<h3><a href="https://www.instagram.com/s.hoon__e/"><img src="https://img.shields.io/badge/Instagram-F557DA?style=flat-square&logo=instagram&logoColor=white"></a></h3>

<h1>Sequelize란?</h1>
Sequelize는 Node.js 환경에서 사용할 수 있는 강력한 ORM(Object-Relational Mapping) 라이브러리이다.<br>
ORM은 데이터베이스와의 상호 작용을 단순화하고 추상화하여 개발자가 SQL 쿼리를 직접 작성하지 않고도 데이터베이스와 상호 작용할 수 있도록 도와준다. <br>

<h2>사용법</h2>

```
npm i sequelize
npx sequelize init
```

<br>을 통해 sequelize를 설치한다.<br>
그 후 models에는 내가 작성하고 싶은 테이블명, config에는 database 연결문을 작성한다.<br>
models 내의 index.js에는<br>

```
const Sequelize = require("sequelize");
const config = require("../config")[process.env.NODE_ENV || "development"];
const db = {};

const sequelize = new Sequelize(
config.database,
config.username,
config.password,
config
);

db.파일명 = require("./파일링크")(sequelize, Sequelize);

Object.values(db).forEach((model) => {
if (model.associate) {
model.associate(db);
}
});

db.sequelize = sequelize;
db.Sequelize = Sequelize;

module.exports = db;
```

를 사용한다.
