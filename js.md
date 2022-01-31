# Javascript, Typescript, Node

## 非同期実装の種類

JSでは非同期実行する関数があるが、その実行順の保証についてはコールバック地獄、Promise、async/awaitとある。

### コールバックで順番制御 (コールバック地獄)
`fs.readFile` は非同期実行。以下実行順は保証されない。
```
const fs = require('fs');

fs.readFile('text_01.json', 'utf-8', (err, data) => {
  console.log(data);
});
fs.readFile('text_02.json', 'utf-8', (err, data) => {
  console.log(data);
});
fs.readFile('text_03.json', 'utf-8', (err, data) => {
  console.log(data);
});
```

のでコールバックで保証する

```
const fs = require('fs');

fs.readFile('text_01.json', 'utf-8', (err, data) => {
  console.log(data);
  fs.readFile('text_02.json', 'utf-8', (err, data) => {
    console.log(data);
    fs.readFile('text_03.json', 'utf-8', (err, data) => {
      console.log(data);
    });
  });
});
```

これだとネストが深くなる。(コールバック地獄)

### Promise(ES2015-)

```
const fs = require('fs');

function readFile() {
  return new Promise((resolve) => {
    fs.readFile(file, 'utf-8', (err, data) => {
      resolve(data);
    });
  });
}

readFile('text_01.json')
  .then((data) => {
    console.log(data);
    return readFile('text_02.json');
  })
  .then((data) => {
    console.log(data);
    return readFile('text_02.json');
  })
  .then((data) => {
    console.log(data);
    return readFile('text_02.json');
  });
```

### async/await (ES2017)

async
```
const fs = require('fs');

function readFile() {
  return new Promise((resolve) => {
    fs.readFile(file, 'utf-8', (err, data) => {
      resolve(data);
    });
  });
}

async function readFiles() {
  text_01 = await readFile('text_01.json');
  console_log(text_01);
  text_02 = await readFile('text_02.json');
  console_log(text_02);
  text_03 = await readFile('text_03.json');
  console_log(text_03);
}

readFiles();
```

参考元: [【初心者向け】JavaScriptの非同期処理を理解する　callback、Promiseそしてasync/awaitへ - Qiita](https://qiita.com/G-awa/items/652107a9abf7ff6d0d06)

## Node 特有

### process

- process.exit(0)  
終了

- process.argv[2]  
node実行時の引数などの取得。など、としたのは0,1が違うため  
0: 実行しているnodeのフルパス
1: 実行されたファイルのフルパス
2以降は引数にわたした順番

