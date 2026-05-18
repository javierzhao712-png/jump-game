# 跳一跳 (Jump Jump) - 3D Web 游戏

## 项目概述
单文件 3D 跳一跳网页游戏，使用 Three.js，类似微信小程序风格。分享给朋友玩的。

## 文件结构
- `index.html` — 游戏主文件（含 HTML/CSS/JS）
- `three.min.js` — Three.js 0.160 本地副本（不依赖外部 CDN）

## 线上地址
- GitHub Pages: https://javierzhao712-png.github.io/jump-game/
- Gitee: 代码已推送但 Pages 未启用（需实名认证后手动部署）

## 部署
```bash
git add index.html three.min.js && git commit -m "更新" && git push
```
GitHub Pages 自动部署，等约 1 分钟后生效。

## 游戏玩法
- 按住屏幕蓄力，松开跳跃
- 跳到下一个平台 +1 分
- 连续命中平台中心：分数翻倍（2→4→8→16...）
- 没命中中心则连击中断
- 跳空（没落在任何平台上）→ 游戏结束
- 落在当前平台（蓄力不够）→ 存活，可重新跳

## 技术要点
- Three.js 通过 `<script>` 标签加载 UMD 版本，不用 ES module
- 音效全部 Web Audio API 合成，无外部音频文件
- 背景音乐：五声音阶循环旋律，首次触摸启动
- 蓄力音效：低频嗡嗡声，频率随蓄力升高
- 腾空音效：三角波+频率抖动模拟风声
- 移动端：Pointer Events + touch-action: none + 禁止缩放
- 相机：落地后延迟 200ms，然后双层 lerp 平滑过渡（不跟随跳跃）

## 当前状态
- 游戏功能完整可玩
- 辅助功能（蓄力条、着陆预览环）已移除
- 完美命中显示 "完美 xN! +分数" 弹窗
- 最高分存储在 localStorage

## 用户偏好
- 不要辅助功能（蓄力条、预览环都去掉了）
- 镜头不要跟着跳跃移动，落地后平滑过渡即可
- 需要背景音乐和音效
- 分享给微信好友玩，URL 直接打开
