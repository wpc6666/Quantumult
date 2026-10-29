# Quantumult X 配置

> Quantumult X（圈 X）iOS 代理工具配置集 —— 策略组、远程/本地分流、URL 重写与 MITM。

[![Platform](https://img.shields.io/badge/Platform-iOS-000000?logo=apple&logoColor=white)](https://apps.apple.com/us/app/quantumult/id1252015438)
[![App](https://img.shields.io/badge/App-Quantumult-FF6B6B)](https://apps.apple.com/us/app/quantumult/id1252015438)
[![Config](https://img.shields.io/badge/Config-4%20files-2ea44f)](#配置文件)

**在线介绍页**：<https://wpc6666.github.io/Quantumult/>

> 本仓库现在包含 QX 格式配置；旧版 `5.17.conf` 和 `2014.11.01QX.conf` 保留用于回滚。

---

## 快速开始

1. 安装 **Quantumult**（App Store 美区 / 港区）。
2. 下载配置文件，或在 App 内「设置 → 配置文件」用链接导入。
3. 选中配置 → 回到首页打开开关。

### 订阅地址

```
# 较新版（推荐日常用）
https://raw.githubusercontent.com/wpc6666/Quantumult/refs/heads/main/2026.10.29-fast.conf

# 三策略主体 + available 自动故障转移兜底
https://raw.githubusercontent.com/wpc6666/Quantumult/refs/heads/main/2026.10.29-policy-only.conf

# 旧版
https://raw.githubusercontent.com/wpc6666/Quantumult/refs/heads/main/5.17.conf
https://raw.githubusercontent.com/wpc6666/Quantumult/refs/heads/main/2014.11.01QX.conf
```

---

## 配置文件

| 文件 | 行数 | 说明 |
|---|---|---|
| `2026.10.29-fast.conf` | 136 | 策略组快速版，兼容 QX 的 `[filter_remote]`，含 available 故障转移 |
| `2026.10.29-policy-only.conf` | 123 | 三策略主体 + available 自动故障转移兜底 |
| `5.17.conf` | 158 | 旧版策略化配置，保留用于回滚 |
| `2014.11.01QX.conf` | 220 | 完整版，含更多远程规则源与本地规则，适合细粒度控制 |
| `index.html` | — | 在线介绍页（GitHub Pages） |

### 段落结构

| 段落 | 作用 |
|---|---|
| `[general]` | 全局设置：网络检查、日志级别、超时 |
| `[dns]` | DNS 服务器与排除列表 |
| `[policy]` | 策略组：快速版使用；三策略版使用内置 direct / reject / proxy，并以 available 兜底 |
| `[server_remote]` | 远程节点订阅源 |
| `[filter_remote]` | 远程分流规则源 |
| `[rewrite_remote]` | 远程 URL 重写规则（部分旧配置使用） |
| `[server_local]` | 本地节点定义 |
| `[filter_local]` | 本地分流规则 |
| `[rewrite_local]` | 本地 URL 重写 |
| `[mitm]` | HTTPS 解密主机名列表 |
| `[task_local]` | 定时任务（签到、cookie 刷新等） |

---

## ⚠️ 注意事项

- **本仓库不含任何节点信息**。`[server_local]` 只有占位，节点需从你自己的机场导入。
- `[server_remote]` 中的旧订阅链接已移除，请在 QX 中添加你自己的订阅。
- **QX 转换说明**：原 Shadowrocket 的 `Ai.yaml` 改为 QX 可解析的 `ai.list`；`RULE-SET` 改写为 `[filter_remote]`。
- **远程规则源失效会导致部分站点走错策略**，请定期更新。
- `[task_local]` 里的定时任务依赖具体服务，换机场后需自行调整。
- `[mitm]` 默认只列了必要域名，可自行增删；开启解密前请确认信任对应证书。

---

## 目录结构

```
Quantumult/
├── 2026.10.29-fast.conf        # QX 策略组快速版
├── 2026.10.29-policy-only.conf # QX 三策略 + 故障转移版
├── 5.17.conf                   # 旧版配置
├── 2014.11.01QX.conf    # 完整版配置
├── index.html           # 在线介绍页
└── README.md
```

---

## 相关

- [Shadowrocket 配置](https://github.com/wpc6666/Shadowrocket)
- [作者主页](https://wpc6666.github.io/)

---

## 许可

配置中的规则部分来自公开社区列表，版权归原作者。本仓库的整合与说明部分采用 MIT License。
