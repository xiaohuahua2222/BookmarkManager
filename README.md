# BookmarkManager · 收藏助手

> 自托管的**个人书签与导航管理平台**：多级分类、公开/私有、导航墙与书签表双视图、全文搜索、主题换肤、AI 智能分类、访问统计，配套一键收藏的浏览器扩展。多用户数据隔离，单文件 SQLite，Docker 一键部署。

![公共首页-导航模式](docs/images/home-nav.svg)

**📖 完整说明文档（各页面图文详解、书签编辑表单、浏览器扩展、系统设置）：[docs/README.md](docs/README.md)**

---

## 快速开始

```bash
# 方式一：docker compose（在本目录执行）
docker compose up -d

# 方式二：docker run
docker run -d --name bookmarkmanager \
  -p 3080:3080 \
  -v "$PWD/bm-data:/data" \
  bookmarkmanager:latest
```

访问 `http://localhost:3080` → 首次进入**初始化向导**创建管理员账号即可。

> 数据全部落在挂载的 `/data` 目录（SQLite 库、配置、备份、日志、上传资源），只需挂载这一个目录。
> 自行构建镜像的构建上下文需为**上级 `.net` 目录**（详见完整说明文档的「自行构建」一节）。

---

## 功能一览

| 分类 | 能力 |
| --- | --- |
| **浏览** | 公共首页双视图：**导航模式**（分类卡片墙）/ **书签模式**（全量表格） |
| **检索** | 模糊搜索（标题 / 地址 / 描述），输入 ≥2 字自动触发 |
| **分类** | 一/二级分类，可折叠、可公开/私有、支持级联公开 |
| **多用户** | 账号体系，数据互相隔离；管理员可管理账号、开关开放注册 |
| **图标** | 书签：在线 favicon / 本地图片 / 图标库（Iconify、selfh.st）/ 文字色块 |
| **浏览器扩展** | Chrome / Edge 扩展**一键收藏**：弹窗收藏、右键快捷收藏、自动去重、可新建目录 |
| **批量操作** | 批量公开/私有、跨分类迁移、批量获取图标、拖拽排序 |
| **AI 能力** | OpenAI 兼容接口：自动推荐分类 + 网页端 AI 检索（SSE 流式） |
| **主题** | 跟随系统 + 多套预设（浅色/护眼/薄荷/樱粉/石墨/深色/商务…） |
| **统计** | 访问记录、点击轨迹、累计/今日访问与点击；开关可控、可清空 |
| **数据** | Chrome/Edge/Firefox 书签 HTML 及 JSON 导入导出；整库 / JSON 备份恢复 |
| **开放生态** | API 令牌 + 开放 API（`/api/v1/*`） |

---

## 界面预览

| 公共首页 · 导航模式 | 公共首页 · 书签模式 |
| --- | --- |
| ![导航模式](docs/images/home-nav.svg) | ![书签模式](docs/images/home-bookmark.svg) |
| **后台 · 书签管理** | **后台 · 分类管理** |
| ![书签管理](docs/images/admin-bookmarks.svg) | ![分类管理](docs/images/admin-categories.svg) |

<details>
<summary>展开查看更多界面预览</summary>

| 登录 / 初始化 | 书签编辑表单 |
| --- | --- |
| ![登录](docs/images/login.svg) | ![书签编辑](docs/images/bookmark-edit.svg) |
| **后台 · 系统设置** | **后台 · 访问统计** |
| ![系统设置](docs/images/admin-settings.svg) | ![访问统计](docs/images/admin-stats.svg) |
| **扩展 · 设置页** | **扩展 · 收藏弹窗** |
| ![扩展设置](docs/images/extension-options.svg) | ![扩展弹窗](docs/images/extension-popup.svg) |

</details>

> 以上为按真实前端界面还原的**界面预览图**（示例数据填充）。部署后用浏览器打开可看到实际效果；也可直接替换 `docs/images/` 下同名文件为真实截图。

---

## 文档导航

| 文档 | 内容 |
| --- | --- |
| [docs/README.md](docs/README.md) | **完整说明文档**（入口）：功能特性、各页面图文详解、书签编辑表单、技术栈、Docker 部署、系统设置、目录结构、常见问题 |
| `extension/README.md` | 浏览器扩展（Manifest V3）说明 |
| `docs/images/` | 各页面界面预览图（SVG） |

---

## 技术栈

.NET 8（Minimal API）+ Dapper + SQLite（WAL） ｜ Vue 3（全局构建，无打包）+ 原生 CSS ｜ Docker 多阶段构建

---

## 许可证

本项目供个人自托管使用。如需在更大范围分发或商用，请查看仓库中的许可证文件（或自行补充 `LICENSE`）。
