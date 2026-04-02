# 匠心行 - 微信小程序

## 项目信息
- **Path**: `E:\Desk\Library\projects\village-exploration`
- **AppID**: wxb5abdec2d107a2a1
- **Repo**: https://github.com/whitefish666/village-exploration.git
- **CDN**: https://village-game-assets-1418646126.cos.ap-shanghai.myqcloud.com

## MCP连接 (WeChat DevTools)
调试小程序前必须先连接开发者工具：

### 第一步：关闭现有开发者工具
```bash
powershell -Command "Stop-Process -Name 'wechatdevtools' -Force -ErrorAction SilentlyContinue; Stop-Process -Name 'WeChatAppEx' -Force -ErrorAction SilentlyContinue"
```

### 第二步：启动开发者工具
```bash
cd "/e/software/微信web开发者工具" && ./cli.bat auto --project "e:/Desk/Library/projects/village-exploration" --auto-port 9420
```
成功标志：显示 `✔ auto`

### 第三步：确认端口
```bash
netstat -ano | grep 9420
```
确认有进程在端口 9420 监听。

### 第四步：连接MCP
在 Claude Code 中使用 `mp_ensureConnection` 工具：
```json
{
  "connection": {
    "mode": "connect",
    "projectPath": "E:\\Desk\\Library\\projects\\village-exploration",
    "wsEndpoint": "ws://127.0.0.1:9420"
  }
}
```

**注意**：如果 MCP 工具不可用，检查 `C:\Users\b4241\.claude\mcp.json` 中 `WEAPP_WS_ENDPOINT` 是否为 `ws://localhost:9420`

### 常用MCP工具
| 工具 | 用途 |
|------|------|
| `mp_ensureConnection` | 建立/重连到开发者工具 |
| `mp_currentPage` | 获取当前页面信息 |
| `mp_screenshot` | 截取当前页面 |
| `mp_navigate` | 页面导航 |
| `element_tap` | 点击元素 |
| `page_getData` | 获取页面 data |

## 资源CDN
- 游戏资源已迁移至腾讯云COS CDN
- 本地保留：`/assets/player.png`, `/assets/qr/*.png`
- 配置域名：`mp.weixin.qq.com → 开发管理 → 开发设置 → downloadFile合法域名`

## 游戏分包
- `pages/minigame/memory/` - 记忆游戏
- `pages/minigame/wheat/` - 麦田小游戏
- `pages/minigame/clay/` - 粘土小游戏
- `pages/music/` - 音乐播放器
- `pages/village-info/` - 村庄介绍
