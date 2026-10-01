# Academic homepage

个人学术主页：<https://denerate-cool.github.io/>

仓库：<https://github.com/DeNeRATe-cool/denerate-cool.github.io>

使用 Jekyll、Markdown 和 YAML，从零编写布局、样式和组件。视觉参考 [Minimal Light](https://github.com/yaoyao-liu/minimal-light)，未复制其模板或使用远程主题。无 JavaScript、数据库、外部字体或分析追踪。

## 填写内容

方括号中的文字都是待替换的占位内容。没有个人信息的链接留空，页面不会生成空链接。

| 内容 | 编辑位置 |
| --- | --- |
| 姓名、身份、单位、邮箱、GitHub、LinkedIn、头像 | `_config.yml` |
| About me、Research interests、栏目顺序 | `index.md` |
| 教育经历（位于 About me 内） | `_data/education.yml` |
| News | `_data/news.yml` |
| Publications | `_data/publications.yml` |
| Services | `_data/services.yml` |
| Honors | `_data/honors.yml` |

- 头像放在 `assets/img/`，然后修改 `_config.yml` 的 `avatar`。初始头像是本项目绘制的占位 SVG。
- `email` 填原始邮箱地址；`linkedin` 填完整个人主页网址。空值时侧栏仅显示占位文字。
- News、论文、教育和荣誉按文件顺序显示，建议最新内容在前。Services 按 `category` 分组，并保留输入顺序。
- 复制列表中的一条记录即可新增内容。日期和带冒号的文本建议用引号包裹。
- Markdown 可用于 About me、News 的 `text`、论文的 `authors` / `notes` / `others`，以及各项 `description`。例如 `**姓名**` 或 `[链接文字](https://example.com)`。
- 清空栏目时保留有效 YAML：一般列表使用 `[]`，论文使用 `main: []`。若不想显示整个栏目，同时移除 `index.md` 中对应的 include 和 `_layouts/homepage.html` 中的导航链接。

## 数据字段

| 文件 | 字段 |
| --- | --- |
| `education.yml` | `institution` 学校，`degree` 学位，`field` 专业，`period` 时间，`description` 可选说明 |
| `news.yml` | `date` 日期（如 `2026-10`），`text` 动态内容 |
| `publications.yml` | `main` 列表中每条的 `title` 标题，`authors` 作者，`conference` 发表渠道或状态；可选 `conference_short`、`pdf`、`code`、`page`、`bibtex`、`image`、`image_alt`、`notes`、`others` |
| `services.yml` | `category` 类别，`role` 职务，`organization` 单位或课程，`period` 时间，`description` 可选说明 |
| `honors.yml` | `title` 荣誉，`organization` 颁发单位，`year` 年份，`description` 可选说明 |

论文保留 Minimal Light 的 `main` 数据结构与常用字段，但展示组件独立实现。`conference` 使用纯文本；作者加粗可使用 Markdown。无配图时不留图片空位。仅非空的 PDF、Code、Project、BibTeX 链接会显示。

站内文件使用 `/assets/files/paper.pdf` 这样的路径，外部链接使用完整网址。公开附件放在 `assets/files/`；提供配图时填写 `image_alt` 描述图片内容。

## 本地预览

安装较新版本的 Ruby 和 Bundler 后，在仓库目录执行：

```sh
bundle install
bundle exec jekyll serve
```

打开 <http://localhost:4000>。修改 `_config.yml` 后重启预览。构建检查可使用 `bundle exec jekyll build`，生成结果在已忽略的 `_site/` 中。

## GitHub 自动部署

仓库必须使用 `denerate-cool.github.io`，默认网址固定为 <https://denerate-cool.github.io/>。

1. 打开仓库 **Settings → Pages**。
2. **Source** 选择 **Deploy from a branch**。
3. 选择 **main** 和 **/(root)**，保存。
4. 此后提交或合并到 `main`，GitHub 会自动运行 Jekyll 并更新网站。在 **Actions** 查看构建和部署结果。

无需自行编写 Actions 工作流。`_config.yml` 中保留 `url: "https://denerate-cool.github.io"` 和 `baseurl: ""`。不使用自定义域名，因此不创建 `CNAME`；也不添加会跳过 Jekyll 的 `.nojekyll`。

日常更新可以直接在 GitHub 上编辑 Markdown / YAML 并提交，也可以本地修改后推送。发布前检查文字、链接、头像，以及手机显示。

## 文件组织

`_data/` 保存内容，`_includes/` 渲染栏目，`_layouts/homepage.html` 组织整页，`_sass/_homepage.scss` 定义样式，`assets/css/main.scss` 是 Jekyll 编译样式的入口。页面随系统切换浅色或深色模式，小屏幕上侧栏移到正文上方。

## License

本项目代码使用 [MIT License](LICENSE)。后续添加的论文、照片及其他附件请保留各自的授权说明。
