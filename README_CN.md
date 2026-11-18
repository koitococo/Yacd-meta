> Yet Another [Clash](https://github.com/yaling888/clash) [Dashboard](https://github.com/yaling888/clash-dashboard)

## 用法

安装[twemoji](https://github.com/mozilla/twemoji-colr/releases)以在 Windows 系统上更好地显示表情符号。

网站 http://yacd.metacubex.one 是通过 HTTP 提供服务的，而不是 HTTPS，因为许多浏览器会阻止从 HTTPS 网站请求 HTTP 资源。如果认为这不安全，可以下载[gh-pages 的 zip 文件](https://github.com/MetaCubeX/yacd/archive/gh-pages.zip)，解压缩并使用 Web 服务器（如 Nginx）提供这些静态文件。

代理搜索支持 JavaScript 正则表达式，可搜索代理组、提供商或节点，忽略大小写。直接输入表达式，不带前后斜杠，例如 `HK|JP` 或 `^HK`。空输入显示全部，无效表达式无匹配。
组或 Provider 名称命中只保留对应卡片，旗下节点仍逐个按正则匹配，不会因父名称命中而全部显示。例如，`^(?!.*HK).*$` 可排除名称中包含 `HK` 的节点。
代理搜索表达式会保存在浏览器的 localStorage 中，刷新页面后自动恢复；清空搜索也会保存。
关闭搜索框左侧的开关可以暂停过滤，不会清空正则表达式。重新打开开关即可按当前表达式过滤；刷新页面也会重新启用搜索。
搜索期间，单组和全部收起/展开操作共用同一状态；批量操作只影响当前标签页中可见的卡片。更改搜索会重置临时折叠状态，清空或暂停搜索会恢复原有折叠偏好。

代理页测速按钮左侧的“刷新状态”会立即重新获取所有代理和提供商的健康检查状态及延迟历史，不受搜索过滤或前端查询缓存影响。此操作不会发起新的测速，也不会更新订阅；主动检测仍使用“全部测速”。

点击代理组标题栏的置顶按钮，可将一个代理组排到最前；置顶其他组会替换之前的置顶，取消置顶恢复后端顺序。置顶组仍受搜索过滤。

“隐藏不可用代理”旁的“隐藏无健康信息的代理”可独立隐藏尚无延迟检测结果的节点；检测失败也算有健康信息，代理组及 DIRECT/REJECT 等内置出口不受此开关影响。两个开关均作用于代理组和提供商的节点列表。置顶组和新增显示偏好保存在 localStorage，刷新后恢复。

**支持的 URL 查询参数**

| 参数     | 描述                                                               |
| -------- | ------------------------------------------------------------------ |
| hostname | Clash 后端 API 的主机名（通常是`external-controller`的 host 部分） |
| port     | Clash 后端 API 的端口号（通常是`external-controller`的 port 部分） |
| secret   | Clash API 密钥（`config.yaml`中的"secret"）                        |
| theme    | UI 颜色方案（dark、light、auto）                                   |

## 开发部署

```sh
# 安装依赖库
# 你可以从 https://bun.sh 安装 bun
bun install

 # 启动开发服务器
 # 然后访问 http://127.0.0.1:3000
 bun start

 # 构建优化资源
 # 准备好部署的资源将在目录 `public` 中
 bun run build
```
