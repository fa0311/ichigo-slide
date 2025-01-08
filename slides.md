---
theme: eloc
title: ichigo-slide
transition: slide-left
mdc: true
highlighter: shiki
---

# ichigo-slide

いちごの物体検出についての正規化とデータ拡張

---

## 問題点

<ul>
  <li>データセットの不足</li>
  <li>色から輪郭を抽出していたため、雑に輪郭を抽出していた</li>
  <li>データセットの解像度が低い</li>
</ul>

<div grid="~ cols-2 gap-2" m="t-2">
  <img src="/hi(81).jpg" style="object-fit: contain;height: 500px;">
  <img src="/33_hi(81).jpg" style="object-fit: contain;height: 500px;">
</div>

---

## データセットの正規化

<ul>
  <li>人力で正規化</li>
  <li>ソースの画像を用いて正規化する</li>
</ul>

---

## 正規化ツールの開発

<ul>
  <li>出来るだけ人間の負荷を減らす</li>
  <li>AIを用いて背景を除去</li>
  <li>AIは完璧ではないので、残りは人間が手動で修正する</li>
</ul>

<img src="/image1.png" style="object-fit: contain; height: 500px;">

<v-click>
  <div class="center">
    <img src="/image1.png" style="object-fit: contain;">
  </div>
</v-click>

---

## 正規化ツールの開発

<ul>
  <li>u2netやsamなどで背景を除去</li>
  <li>GPUもサポート</li>
</ul>

<div grid="~ cols-2 gap-2" m="t-2">
  <img src="/image2.png">
  <img src="/image3.png">
</div>

---

## モデル別AIの違い

<ul>
  <li>u2net(左から2番目)が軽量な上に、精度が高い</li>
  <li>CPUでも十分な速度で動作する</li>
</ul>

<img src="/image-1-1.png" style="object-fit: contain; height: 500px;">

<v-click>
  <div class="center">
    <img src="/image-1-1.png" style="object-fit: contain;">
  </div>
</v-click>

---

## データ拡張

<ul>
  <li>データそのものに色補正を行う</li>
  <li>明るさやカメラ性能による色の違いを吸収する</li>
  <li>HSV色空間を用いて、色相、彩度、明度を変更する</li>
</ul>

<img src="/hsv_1.0.png" style="object-fit: contain; height: 500px;">

<v-click>
  <div class="center">
    <img src="/hsv_0.5.png" style="object-fit: contain;">
  </div>
</v-click>
<v-click>
  <div class="center">
    <img src="/hsv_0.8.png" style="object-fit: contain;">
  </div>
</v-click>
<v-click>
  <div class="center">
    <img src="/hsv_1.0.png" style="object-fit: contain;">
  </div>
</v-click>
<v-click>
  <div class="center">
    <img src="/hsv_1.2.png" style="object-fit: contain;">
  </div>
</v-click>
<v-click>
  <div class="center">
    <img src="/hsv_1.5.png" style="object-fit: contain;">
  </div>
</v-click>

---

## データ拡張

<ul>
  <li>大きさと位置を変更する</li>
  <li>背景にノイズを加える</li>
</ul>

<div grid="~ cols-4 gap-2" m="t-2">
  <img src="/hi(81)_0.jpg">
  <img src="/hi(81)_1.jpg">
  <img src="/hi(81)_2.jpg">
  <img src="/hi(81)_3.jpg">
</div>

---

## VOC形式への自動変換

<ul>
  <li>データセットの形式を統一</li>
  <li>既存のツールをそのまま使える</li>
  <li>テストデータも自動で作成</li>
</ul>

<div grid="~ cols-4 gap-2" m="t-2">
  <img src="/hi(81)_2_0.png">
  <img src="/hi(81)_2_1.png">
  <img src="/hi(81)_2_2.png">
  <img src="/hi(81)_2_3.png">
</div>

<!--
aa確率的勾配降下法
-->

---

## 学習

<ul>
  <li>SGDの閾値を50分の1に変更することで学習率改善</li>
  <li>図の緑色</li>
</ul>

<img src="/画像 (2).png" style="object-fit: contain; height: 500px;">
