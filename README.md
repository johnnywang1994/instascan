# instascan
Instascan tool fixing for safari, chrome 
Form: https://github.com/schmich/instascan/issues/182
Page: https://github.com/quocthai95/instascan.git

## Usage

1. Create HTML' video tag for Camera

```html
<video id="preview"></video>
```

2. Create a new Scanner in js

```js
var scanner = new Instascan.Scanner({
  video: document.getElementById('preview');
})
```

3. Change the camera from left to right

```js
scanner.video.style.transform = 'scaleX(-1)'
```

4. Add attribute 'playsinline' for IOS device

```js
scanner.video.setAttribute("playsinline", true)
```

5. Start Listening for Event 'scan'

```js
scanner.addListener('scan', function (content) {
  alert('You are going to: '+content);
  location.href = content;
})
```

6. Initialize & detect Cameras to start

```js
Instascan.Camera.getCameras().then(function (cameras) {
  // cameras => array for cameras detected in now device
  if (cameras.length > 0) {
    scanner.start(cameras[0])
  } else {
    alert("Sorry, No camera was detected in your device!")
  }
}).catch(function (e) {
  console.error(e)
})
```