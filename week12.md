## 服务器的配置

- 下载环境

  ~~~
  // 下载node.js
  sudo apt install nodejs
  // 下载npm
  sudo apt install npm
  // 下载node版本管理包
  sudo npm install -g n
  // 下载最新班node.js，利用n下载
  sudo n latest
  ~~~
  http:// mirrors.aliyun.com/ubuntu

  

- 初始化express

  ~~~
  npx express-generator
  ~~~

  

- 服务端配置

  ~~~
  // 启动ssr
  service ssh start
  //
  scp -P 8022 -r ./* fan@127.0.0.1:/home/fan/server
  ~~~

  

## node.js的API的使用

- fs.createReadStream

  ~~~javascript
  // 读取文件
  let file = fs.createReadStream('./index.html');
  // 监听文件的传输
  file.on('data', chunk => {
      console.log(chunk.toString());
      request.write(chunk);
  })
  file.on('end', () => {
      request.end();
      console.log('file finished');
  
      // request.end();
  })
  // 可读流上调用该方法时会发出该事件，并将此可写内容添加到其目标集。
  file.pipe(request) // 快捷发送流处理
  ~~~

- fs.createWriteStream

  ~~~javascript
  // 写入文件
  var setFile = fs.createWriteStream('../server/public/index.html');
  // 监听写入的文件
  request.on('data', chunk => {
  	setFile.write(chunk);
  })
  request.on('end', chunk => {
  	response.end('hello world');
  }) 
  // 可读流上调用该方法时会发出该事件，并将此可写内容添加到其目标集。
  file.pipe(request) // 快捷发送流处理
  ~~~

- fs.stat

  ~~~javascript
  // 获取文件的大小
  fs.stat('./index.html', (err, stats) => {
  	// stats.size
  }
  ~~~

  

- 压缩包archive模块的使用

  ~~~javascript
  // 下载依赖
  // npm install --save archiver
  const archive = require('archive');
  
  // 创建实例
  const archive = archive('zip', {
      zlib: {level: 9} //Sets the compression level
  })
  
  archive.directory('./path', false);
  // 调用完成后方法
  archive.finalize();
  ~~~

  

- 解压包unzipper模块的使用

  ~~~javascript
  // 下载依赖
  // npm install --save unziper
  fs.createReadStream('path/to/archive.zip')
    .pipe(unzipper.Extract({ path: 'output/path' }));
  ~~~

  

## git HOOKS的基本使用

- 查看文件及文件的操作

  ~~~
  ls -a //查看所有的文件
  start .git // 打开文件
  ls -l ./pre-commit // 查看文件的权限
  chmod +x ./pre-commit // 添加文件执行的权限
  
  git stash -k // 将代码暂存
  git stash pop // 将代码从暂存去出来
  ~~~

  

- pre-commit运行

  ~~~
  #!/usr/bin/env node //声明使用的语言
  
  let process = require('process'); // 使用node.js的process模块
  let child_process = require('child_process'); // 使用node.js的child_process模块，进行git命令的操作
  process.exitCode(1);
  process.exit(); // 退出不进行操作
  // 改写child_process的exec方法，以为exec方法是回调的形式。
  function exec(code) {
      return new Promise((resovle) => {
          child_process.exec(code, resovle);
      });
  }
  ~~~

  

## ESlint的基本使用

- 配置ESlint

  ~~~
  npm install --save-dev eslint // 下载eslint的包
  
  npx eslint --init // 初始化配置eslint
  
  npx eslint ./index.js // 使用eslint来检查指定的文件
  ~~~

## headless无头浏览器

- 无头浏览器的使用

  ~~~
 
  ~~~

  