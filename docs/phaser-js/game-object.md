# Game object

## Event

[Phaser3 issue 116](https://madmimi.com/p/a022cb)
- pointerdown
- pointerup
- pointermove

[setInteractive](http://www.html5gamedevs.com/topic/36248-setinteractive-on-a-whole-group/)

## Container

## Group

## Text

### Input

這部分原本希望能夠寫出類似`原生 HTML`的`<input/>`，但受限於瀏覽器的限制，並沒有辦法在手機上直接叫出`輸入鍵盤`，具體情況請看[Reference](http://www.iamaddy.net/2016/11/mobile-keyboard-javascript/)，因此在使用上只剩下下列兩種方法:

1. [prompt](https://developer.mozilla.org/en-US/docs/Web/API/Window/prompt)

  - [Good] 實現簡單
  - [Bad] 用戶多一道操作，且部分瀏覽器並不會 autofocus
  - [Bad] 瀏覽器自帶的彈跳視窗無法修改樣式
  - [Improve] 可製作客製化的彈窗，內塞`<input/>`替代，但一樣無法透過 autofocus 叫出`輸入鍵盤`

```js
const text = new Phaser.GameObjects.Text(yourScene, 0, 0, '');
// Used prompt to get inputed value, if the device is mobile
if (isMobile) {
  const result = window.prompt('Input you name', 'Alloy');
  text.setText(result);
} else {
  // Used input element to get the inputed value
}
```

2. 使用`<input/>`

  - [Good] 體驗較好
  - [Bad] 自適應困難
  - [Bad] 輸入的文字樣式及大小可能和顯示的樣式大小有所落差
  - [Bad] 會有`zoom in`的效果，需要特別處理
