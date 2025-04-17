# dynamic-survey

`dynamic-survey` 是一個基於前端 `dynamic-survey-ui` 與後端 `dynamic-survey-api`，前後端分離的**動態問卷系統**，專門用於創建、管理和分析動態問卷調查。本系統提供靈活的問卷設計、即時回饋、統計分析等功能，並適用於市場研究、用戶滿意度調查等多種場景。

## Project Structure

專案架構（Figma），請參考 [`動態問卷系統`](https://www.figma.com/design/7jcsPZxB0Q26WYPpvk3tzr/%E5%8B%95%E6%85%8B%E5%95%8F%E5%8D%B7%E7%B3%BB%E7%B5%B1-Template_For_Class-)。

## Key Features

- **問卷管理**：創建、更新和刪除問卷，支持基於多種條件（如名稱、日期等）進行問卷模糊查詢。
- **問卷填寫**：用戶可以填寫問卷，並即時提交答案。
- **數據與統計**：查詢問卷資料、回饋資料及統計數據，並支持圖表化展示。

## Tech Stack

此專案使用以下技術：

- **前端**：[`dynamic-survey-ui`](https://github.com/rikka0823/dynamic-survey-ui)。
- **後端**：[`dynamic-survey-api`](https://github.com/rikka0823/dynamic-survey-api/tree/main)。
- **Nginx**：作為靜態網頁資源的存放伺服器，並以反向代理（Reverse Proxy）的技術，將前端 Angular 應用程式的請求路由轉向後端的 Spring Boot 服務。
- **Docker**：採用 Docker Compose 的三層式架構（three tier architecture），前端（ui）、後端（api）、資料庫（db）個別容器化及整合的技術，簡化部署流程。

## Running the Project in Docker

在執行以下 Shell 指令前，請先確保電腦安裝及啟動 Docker：

- `docker-compose build --no-cache`：建立 Spring Boot 應用程式和 MySQL 資料庫的 Docker 映像檔（image），並強制不使用 Cache。
- `docker-compose up -d`：啟動 docker-compose，並在 Docker daemon 背景中運作所有容器。
- `docker-compose down`： 停止、移除運作中的容器，並且移除相關的映像檔（image）。
- `docker volume rm dynamic-survey-api_db-data`：移除本地 Docker Volume 中存放的資料庫資料。

容器順利運作後，請直接於網址列上輸入**localhost**，並可依需求輸入 Shell 指令停止、移除運作中的容器，停止服務。
