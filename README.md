# json-open

把 JSON 直接在浏览器里可折叠查看（支持 `stdin` 和行内 JSON 字符串）。

> 一个给命令行用户准备的「JSON 临时观察器」：输入 JSON，立刻打开浏览器，以树形结构查看复杂响应。

---

## 为什么做这个

在终端里看 JSON，常见痛点是：

- 内容太长，滚动和定位困难
- 嵌套层级深，不容易快速理解结构
- 临时调试时不想引入重型工具

`json-open` 的目标很简单：**把“看 JSON”这一步变得顺手**。

---

## 功能特性

- ✅ 支持管道输入：`curl ... | json`
- ✅ 支持行内 JSON：`json '{"a":1}'`
- ✅ 浏览器树形展示（可折叠/展开）
- ✅ 一键全展开 / 全收起
- ✅ 本地临时文件渲染，不上传数据
- ✅ 跨平台打开浏览器（macOS / Linux / Windows）

---

## 安装

### 方式一：GitHub Packages（当前主分发）

先配置 npm 使用 GitHub Packages：

```bash
echo "@zjy4fun:registry=https://npm.pkg.github.com" >> ~/.npmrc
echo "//npm.pkg.github.com/:_authToken=YOUR_GITHUB_TOKEN" >> ~/.npmrc
```

然后安装：

```bash
npm i -g @zjy4fun/json-open
```

### 方式二：本地开发安装

```bash
git clone https://github.com/zjy4fun/json-open.git
cd json-open
npm install
npm link
```

安装后可直接使用 `json` 命令。

---

## 快速开始

```bash
# 1) 来自 API 响应
curl https://jsonplaceholder.typicode.com/todos/1 | json

# 2) 行内 JSON
json '{"hello":"world","list":[1,2,3]}'

# 3) 文件内容
cat response.json | json
```

执行后会自动打开浏览器，展示 JSON 树形视图。

---

## 常见应用场景

### 1. API 调试
快速查看接口响应结构，定位字段和嵌套层级。

### 2. 联调排错
后端返回结构变更时，用于快速比对是否缺字段/类型异常。

### 3. 临时数据检查
拿到一段 JSON（日志、消息队列、缓存快照）时，直接可视化排查。

### 4. 演示与沟通
和同事讨论响应结构时，用可折叠视图更直观。

---

## 命令说明

```bash
json
```

输入来源：

- 管道输入（stdin）
- 第一个参数作为 JSON 字符串

示例：

```bash
json '{"ok":true}'
```

无输入时会给出 usage 提示。

---

## 发布与分发

仓库已内置 GitHub Actions：

- `CI`：基础测试流程
- `Publish to GitHub Packages`：发布到 GPR
- `Publish to npm (Trusted Publishing)`：预留 npm OIDC 发布流程

当前主分发方式为 GitHub Packages。

---

## 参与贡献

欢迎提 Issue / PR，一起把这个小工具做得更顺手。

### 贡献方向建议

- 更好的错误提示（例如 JSON 语法定位）
- 支持主题切换（亮色/暗色）
- 支持从文件路径直接读取（如 `json ./data.json`）
- 更丰富的节点交互（搜索、高亮、路径复制）

### 本地开发

```bash
npm install
npm test
```

提交前请确保：

- 代码可运行
- README 示例可复现
- 保持改动小而清晰

---

## License

MIT
