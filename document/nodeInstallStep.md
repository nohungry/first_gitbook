# GitBook 安装

GitBook 使用 NPM 進行安裝, 命令行中輸入下面的命令進行安裝 :

```Powershell
$ npm install gitbook-cli -g
```
    -g : 全域安裝

![return](/image/gitbook-cli_version.jpg)

---

### 確認安裝完成

```powershell
$ gitbook -V
```
![return](/image/gitbook-cli_check.jpg)

---

# 遇到的問題

## 1. 使用 gitbook init, 彈出錯誤警告

```Powershell
$ gitbook init
```

![return](/image/gitbook_init_error.jpg)

打開 `C:\Users\<xxx>\AppData\Roaming\nvm\v18.20.2\node_modules\gitbook-cli\node_modules\npm\node_modules\graceful-fs\polyfills.js`

註解 62 - 64 行的code
```
// fs.stat = statFix(fs.stat)
// fs.fstat = statFix(fs.fstat)
// fs.lstat = statFix(fs.lstat)
```

## 2. 解決完第一步後, gitbook init, 彈出另外的錯誤警告

```Powershell
$ gitbook init
```

![return](/image/gitbook_init_error002.jpg)

執行 debug 命令

```powershell
$ gitbook init --debug
```

![return](/image/gitbook_init_error003.jpg)

打開 `C:\Users\<xxx>\.gitbook\versions\3.2.3\lib\init.js`

註解 72 行的code
```
// return fs.writeFile(filePath, summary.toText(extension));

return summary.toText(extension).then(stx=>{return fs.writeFile(filePath, stx);});
```
