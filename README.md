## 概要
剣盾の自動コントロールを[atmega32u4](https://www.amazon.co.jp/gp/product/B073NXQKHT)で行うためのサンプルコードとTipsです.  
躓いた点しか書かないため、細かい詳細は参考リンクなどをご確認ください.  

## AVRdude
マイコンへのインストールはavrdudeで行います.参考ですが以下のコマンドで通りました.  

```avrdude -p atmega32u4 -c avr109 -v -v -v -v -P COMX -U flash:w:Joystick.hex:i -D -b 57600 -F```

ポートのCOMXはArduinoIDEで確認します. 上記リンクのatmega32u4はArduino IDE v1.0.5のサポートですが、最新のIDEで問題ありません.  (もっと簡単な方法あるかも)
ポートはツール->シリアルポートで確認できますが、DFUモードの瞬間じゃないと正しいポートが取得できません.  
DFUモードにするには物理的にリセットボタンを起動させる必要があります.  

リセットを行うには[こちらの図](https://www.14core.com/installing-bootloading-micro-mini-pro-atmega32u4-5v-16mhz/)にあるようにRSTとGNDのピンをショートさせる必要があります.  
ショートさせるには付属のピンを差し、ドライバなどで通電させればOKです.  
ショートさせるとLEDが何かしら反応するので、そのタイミングでIDEのポートを確認してください.  

avrdudeのコマンドを打つ際もDFUモードにしてからでないと失敗するので、同様にショートさせてください.  

## Switchとの接続
インストール済みのマイコンをSwitchのUSBポートに刺しても反応しない場合があります.  
その場合はSwitchの再起動をすれば動き出す場合があります.  

### 参考
[One-Shot-Station](https://github.com/anaakikutushita/One-Shot-Station)  
[timewalk-with-watt](https://github.com/john-ditto/timewalk-with-watt)  
