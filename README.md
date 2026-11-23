# 湘湘的成长日记 ♡

单文件静态网页，给桓桓部署到 GitHub Pages 用。

## 怎么部署

1. 新建一个仓库，把 `index.html` 放在**仓库根目录**（文件名必须是 `index.html`）。
2. Settings → Pages → Source 选 `Deploy from a branch`，分支 `main`、目录 `/ (root)`，保存。
3. 等 1 分钟左右，地址是 `https://<用户名>.github.io/<仓库名>/`。

整个网页只有这一个文件，CSS、JS、所有插画（花瓣、草莓、信封、邮票）都内联在里面，不依赖本地图片，
所以在 GitHub Pages 上不会出现裂图。字体从 CDN 取（ZCOOL KuaiLe / Noto Sans SC / Noto Serif SC），
取不到时自动退回系统字体，页面仍然成立。

## 怎么改内容

都在 `index.html` 里，用编辑器搜索关键词就能定位：

| 想改什么 | 搜什么 |
| --- | --- |
| 首页大标题 / 副标题 / 核心句 | `hero__title`、`hero__sub`、`hero__core` |
| 相册那五段话 | `album__text` |
| 三张顿悟便签（日期、句子、背面留白） | `note__quote`、`note__date`、`note__slottext` |
| 桓桓的信 | `paper__hi` 往下的 `<p>` |
| 结尾两句和署名 | `future__line`、`footer__name` |

### 换成真实照片

相册里四个占位框，每个长这样：

```html
<div class="frame__img"><b>＋</b><span>放一张照片</span></div>
```

把它整行换成（照片放在 `assets/` 目录里，用相对路径）：

```html
<div class="frame__img"><img src="assets/photo1.jpg" alt="那一天的我" style="width:100%;height:100%;object-fit:cover;"></div>
```

注意：一旦有图片文件，仓库里就要多一个 `assets/` 目录，一起提交。

### 便签背面的留白

三张便签翻过来是空的，写着「这一格先空着」。想补故事，搜 `note__slottext`，
把里面的提示句换成那天真实发生的事就行。

## 交互清单

- 首屏小种子发芽、抽茎、开花，花瓣依次绽开
- 「开始我的小故事 ♡」平滑滚到相册
- 三张便签点击翻转（`aria-pressed` 同步，键盘可用）
- 信封：点「拆开看看 ♡」，封蜡收起、封口掀开、信纸升起；可反复开合
- 「嘿嘿，收到啦！😋」→ 爱心与樱花四散
- 结尾两个按钮 → 「这里正在等待更多故事呀 ♡」弹窗（Esc / 点遮罩可关）
- 右下角小草莓，点一下会蹦跶并撒爱心
- 桌面端鼠标移动有细碎星光，右上角有章节导航点
- 支持 `prefers-reduced-motion`：系统开启「减少动态效果」时全部动画自动关闭

## 已知边界

- 没有后端、数据库、登录，纯静态
- 便签背面的故事是留白，没有替她编内容
- 相册是占位框，还没接真实照片
- 这是公网页面：里面的信是真实聊天内容改写，发布前自己确认一次要不要公开

> （注：部分内容由豆包 AI 生成）