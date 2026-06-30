# Nginx 配置结构解析

## 1. 主配置文件

**路径：** `/etc/nginx/nginx.conf`

负责全局参数（worker、日志、事件模型等）。

最后一行 `include /etc/nginx/conf.d/*.conf;` 会加载虚拟主机配置。

---

## 2. 虚拟主机配置

**路径：** `/etc/nginx/conf.d/default.conf`

- 默认监听 **80 端口**（IPv4 和 IPv6）
- `server_name localhost;` → 默认站点
- `location / { root /usr/share/nginx/html; index index.html index.htm; }` → 说明根目录就是 `/usr/share/nginx/html`，默认入口文件是 `index.html` 或 `index.htm`

---

## ✅ 实际效果

只要把 `index.html` 放到 `/usr/share/nginx/html/`，容器启动后就能通过 80 端口访问：

| 访问地址 | 显示内容 |
|---------|---------|
| `http://容器IP:80/` | `index.html` 内容 |
| `http://容器IP:80/test.html` | 放入的 `test.html` 内容 |

### 宿主机端口映射示例

如果在宿主机运行容器时使用了端口映射：

```bash
docker run -d -p 8080:80 nginx:alpine
```

则访问地址变为：

```
http://localhost:8080/
```
