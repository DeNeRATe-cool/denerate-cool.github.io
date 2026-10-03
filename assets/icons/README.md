# 条目图标

在 `_data/education.yml`、`_data/services.yml` 或 `_data/honors.yml` 的每条记录中填写：

```yaml
icon: "/assets/icons/tsinghua.svg"
```

省略 `icon` 或设置为 `""` 时不显示图标，也不会保留空白图标列。图标只辅助识别，完整信息仍由旁边的文字提供。所有 SVG 均为本地静态文件，不依赖图标字体或 JavaScript。

| 文件 | 用途 |
| --- | --- |
| `tsinghua.svg` | 清华大学校徽 |
| `beihang.svg` | 北航校徽 |
| `icpc.svg` | ICPC 官方标识，当前三项 ICPC 荣誉共用 |
| `gold-medal.svg` | 金牌（Phosphor，可选替代） |
| `silver-medal.svg` | 银牌（Phosphor，可选替代） |
| `ninebot.svg` | Ninebot 奖学金 |
| `rank-first.svg` | 学业成绩 / 综合测评第一名 |
| `challenge-cup.svg` | 挑战杯奖项（Phosphor 线条奖杯，非官方会徽） |
| `national-scholarship.svg` | 国家奖学金（国徽） |
| `teaching.svg` | 助教 |
| `presidium.svg` | 主席团 |

Education 校徽默认 48px（手机 40px），维持原有排版。Services 和 Honors 统一使用 28px 图标列和 12px 图文间距，实际图片通过 Flex 对齐标题第一行的中心；标题换行、说明文字或日期变长不会拉低图标。图标完整等比显示，不裁切，品牌标识保留原始比例与颜色。尺寸与间距在 `_sass/_homepage.scss` 中统一控制。

`gold-medal.svg`、`silver-medal.svg`、`rank-first.svg`、`teaching.svg`、`presidium.svg`、`challenge-cup.svg` 使用 Phosphor Regular 的原始矢量路径（MIT），仅适配颜色；出处与选型比较见 [SOURCES.txt](SOURCES.txt)，许可见 [Phosphor-LICENSE.txt](Phosphor-LICENSE.txt)。其他素材的来源和权利说明见 [INSTITUTION-SOURCES.md](INSTITUTION-SOURCES.md)、[COMPETITION-SOURCES.md](COMPETITION-SOURCES.md)。社交图标的说明仍见 [SOURCES.txt](SOURCES.txt)。
