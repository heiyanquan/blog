方案一：让 Codex 同时“看见”两个代理（推荐先试这个）

既然 Codex 需要同时用到 VPN（为了访问外部网络）和 CC Switch（为了管理供应商），最直接的办法就是告诉 Codex 这两个代理都存在。

打开或新建 Codex 的配置文件（Windows 在 C:\Users\你的用户名\.codex\.env，Mac/Linux 在 ~/.codex/.env），写入以下内容（假设你的 VPN 端口是 7890）：

ini
HTTP_PROXY="http://127.0.0.1:7890"
HTTPS_PROXY="http://127.0.0.1:7890"
ALL_PROXY="socks5h://127.0.0.1:7890"
NO_PROXY="localhost,127.0.0.1,::1"
关键点：NO_PROXY 里必须包含 127.0.0.1。这能确保 Codex 访问本机的 CC Switch 服务时，不会把这个请求也傻傻地丢给 VPN 代理，从而避免本地回环冲突。
