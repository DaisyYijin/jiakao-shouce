# 驾考手册

一个开箱即用的中文驾考练习网页雏形，可通过 Docker Compose 部署。当前版本为纯前端静态应用，无需数据库或外部 API。

## 功能

- 响应式学习首页与每日练习进度
- 科目一、科目四及交通标志专项练习
- 答题即时反馈、解析、错题回顾和题目收藏
- 今日答题量、累计答题、正确率、连续练习天数
- 使用浏览器 `localStorage` 保存练习数据

> 当前内置少量示例题目，用于演示功能和交互；并非完整、实时更新的官方题库。正式备考请以当地考试要求和最新官方资料为准。学习数据只存储在当前浏览器，不会同步至其他设备。

## 使用 Docker Compose 启动

要求安装 Docker Engine/Desktop 与 Docker Compose v2。在项目目录执行：

```sh
docker compose up -d --build
```

浏览器打开：<http://localhost:8080>

查看服务状态和健康检查：

```sh
docker compose ps
```

查看日志：

```sh
docker compose logs -f
```

停止服务：

```sh
docker compose down
```

### 修改访问端口

默认映射本机 `8080` 端口。如需更换，可执行：

```sh
PORT=9000 docker compose up -d --build
```

Windows PowerShell：

```powershell
$env:PORT = '9000'
docker compose up -d --build
```

此时访问 <http://localhost:9000>。

## 直接预览

也可以直接用现代浏览器打开 `index.html`。练习记录保存在当前浏览器的本地存储中。

## 项目文件

- `index.html`：单页应用、样式、示例题库和交互逻辑
- `Dockerfile`：构建 Nginx 静态站点容器
- `nginx.conf`：静态站点与健康检查路径配置
- `docker-compose.yml`：Compose 服务编排

## 题库与数据注意事项

本项目没有服务端，题库是示例数据并随 `index.html` 发布。新增、审核或更新题目需要编辑该文件中的题目数据。不要将浏览器本地存储当作账号级备份或多设备同步方案。
