---
title: 音声と動画の加工
slug: Web/Media/Guides/Audio_and_video_manipulation
l10n:
  sourceCommit: 6030ef1aadf967b80e2c79c3d3463cccc8ea0c95
---

ウェブのよいところは、複数の技術をまとめて新しいものを作ることができる点です。ネイティブの音声や動画をブラウザー上で利用できるということは、これらのデータストリームを {{htmlelement("canvas")}}、[WebGL](/ja/docs/Web/API/WebGL_API)、[ウェブオーディオ API](/ja/docs/Web/API/Web_Audio_API) を利用して操作することで、音声や動画に直接変更を加えることができることを意味します。例えば音声にリバーブやコンプレッション効果をかけたり、動画にグレイスケールやセピアのフィルターをかけたりすることができます。この記事では、必要なことを説明するためのリファレンスを提供します。

## 動画の加工

動画の各フレームからピクセルの値を読むことができることは、とても有用です。

### 動画とキャンバス

{{htmlelement("canvas")}} 要素はウェブページ上でグラフィックを描画するための平面を提供します。これは強力で、動画の処理にも有用です。

一般的なテクニックは次のようになります。

1. {{htmlelement("video")}} 要素からのフレームを中間の {{htmlelement("canvas")}} 要素に描画します。
2. 中間の `<canvas>` 要素からデータを取得し、それを加工します。
3. 加工したデータを「画面」の `<canvas>` を通じて描画します。
4. 一時停止し、繰り返します。

例えば、動画を処理してグレースケールで表示する場合を考えてみましょう。この場合、ソース動画と出力のグレースケールのフレームの両方を表示します。通常、「動画をグレースケールで再生」機能を実装する場合、 `display: none` を `<video>` 要素のスタイルに追加して、ソース動画が画面に描画されず、変更されたフレームのみが表示されるキャンバスが表示されるようにします。

#### HTML

動画プレイヤーと、 `<canvas>` 要素は次のように記述します。

```html
<video id="my-video" controls width="480" height="270" crossorigin="anonymous">
  <source
    src="https://jplayer.org/video/webm/Big_Buck_Bunny_Trailer.webm"
    type="video/webm" />
  <source
    src="https://jplayer.org/video/m4v/Big_Buck_Bunny_Trailer.m4v"
    type="video/mp4" />
</video>

<canvas id="my-canvas" width="480" height="270"></canvas>
```

#### JavaScript

このコードはフレームの加工を扱います。

```js
const processor = {
  timerCallback() {
    if (this.video.paused || this.video.ended) {
      return;
    }
    this.computeFrame();
    setTimeout(() => {
      this.timerCallback();
    }, 16); // 約 60 フレーム/秒
  },

  doLoad() {
    this.video = document.getElementById("my-video");
    this.c1 = document.getElementById("my-canvas");
    this.ctx1 = this.c1.getContext("2d");

    this.video.addEventListener("play", () => {
      this.width = this.video.width;
      this.height = this.video.height;
      this.timerCallback();
    });
  },

  computeFrame() {
    this.ctx1.drawImage(this.video, 0, 0, this.width, this.height);
    const frame = this.ctx1.getImageData(0, 0, this.width, this.height);
    const l = frame.data.length / 4;

    for (let i = 0; i < l; i++) {
      const grey =
        (frame.data[i * 4 + 0] +
          frame.data[i * 4 + 1] +
          frame.data[i * 4 + 2]) /
        3;

      frame.data[i * 4 + 0] = grey;
      frame.data[i * 4 + 1] = grey;
      frame.data[i * 4 + 2] = grey;
    }
    this.ctx1.putImageData(frame, 0, 0);
  },
};
```

ページの読み込み後に、次のように呼び出してください。

```js
processor.doLoad();
```

#### 結果

{{EmbedLiveSample("Video_and_canvas", '100%', 580)}}

これは、キャンバスを使用して動画フレームを加工する例です。効率をよくするために、対応しているブラウザーで実行する場合は {{domxref("Window.requestAnimationFrame", "requestAnimationFrame()")}} を `setTimeout()` の代わりに使用することを検討したほうがいいでしょう。

ソースの `<video>` 要素に CSS の {{cssxref("filter-function/grayscale", "grayscale()")}} 関数を適用しても、同じ結果が得られます。

> [!NOTE]
> 潜在的なセキュリティ上の問題があるため、動画がコードとは異なるドメインから配信されている場合は、動画サーバーで [CORS (オリジン間リソース共有)](/ja/docs/Web/HTTP/Guides/CORS) を有効にする必要があります。

### 動画と WebGL

[WebGL](/ja/docs/Web/API/WebGL_API) はキャンバスを使用してハードウェアアクセラレーションによる三次元や二次元の描画を行う強力な API です。 {{htmlelement("video")}} 要素と組み合わせることで、動画をテクスチャとして利用できます。つまり三次元空間上に動画を配置し、再生できます。

{{EmbedGHLiveSample('dom-examples/webgl-examples/tutorial/sample8/index.html', 670, 510) }}

> [!NOTE]
> [このデモのソースコードは GitHub](https://github.com/mdn/dom-examples/tree/main/webgl-examples/tutorial/sample8) にあります ([ライブで表示](https://mdn.github.io/dom-examples/webgl-examples/tutorial/sample8/)も)。

### 再生速度

音声や動画の再生速度は {{htmlelement("audio")}} または {{htmlelement("video")}} 要素の {{domxref("HTMLMediaElement.playbackRate", "playbackRate")}} プロパティを使用して調整できます。`playbackRate` には再生速度の倍率を指定します。例えば、0.5 を指定すると半分の速度で、2 を指定すると倍速で再生されます。

なお、`playbackRate` プロパティは `<audio>` と `<video>` の両方で動作しますが、再生速度を変更しても音程は*変わりません*。音声の音程を変更するには、ウェブオーディオ API を使用する必要があります。{{domxref("AudioBufferSourceNode.playbackRate")}} プロパティを参照してください。

```html live-sample___playback-rate
<video id="my-video" controls loop>
  <source src="/shared-assets/videos/flower.mp4" type="video/mp4" />
  <source src="/shared-assets/videos/flower.webm" type="video/webm" />
</video>
<label for="rate">再生速度 <span id="rate-value">1.0</span></label>
<input type="range" id="rate" name="rate" min="0" max="4" value="1" step=".2" />
```

```js live-sample___playback-rate
const rateSlider = document.getElementById("rate");
const rateValue = document.getElementById("rate-value");
const myVideo = document.getElementById("my-video");

rateSlider.addEventListener("input", () => {
  myVideo.playbackRate = rateSlider.value;
  rateValue.textContent = parseFloat(rateSlider.value);
});
```

```css hidden live-sample___playback-rate live-sample___audio-filter
body {
  font-family: sans-serif;
}
video,
label,
input {
  display: block;
  padding: 0.5em;
  width: 80%;
  margin: auto;
}
```

動画を再生し、スライダーを調整してメディアの再生速度を変更してください。

{{EmbedLiveSample('playback-rate', , 450)}}

## 音声の加工

`playbackRate` の一方で、音声を加工するためには [ウェブオーディオ API](/ja/docs/Web/API/Web_Audio_API) を利用することが一般的です。

### 音源の選択

ウェブオーディオ API は様々なソースから音声を受け取り、処理した後、出力機器を表す {{domxref("AudioDestinationNode")}} に送ります。

| この音声ソースの場合...                                                                                                                                   | 使用するウェブオーディオのノード型         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| HTML の {{HTMLElement("audio")}} または {{HTMLElement("video")}} 要素の音声トラック                                                                       | {{domxref("MediaElementAudioSourceNode")}} |
| メモリ内の生の音声データバッファー                                                                                                                        | {{domxref("AudioBufferSourceNode")}}       |
| サイン波やその他の合成波形を生成するオシレーター                                                                                                          | {{domxref("OscillatorNode")}}              |
| [WebRTC](/ja/docs/Web/API/WebRTC_API) の音声トラック (例えば {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} を使用して取得できるマイク入力)。 | {{domxref("MediaStreamAudioSourceNode")}}  |

### 音声フィルター

ウェブオーディオ API では {{domxref("BiquadFilterNode")}} を利用することで様々なフィルターやエフェクトを利用できます。

```html live-sample___audio-filter
<video id="my-video" controls loop>
  <source src="/shared-assets/videos/friday.mp4" type="video/mp4" />
</video>
<label for="freq">フィルター周波数 <span id="freq-value">1.0</span>hz</label>
<input type="range" id="freq" name="freq" max="20000" value="1000" step="100" />
```

```js live-sample___audio-filter
const freqSlider = document.getElementById("freq");
const freqValue = document.getElementById("freq-value");

const context = new AudioContext();
const audioSource = context.createMediaElementSource(
  document.getElementById("my-video"),
);
const filter = context.createBiquadFilter();
audioSource.connect(filter);
filter.connect(context.destination);

// フィルターを設定
filter.type = "lowshelf";
filter.frequency.value = 1000;
filter.gain.value = 20;

freqSlider.addEventListener("input", () => {
  filter.frequency.value = freqSlider.value;
  freqValue.textContent = parseFloat(freqSlider.value);
});
```

{{EmbedLiveSample('audio-filter', , 550)}}

> [!NOTE]
> [CORS](/ja/docs/Web/HTTP/Guides/CORS) を有効にしていない場合、セキュリティ上の問題を避けるため、動画はコードと同じドメイン上に置く必要があります。

#### よく使われる音声フィルター

このノードでよく利用されるフィルターは以下の通りです。

- ローパス: カットオフ周波数より低い周波数を通過させ、高い周波数を減衰させます。
- ハイパス: カットオフ周波数より高い周波数を通過させ、低い周波数を減衰させます。
- バンドパス: 指定された周波数帯を通過させ、その範囲より低い周波数と高い周波数を減衰させます。
- ローシェルフ: すべての周波数を通過させますが、低い周波数を増幅（または減衰）させます。
- ハイシェルフ: すべての周波数を通過させますが、高い周波数を増幅（または減衰）させます。
- ピーキング: すべての周波数を通過させますが、指定された周波数帯を増幅（または減衰）させます。
- ノッチ: 指定された周波数帯を除き、すべての周波数を通過させます。
- オールパス: すべての周波数を通過させますが、周波数間の位相関係を変化させます。

> [!NOTE]
> 詳しくは {{domxref("BiquadFilterNode")}} を参照してください。

### たたみ込みとインパルス

{{domxref("ConvolverNode")}} を利用することで、音声に**インパルス応答**を適用することができます。インパルス応答とはハンドクラップのような短い音のインパルスから作成された音のことです。インパルス応答はインパルスが作られた環境 (例えばトンネル内で手を叩くことで発生するエコー) を示します。

#### 例

```js
const convolver = context.createConvolver();
convolver.buffer = this.impulseResponseBuffer;
// オーディオグラフを接続
source.connect(convolver);
convolver.connect(context.destination);
```

適用例として [HolySpaceCow](https://mdn.github.io/webaudio-examples/holy-space-cow/) を参照してください（とても、とてもばかげた例ですが）。

### 空間的な音

**パンナーノード**を使用することで、音源の位置を操作できます。パンナーノード—{{domxref("PannerNode")}}—は、ソースコーンの位置だけでなく、その方向も指定することができます。位置や方向は三次元空間上で指定します。

#### 例

```js
const panner = context.createPanner();
panner.coneOuterGain = 0.2;
panner.coneOuterAngle = 120;
panner.coneInnerAngle = 0;

panner.connect(context.destination);
source.connect(panner);
source.start(0);

// リスナーを原点に配置
context.listener.setPosition(0, 0, 0);
```

> [!NOTE]
> [GitHub リポジトリに例](https://github.com/mdn/webaudio-examples/tree/main/panner-node)があります ([ライブ版](https://mdn.github.io/webaudio-examples/panner-node/)も)。

## 例

- [様々なウェブオーディオ API (およびその他) の例](https://github.com/mdn/webaudio-examples)
- [THREE.js Video Cube example](https://github.com/chrisdavidmills/threejs-video-cube)
- [Convolution Effects in Real-Time](https://github.com/cwilso/web-audio-samples/blob/master/samples/audio/convolution-effects.html)

## 関連情報

### チュートリアル

- [キャンバスを使用した動画の加工](/ja/docs/Web/API/Canvas_API/Manipulating_video_using_canvas)
- [HTML playbackRate の解説](/ja/docs/Web/Media/Guides/Audio_and_video_delivery/WebAudio_playbackRate_explained)
- [ウェブオーディオ API の利用](/ja/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [ウェブオーディオの空間化の基本](/ja/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)
- [動画フレームの WebGL テクスチャとしての利用](/ja/docs/Web/API/WebGL_API/Tutorial/Animating_textures_in_WebGL#動画フレームをテクスチャとして使用する) ([THREE.js](https://threejs.org/) WebGL ライブラリ (及びその他) と [この効果の実現](https://stemkoski.github.io/Three.js/Video.html))
- [WebGL におけるアニメーションテクスチャ](/ja/docs/Web/API/WebGL_API/Tutorial/Animating_textures_in_WebGL)
- [ウェブオーディオ API を使ったゲーム音声の開発（ルームエフェクトとフィルター）](https://web.dev/articles/webaudio-games#room_effects_and_filters)<sup>(英語)</sup>

### リファレンス

- {{htmlelement("audio")}} および {{htmlelement("video")}} 要素
- {{domxref("HTMLMediaElement")}} API
- {{htmlelement("canvas")}} 要素
- [ウェブオーディオ API](/ja/docs/Web/API/Web_Audio_API)
- [AudioContext](/ja/docs/Web/API/AudioContext)
- [空間オーディオ](/ja/docs/Web/API/BaseAudioContext/createPanner)の詳細情報
- [ウェブメディア技術](/ja/docs/Web/Media)
