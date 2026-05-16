# Sub2API 部署

基于 Docker Compose 的 Sub2API 一键部署方案。

## 快速开始

```bash
# 1. 配置环境变量
cp .env.example .env
# 编辑 .env，设置 POSTGRES_PASSWORD 等必要参数

# 2. 创建数据目录
mkdir -p data postgres_data redis_data

# 3. 启动服务
docker compose up -d

# 4. 查看日志
docker compose logs -f

# 5. 访问
http://localhost:8080
```

## 目录结构

```
.
├── docker-compose.yml   # 服务编排配置
├── docker-deploy.sh     # 部署脚本
├── .env.example         # 环境变量模板
├── .env                 # 环境变量配置（已忽略，不提交）
├── data/                # 应用数据（已忽略）
├── postgres_data/       # 数据库数据（已忽略）
└── redis_data/          # 缓存数据（已忽略）
```

## 迁移到新服务器

```bash
docker compose down
tar czf sub2api-deploy.tar.gz .
# 传输到新服务器
tar xzf sub2api-deploy.tar.gz
docker compose up -d
```
