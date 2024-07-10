# 使用 ```gh-pages``` 進行自動發佈


## 安裝 npm 套件 ```gh-pages```

1. 在專案目錄下使用 ```npm``` 進行安裝
    ```Powershell
    $ npm install gh-pages --save-dev
    ```

2. 當前的專案目錄下創建新的 ```git branch```
    ```Powershell
    $ git branch gh-pages
    ```

3. 確認當前是屬於```branch```, 切換到```main```主分支 (或是```master```)
    ```Powershell
    $ git checkout main
    ```
    or
    ```Powershell
    $ git checkout master
    ```

4. 調整 ```package.json``` 添加些指令進去
    ```
    "scripts": {
        "build": "gitbook build ./ ./_book",
        "deploy": "gh-pages -d _book -b gh_pages"
        },
    ```

5. 此時在 ```main``` 分支下完成後續的文本撰寫, 提交到遠端, 順便把新的分支 ```gh-pages``` 也提交
    ```Powershell
    $ git add .
    $ git commit -m "Add build and deploy scripts to package.json and update .gitignore"
    $ git push
    ```

6. 執行構建和部署
    ```Powershell
    $ npm run build
    $ npm run deploy
    ```
    會把 ```main``` 分支中的更動, 自動更新到遠端的 ```gh-pages``` 