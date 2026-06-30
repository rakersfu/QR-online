# 📱 QR Code Generator

一个现代、功能丰富的二维码生成器，支持自定义颜色、尺寸、格式和纠错等级。基于纯 HTML、CSS 和 JavaScript 构建，无需任何框架依赖。

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Node >= 14](https://img.shields.io/badge/node-%3E%3D14.0.0-brightgreen)](https://nodejs.org/)
[![GitHub Pages](https://img.shields.io/badge/deploy-GitHub_Pages-blue)](https://prabasajee.github.io/QR-generator)

---

## ✨ 特性

| 特性 | 说明 |
|------|------|
| ⚡ **快速生成** | 输入内容即可即时生成二维码 |
| 🎨 **高度可定制** | 支持前景色、背景色、尺寸、格式、纠错等级自定义 |
| 📱 **移动端友好** | 响应式设计，适配所有设备 |
| ♿ **无障碍访问** | 符合 WCAG 标准，支持 ARIA 标签和键盘导航 |
| 💎 **现代 UI** | 毛玻璃设计风格，搭配流畅动画效果 |
| 🔗 **多种数据类型** | 支持文本、URL、邮箱、电话、WiFi 等 |
| 📤 **分享功能** | 原生 Web Share API 支持，一键分享二维码 |

## 🚀 在线体验

直接访问 [GitHub Pages 演示](https://prabasajee.github.io/QR-generator) 开始使用。

## 🐳 Docker 部署

```bash
# 构建镜像
docker build -t qr-generator .

# 运行（浏览器访问 http://localhost:8000）
docker run -d -p 8000:80 --name qr-app qr-generator
```

## 📦 本地运行

```bash
# 方式一：使用 Node.js 内置 http-server
npm start

# 方式二：使用 npx 直接启动
npx http-server . -p 8000 -o
```

然后在浏览器中打开 `http://localhost:8000`。

## 📖 使用方法

### 网页端使用

1. 在文本框中输入要编码的内容（文本、URL、邮箱、电话号码等）
2. 选择二维码的尺寸、纠错等级和输出格式
3. 自定义前景色和背景色
4. 点击「Generate QR Code」按钮生成，或等待自动生成
5. 下载生成的二维码图片或分享

### Node.js 模块使用

```bash
npm install @prabasajee/qr-generator
```

```javascript
const QRCodeGenerator = require('@prabasajee/qr-generator');

const qrGenerator = new QRCodeGenerator();

// 生成基础二维码 URL
const qrUrl = qrGenerator.generateQRCodeURL('https://example.com');

// 自定义参数生成
const customQrUrl = qrGenerator.generateQRCodeURL('Hello World!', {
    size: 500,              // 尺寸（像素）
    errorCorrection: 'H',   // 纠错等级：L / M / Q / H
    format: 'png',          // 格式：png / jpg / gif / svg
    foregroundColor: '000080',  // 前景色（十六进制，不含 #）
    backgroundColor: 'ffffff'   // 背景色（十六进制，不含 #）
});

// 验证输入数据
const validation = qrGenerator.validateData('Your text here');
if (validation.valid) {
    const qrUrl = qrGenerator.generateQRCodeURL('Your text here');
    // 使用生成的 URL...
}
```

### 浏览器 Script 标签使用

```html
<script src="index.js"></script>
<script>
    const qrGenerator = new QRCodeGenerator();
    const qrUrl = qrGenerator.generateQRCodeURL('https://example.com');

    const img = document.createElement('img');
    img.src = qrUrl;
    document.body.appendChild(img);
</script>
```

## 🔧 配置选项

### 支持的尺寸

| 选项 | 值 |
|------|-----|
| 小 | 200 × 200 |
| 中 | 300 × 300（默认） |
| 大 | 400 × 400 |
| 超大 | 500 × 500 |
| 最大 | 1000 × 1000 |

### 纠错等级

| 等级 | 恢复能力 |
|------|----------|
| **L** (低) | ~7% |
| **M** (中) | ~15%（默认） |
| **Q** (四分位) | ~25% |
| **H** (高) | ~30% |

### 支持的数据类型

```javascript
// URL
qrGenerator.generateQRCodeURL('https://github.com/prabasajee/QR-generator');

// 邮箱
qrGenerator.generateQRCodeURL('mailto:user@example.com?subject=Hello&body=Hi%20there!');

// 电话
qrGenerator.generateQRCodeURL('tel:+8613800138000');

// SMS
qrGenerator.generateQRCodeURL('sms:+8613800138000?body=Hello%20World');

// WiFi
qrGenerator.generateQRCodeURL('WIFI:T:WPA;S:NetworkName;P:Password;H:false;;');
```

### API 参考

| 方法 | 说明 |
|------|------|
| `new QRCodeGenerator()` | 创建一个新的二维码生成器实例 |
| `generateQRCodeURL(data, options?)` | 生成二维码图片 URL |
| `validateData(data)` | 验证输入数据是否有效，返回 `{ valid, error }` |
| `getSupportedOptions()` | 获取所有支持的配置选项 |

## 🛠️ 技术栈

- **前端**: HTML5 · CSS3 · Vanilla JavaScript
- **字体**: Google Fonts (Inter)
- **API**: QR Server API (`api.qrserver.com`)
- **部署**: GitHub Pages / Docker / Nginx

## 📄 许可证

本项目采用 [MIT License](LICENSE) 开源协议。

## 🔗 相关链接

- [GitHub 仓库](https://github.com/prabasajee/QR-generator)
- [在线演示](https://prabasajee.github.io/QR-generator)
- [NPM 包](https://www.npmjs.com/package/@prabasajee/qr-generator)

---

Made with ❤️ by [prabasajee](https://github.com/prabasajee)
