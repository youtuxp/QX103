# ConfigConverter
[![Netlify Status](https://api.netlify.com/api/v1/badges/b8d38664-9076-461a-aa8e-d419ee365f9c/deploy-status)](https://app.netlify.com/sites/config-converter/deploys)

将各种代理软件的配置文件进行转换

## API Endpoint

使用方式请参考 [部署与说明文档](https://www.markeditor.com/file/get/eb581bd61fad7c345853e2ac1a5482f8?t=1574667122)

- `/api/SurgeProfile2SurgeList` 将 Surge 配置文件转换为 List
- `/api/QuantumultXScriptAddDeviceID` 将 QX 脚本中添加设备 ID
- `/api/QuantumultXScriptSubscriptionAddDeviceID` 自动为 QX 脚本订阅添加设备 ID 行


## 自部署

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/ImSingee/ConfigConverter)

相关更新将在 [Singee 的日常](https://t.me/singee_daily) 中发布

有问题可以通过 [@Bryan](https://t.me/atbryanbot) 联系我



<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en-us">
<head>
    <meta http-equiv="content-type" content="text/html; charset=utf-8" />
    <meta name="renderer" content="webkit">
    <meta content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0" name="viewport"/>
    <meta content="yes" name="apple-mobile-web-app-capable"/>
    <meta content="black" name="apple-mobile-web-app-status-bar-style"/>
    <meta content="telephone=no" name="format-detection"/>
    <meta name="renderer" content="webkit"/>
    <title>ConfigConverter 使用说明</title>
    <link rel="stylesheet" href="data:text/css;base64,CiAgICBoMSwgaDIsIGgzLCBoNSwgaDYsICBpbWcsIHN2ZywgcHJlLCB0YWJsZSwgdHJ7cGFnZS1icmVhay1pbnNpZGU6IGF2b2lkfQoKCiAgICBib2R5IHsKICAgICAgICBiYWNrZ3JvdW5kOiAjRjlGNUU4OwogICAgICAgIGZvbnQtc2l6ZTogMTRweDsKICAgICAgICBsaW5lLWhlaWdodDoyLjM7CiAgICAgICAgZm9udC1mYW1pbHk6ICJIZWx2ZXRpY2EiOwogICAgICAgIGZvbnQtd2VpZ2h0OiBub3JtYWw7CiAgICAgICAgY29sb3I6ICM2NjM3MTg7CiAgICAgICAgcGFkZGluZzogMCAzOHB4OwogICAgICAgIG1heC13aWR0aDogODIwcHg7CiAgICAgICAgbWFyZ2luOiAwIGF1dG87CgogICAgICAgIHdvcmQtd3JhcDpicmVhay13b3JkOwogICAgICAgIHdvcmQtYnJlYWs6IG5vcm1hbDsKICAgICAgICBvdmVyZmxvdy13cmFwOmJyZWFrLXdvcmQ7CgoKICAgICAgICBvdmVyZmxvdy14OiBoaWRkZW47CiAgICAgICAgdGV4dC1yZW5kZXJpbmc6IG9wdGltaXplTGVnaWJpbGl0eTsKICAgICAgICAtd2Via2l0LXRleHQtc2l6ZS1hZGp1c3Q6IG5vbmU7CiAgICB9CgogICAgYnJ7CiAgICAgICAgbGluZS1oZWlnaHQ6IDIuMzsKICAgIH0KCgoKICAgIEBtZWRpYSAobWF4LXdpZHRoOiA2MDBweCkgewogICAgICAgIGJvZHl7CiAgICAgICAgICAgIHBhZGRpbmc6IDAgMzBweDsKICAgICAgICB9CiAgICB9CgogICAgQG1lZGlhIChtYXgtd2lkdGg6IDQ4MHB4KSB7CiAgICAgICAgYm9keXsKICAgICAgICAgICAgcGFkZGluZzogMCAyMHB4OwogICAgICAgIH0KICAgIH0KCiAgICAuZ2lzdHsKICAgICAgICB3b3JkLWJyZWFrOiBub3JtYWw7CiAgICB9CgogICAgLnBvc3R7CiAgICAgICAgbWFyZ2luLXRvcDogMTBweDsKICAgICAgICBtYXJnaW4tYm90dG9tOiA1MHB4OwogICAgICAgIHBvc2l0aW9uOiByZWxhdGl2ZTsKICAgIH0KCgoKICAgIGltZ3sKICAgICAgICBtYXgtd2lkdGg6IDk4JTsKICAgICAgICBtYXJnaW46IDAuOGVtIGF1dG8gMC44ZW0gYXV0bzsKICAgIH0KCiAgICBoMSBpbWcsIGgyIGltZywgaDMgaW1nLCBoNCBpbWcsIGg1IGltZywgaDYgaW1newogICAgICAgIG1hcmdpbjogYXV0bzsKICAgIH0KCiAgICAueDJfaW1hZ2V7CiAgICAgICAgem9vbTogNTAlOwogICAgfQoKICAgIC54M19pbWFnZXsKICAgICAgICB6b29tOiAzMy4zMyU7CiAgICB9CgogICAgLng0X2ltYWdlewogICAgICAgIHpvb206IDI1JTsKICAgIH0KCgogICAgcCBpbWd7CiAgICAgICAgbWFyZ2luOiAwIGF1dG87CiAgICB9CgogICAgcHsKICAgICAgICAvKm92ZXJmbG93OmhpZGRlbjsqLwogICAgICAgIG1hcmdpbjogMS4wZW0gMCAxLjhlbSAwOwogICAgfQoKICAgIHAubWRfYmxvY2tfYXNfb3BlbmluZ3sKICAgICAgICBtYXJnaW4tYm90dG9tOiAtMC41ZW0gIWltcG9ydGFudDsKICAgIH0KCiAgICBsaSBwewogICAgICAgIGxpbmUtaGVpZ2h0OiAyLjA3OwogICAgICAgIG1hcmdpbjogMDsKICAgIH0KCiAgICAucF9wYXJ0IHsKICAgICAgICBtYXJnaW46IDEwcHggMDsKICAgIH0KCiAgICAucF9wYXJ0IHB7CiAgICAgICAgbWFyZ2luOiAwIDAgMC42ZW0gMDsKICAgIH0KCiAgICAvKiB0ZXh0IGluZGVudCBmb3IgY2hpbmVzZSBzdGFydHMqLwogICAgLypoMiwgaDMsIGg0LCBoNSwgaDYsIC5wX3BhcnQgcCwgLnRvZG9faXRlbSwgcHsKICAgICAgICB0ZXh0LWluZGVudDogMHB4OwogICAgfSovCiAgICB0YWJsZSwgcHJlLCBzdmcsIC5jb2RlaGlsaXRldGFibGV7CiAgICAgICAgbWFyZ2luLWxlZnQ6IDBweDsKICAgICAgICBtYXJnaW4tcmlnaHQ6IDBweDsKICAgIH0KCiAgICAuY29kZWhpbGl0ZXRhYmxlIHByZXsKICAgICAgICBtYXJnaW4tbGVmdDogMDsKICAgICAgICBtYXJnaW4tcmlnaHQ6IDA7CgogICAgfQoKICAgIC5jb2RlaGlsaXRldGFibGUgLmNvZGVoaWxpdGUgcHJlewogICAgICAgIGJvcmRlci1sZWZ0OiBub25lOwogICAgfQoKICAgIC8qIHRleHQgaW5kZW50IGZvciBjaGluZXNlIGVuZHMqLwoKCiAgICBibG9ja3F1b3RlIC5wX3BhcnQgcCwgbGkgLnBfcGFydCBwewogICAgICAgIHRleHQtaW5kZW50OiAwICFpbXBvcnRhbnQ7CiAgICB9CgoKICAgIGhyewogICAgICAgIG1hcmdpbjogMzhweCAwOwogICAgICAgIGJvcmRlcjogbm9uZTsKICAgICAgICBib3JkZXItYm90dG9tOiAxcHggZGFzaGVkIHJnYmEoMjA1LCAyMDUsIDIwNSwgMC4zNSk7CiAgICAgICAgY29sb3I6IHJnYmEoMjA1LCAyMDUsIDIwNSwgMC4zNSk7CiAgICAgICAgaGVpZ2h0OiAxcHg7CiAgICAgICAgbGluZS1oZWlnaHQ6MXB4OwogICAgICAgIGZvbnQtc2l6ZToxcHg7CiAgICAgICAgb3ZlcmZsb3cteTogaGlkZGVuOwogICAgfQoKCiAgICBoMXsKICAgICAgICBjb2xvcjogIzAwNzlEMjsKICAgICAgICBmb250LXNpemU6IDEuN2VtOwogICAgICAgIHRleHQtYWxpZ246IGxlZnQ7CiAgICAgICAgbWFyZ2luOiAwOwogICAgICAgIHBhZGRpbmc6IDA7CiAgICAgICAgbGluZS1oZWlnaHQ6IDEuN2VtOwogICAgICAgIG1hcmdpbi10b3A6IDAuOGVtOwogICAgICAgIG1hcmdpbi1ib3R0b206IDAuNmVtOwogICAgfQoKICAgIGgxLCBoMiwgaDMsIGg0ewogICAgICAgIGNvbG9yOiAjMDA3OUQyOwogICAgfQogICAgCiAgICBoMXtjb2xvcjojMDA3OUQyfQoKCgogICAgaDIsIGgzewogICAgICAgIGxpbmUtaGVpZ2h0OiAxLjVlbTsKICAgICAgICBtYXJnaW4tdG9wOiAxLjhlbTsKICAgICAgICBtYXJnaW4tYm90dG9tOiAwLjVlbTsKICAgIH0KCiAgICAuaDE2Lm1kX2ZpcnN0X2gubWRfZmlyc3RfcGFydCB7CiAgICAgICAgbWFyZ2luLXRvcDogNXB4OwogICAgfQoKICAgIGgyIHsKICAgICAgICBmb250LXNpemU6IDEuNWVtOwogICAgfQoKICAgIGgzIHsKICAgICAgICBmb250LXNpemU6IDEuMjVlbQogICAgfQoKICAgIGg0IHsKICAgICAgICBmb250LXNpemU6IDEuMTVlbTsKICAgIH0KCiAgICBoNSB7CiAgICAgICAgZm9udC1zaXplOiAxLjFlbTsKICAgIH0KCiAgICBoNiB7Zm9udC1zaXplOiAxZW19CgoKICAgIGgxLCBoMiwgaDMsIGg0LCBoNSwgaDZ7CiAgICAgICAgZm9udC1mYW1pbHk6ICJIZWl0aSBTQyI7CiAgICB9CgoKICAgIG9sIHsKICAgICAgICBtYXJnaW46IDA7CiAgICB9CgogICAgdWx7CiAgICAgICAgcGFkZGluZzogNXB4IDM4cHg7CiAgICAgICAgbWFyZ2luOiAwOwogICAgfQoKICAgIHVsIGxpLCBsaXsKICAgICAgICBwYWRkaW5nOiAwOwogICAgICAgIG1hcmdpbjogMDsKICAgIH0KCiAgICB1bCBwLCBvbCBwewogICAgICAgIG92ZXJmbG93OiB2aXNpYmxlOwogICAgfQoKCiAgICBibG9ja3F1b3RlIHsKICAgICAgICAtbW96LWJveC1zaXppbmc6IGJvcmRlci1ib3g7CiAgICAgICAgYm94LXNpemluZzogYm9yZGVyLWJveDsKICAgICAgICBtYXJnaW46IDEuNmVtIDA7CiAgICAgICAgcGFkZGluZzogMCAwIDAgMS4yZW07CiAgICAgICAgYm9yZGVyLWxlZnQ6IDAuNGVtIHNvbGlkICMxNkIwRkY7CiAgICAgICAgY29sb3I6ICM4ODg4ODg7CiAgICAgICAgbWluLWhlaWdodDoyMHB4OwogICAgfQoKCiAgICBibG9ja3F1b3RlIHAgewogICAgICAgIG1hcmdpbjogMC44ZW0gMDsKICAgIH0KCiAgICBibG9ja3F1b3RlIHNwYW4ubWRfbGluZSB7CiAgICAgICAgbWFyZ2luLWJvdHRvbTogMC4yNWVtOwogICAgICAgIG1hcmdpbi10b3A6IDAuMjVlbTsKICAgIH0KCiAgICBibG9ja3F1b3RlIHVsewogICAgICAgIHBhZGRpbmc6IDAgMTVweDsKICAgIH0KCiAgICBibG9ja3F1b3RlIHNtYWxsIHsKICAgICAgICBkaXNwbGF5OiBpbmxpbmUtYmxvY2s7CiAgICAgICAgbWFyZ2luOiAwLjhlbSAwIDAuOGVtIDEuNWVtOwogICAgICAgIGZvbnQtc2l6ZTogMC45ZW07CiAgICAgICAgY29sb3I6ICNjY2M7CiAgICB9CgoKCgoKCiAgICB0YWJsZSB7CiAgICAgICAgbGluZS1oZWlnaHQ6IDEuNzsKICAgICAgICAtbW96LWJveC1zaXppbmc6IGJvcmRlci1ib3g7CiAgICAgICAgYm94LXNpemluZzogYm9yZGVyLWJveDsKICAgICAgICBtYXJnaW46IDFlbSAwOwogICAgICAgIHdpZHRoOiAxMDAlOwogICAgICAgIG1heC13aWR0aDogMTAwJTsKICAgICAgICBib3JkZXItd2lkdGg6IDFweDsKICAgICAgICBib3JkZXItc3R5bGU6IHNvbGlkOwogICAgICAgIGJhY2tncm91bmQtY29sb3I6IHRyYW5zcGFyZW50OwogICAgICAgIGJvcmRlci1zcGFjaW5nOiAwOwogICAgICAgIHdvcmQtYnJlYWs6IG5vcm1hbDsKICAgIH0KICAgIAogICAgLyogZm9yIHdlY2hhdCBvbmx5IHN0YXJ0cyAqLwogICAgdGFibGUgdHJ7CiAgICAgICAgYm9yZGVyLXJpZ2h0LXN0eWxlOiBzb2xpZDsKICAgICAgICBib3JkZXItcmlnaHQtd2lkdGg6IDFweDsKICAgIH0KICAgIAogICAgdGFibGUgdGJvZHl7CiAgICAgICAgYm9yZGVyLWJvdHRvbS13aWR0aDogMXB4OwogICAgICAgIGJvcmRlci1ib3R0b20tc3R5bGU6IHNvbGlkOwogICAgfQogICAgLyogZm9yIHdlY2hhdCBvbmx5IGVuZHMgKi8KCgogICAgdGFibGUsIHRhYmxlIHRyLCB0YWJsZSB0ciB0ZCwgdGFibGUgdHIgdGgsIHRhYmxlIHRib2R5IHsKICAgICAgICBib3JkZXItY29sb3I6IHJnYmEoMjA1LCAyMDUsIDIwNSwgMC4zNSk7CiAgICB9CgogICAgdGFibGUgdGggewogICAgICAgIGZvbnQtd2VpZ2h0OiBib2xkOwogICAgfQoKICAgIHRyIHRoIHsKICAgICAgICBib3JkZXItYm90dG9tLXdpZHRoOiAxcHg7CiAgICAgICAgYm9yZGVyLWJvdHRvbS1zdHlsZTogc29saWQ7CiAgICAgICAgdGV4dC1hbGlnbjogbGVmdDsKICAgIH0KCiAgICB0ciB0aCwgdHIgdGQgewogICAgICAgIHBhZGRpbmc6IDEwcHggMjBweDsKICAgICAgICBib3JkZXItcmlnaHQ6IDFweCBzb2xpZDsKICAgICAgICBib3JkZXItYm90dG9tOiAxcHggc29saWQgcmdiYSgyMDUsIDIwNSwgMjA1LCAwLjM1KTsKICAgIH0KCiAgICB0Ym9keSB0cjpsYXN0LWNoaWxkIHRkewogICAgICAgIGJvcmRlci1ib3R0b206IDA7CiAgICB9CgogICAgdHIgdGg6bGFzdC1jaGlsZCwgdHIgdGQ6bGFzdC1jaGlsZCB7CiAgICAgICAgYm9yZGVyLXJpZ2h0OiAwOwogICAgfQoKICAgIHRhYmxlIHRib2R5ID4gdHI6bnRoLWNoaWxkKG9kZCkgPiB0ZCwgdGFibGUgdGJvZHkgPiB0cjpudGgtY2hpbGQob2RkKSA+IHRoIHsKICAgICAgICBiYWNrZ3JvdW5kLWNvbG9yOiByZ2JhKDIzNSwgMjM1LCAyMzUsIDAuMik7CiAgICB9CgoKCgogICAgY29kZXsKICAgICAgICBiYWNrZ3JvdW5kOiByZ2JhKDIzNSwgMjM1LCAyMzUsIDAuMzUpOwogICAgICAgIGNvbG9yOiAjNDhCNDU2OwogICAgICAgIHBhZGRpbmc6IDAgNXB4OwogICAgICAgIG1hcmdpbjogMCAycHg7CiAgICB9CgogICAgcHJlewogICAgICAgIG1hcmdpbi10b3A6IDEuMmVtOwogICAgICAgIG1hcmdpbi1ib3R0b206IDEuMmVtOwogICAgICAgIHBhZGRpbmc6IDE1cHggMTBweDsKICAgICAgICBkaXNwbGF5OiBibG9jazsKICAgICAgICAvKiBvdmVyZmxvdzogYXV0bzsgKi8KICAgICAgICBib3JkZXI6IDFweCBzb2xpZCByZ2JhKDIwNSwgMjA1LCAyMDUsIDAuMzUpOwogICAgICAgIC8qYmFja2dyb3VuZDogcmdiYSgyMzUsIDIzNSwgMjM1LCAwLjM1KTsqLwogICAgICAgIGZvbnQtc2l6ZTogOTAlOwogICAgICAgIGxpbmUtaGVpZ2h0OjIuMzsKICAgICAgICB3aGl0ZS1zcGFjZTogcHJlLXdyYXA7CiAgICB9CgogICAgLmhpZ2hsaWdodHRhYmxlIHRkewogICAgICAgIC8qYmFja2dyb3VuZC1jb2xvcjogcmdiYSgyMzUsIDIzNSwgMjM1LCAwLjM1KSAhaW1wb3J0YW50OyovCiAgICB9CgogICAgLndpdGhfbGluZXMgcHJlewogICAgICAgIGJvcmRlcjpub25lOwogICAgICAgIG1hcmdpbi10b3A6IDAuMmVtOwogICAgICAgIG1hcmdpbi1ib3R0b206IDAuMmVtOwogICAgICAgIGJhY2tncm91bmQ6IHRyYW5zcGFyZW50OwogICAgfQoKICAgIC5pc19jb2RlX2ZpbGUgcHJlewogICAgICAgIGJvcmRlcjogbm9uZTsKICAgICAgICBiYWNrZ3JvdW5kOiB0cmFuc3BhcmVudDsKICAgIH0KCiAgICAuY29kZWhpbGl0ZSBwcmV7CiAgICAgICAgLyp3b3JkLXdyYXA6IG5vcm1hbDsqLwogICAgICAgIGZvbnQtc2l6ZTogMTNweDsKICAgIH0KCiAgICBwcmUgY29kZXsKICAgICAgICBib3JkZXI6bm9uZTsKICAgICAgICBiYWNrZ3JvdW5kOiBub25lOwogICAgICAgIHBhZGRpbmc6IDA7CiAgICAgICAgbWFyZ2luOiAwOwogICAgfQoKICAgIHByZSBwewogICAgICAgIG1hcmdpbjogMDsKICAgICAgICBwYWRkaW5nOiAwOwogICAgfQoKICAgIC5jb2RlaGlsaXRlIHRoLCAuY29kZWhpbGl0ZSB0ZHsKICAgICAgICBsaW5lLWhlaWdodDogMS44ZW07CiAgICB9CgoKICAgIGF7CiAgICAgICAgY29sb3I6ICM0MDgzQzQ7CiAgICAgICAgdGV4dC1kZWNvcmF0aW9uOiBub25lOwogICAgICAgIC8vYm9yZGVyLWJvdHRvbTogMXB4IHNvbGlkIHRyYW5zcGFyZW50OwogICAgfQoKICAgIGE6aG92ZXJ7CiAgICAgICAgdGV4dC1kZWNvcmF0aW9uOiB1bmRlcmxpbmU7CiAgICAgICAgLy9ib3JkZXItYm90dG9tOiAxcHggc29saWQgIzQwODNDNDsKICAgIH0KCiAgICBzdHJvbmcgewogICAgICAgIGNvbG9yOiAjMDAwMDAwOwogICAgICAgIGZvbnQtd2VpZ2h0OiBib2xkOwogICAgfQoKCiAgICAvKiBmb3IgbWFya2Rvd24gKi8KCiAgICAubGluZW5vcyBwcmV7CgkJYmFja2dyb3VuZDogdHJhbnNwYXJlbnQ7CgkJYm9yZGVyOiBub25lOwoJfQoKCS5saW5lbm9zewoJICAgIHBhZGRpbmc6IDAgNXB4IDAgNXB4OwoJICAgIHdpZHRoOiAwLjAwMSU7Cgl9CgoJLmhpZ2hsaWdodHRhYmxlIHByZXsKCSAgICBwYWRkaW5nOiA1cHggMTBweDsKCX0KCiAgICAudG9jewogICAgICAgIGJhY2tncm91bmQ6IE5vbmU7CiAgICAgICAgYm9yZGVyLXJhZGl1czogNXB4OwogICAgICAgIGJvcmRlcjogMXB4IHNvbGlkIE5vbmU7CiAgICAgICAgbWFyZ2luOiAyN3B4IDAgNDdweCAwOwogICAgICAgIHBhZGRpbmc6IDEwcHggMDsKICAgIH0KCiAgICAudG9jIHVsewogICAgICAgIC8vcGFkZGluZzogNXB4IDQycHg7CiAgICB9CgogICAgLnRvYyB1bCBsaXsKICAgICAgICBwYWRkaW5nOiAwOwogICAgICAgIG1hcmdpbjogMDsKICAgIH0KICAgIC50b2MgYXsKICAgICAgICBjb2xvcjogIzY2MzcxODsKICAgIH0KCgoKICAgIC50b2RvX2l0ZW17CiAgICAgICAgbGlzdC1zdHlsZTogbm9uZTsKICAgICAgICBtYXJnaW4tbGVmdDogLTEuNWVtCiAgICB9CiAgICAudG9kb19pdGVtIC50b2RvX2l0ZW0gewogICAgICAgIG1hcmdpbi1sZWZ0OiBhdXRvOwogICAgfQoKICAgIC50b2RvX2RvbmVfaXRlbXsKICAgICAgICBjb2xvcjogIzk5OTk5OTsKICAgIH0KCiAgICAudG9kb191bmRvbmVfaXRlbXsKICAgICAgICBjb2xvcjogI0M4NUE1NzsKICAgIH0KCgogICAgdWwgbGkudG9kb19pdGVtewoJbGlzdC1zdHlsZS10eXBlOiBub25lOwogICAgfQoKICAgIHVsIGxpLnRvZG9faXRlbTpiZWZvcmV7CiAgICAgICAgY29udGVudDogJ+KYkCc7CiAgICAgICAgLypwYWRkaW5nLXJpZ2h0OiAwLjJlbTsqLwogICAgICAgIGZvbnQtZmFtaWx5OiBhcmlhbDsKICAgIH0KCiAgICB1bCBsaS50b2RvX2RvbmVfaXRlbTpiZWZvcmV7CiAgICAgICAgY29udGVudDogJ+KYkSc7CiAgICAgICAgLypwYWRkaW5nLXJpZ2h0OiAwLjJlbTsqLwogICAgICAgIGZvbnQtZmFtaWx5OiBhcmlhbDsKICAgIH0KCiAgICB1bCBsaS50b2RvX2l0ZW0gaW5wdXR7CiAgICAgICAgZGlzcGxheTpub25lCiAgICB9CgoKICAgIC8qcHlnbWVudHMqLwoKICAgIC5jb2RlaGlsaXRlewogICAgICAgIGJhY2tncm91bmQ6IHRyYW5zcGFyZW50ICFpbXBvcnRhbnQ7CiAgICB9CgogICAgdGFibGUuY29kZWhpbGl0ZXRhYmxleyBib3JkZXI6bm9uZTsgfQoKCiAgICAuY29kZWhpbGl0ZXRhYmxlIHRkeyBib3JkZXI6IG5vbmU7IHBhZGRpbmc6IDA7fQoKICAgIC5mbG93LWdyYXBoaWMsIC5tZF9ibG9ja19zZWN0aW9uX2Zvcl9mbG93X2dyYXBoaWN7dGV4dC1hbGlnbjogY2VudGVyfQogICAgLmZsb3ctZ3JhcGhpYyB7IG92ZXJmbG93LXg6IGF1dG87fQogICAgLm1lcm1haWQsIC5tZF9ibG9ja19zZWN0aW9uX2Zvcl9tZXJtYWlke3RleHQtYWxpZ246IGNlbnRlcn0KICAgIAogICAgLmZsb3ctZ3JhcGhpYywgLm1lcm1haWR7CiAgICAgICAgYmFja2dyb3VuZDogI2ZmZmZmZjsKICAgIH0KCgogICAgdGFibGUsIHRyLCB0ZCwgdGgsIHRib2R5LCB0aGVhZCwgdGZvb3QsIC5tZF9lY2hhcnRzLCBibG9ja3F1b3RlIC5tZF9saW5lewogICAgICAgIHBhZ2UtYnJlYWstaW5zaWRlOiBhdm9pZCAhaW1wb3J0YW50OwogICAgfQoKICAgIC5mb290bm90ZXMgLm1kX2xpbmV7CiAgICAgICAgZGlzcGxheTogaW5saW5lICFpbXBvcnRhbnQ7CiAgICB9CgoKICAgIC5pbWdfcnRfOTB7CiAgICAgICAgdHJhbnNmb3JtOnJvdGF0ZSg5MGRlZyk7CiAgICAgICAgLW1zLXRyYW5zZm9ybTpyb3RhdGUoOTBkZWcpOwogICAgICAgIC1tb3otdHJhbnNmb3JtOnJvdGF0ZSg5MGRlZyk7CiAgICAgICAgLXdlYmtpdC10cmFuc2Zvcm06cm90YXRlKDkwZGVnKTsKICAgICAgICAtby10cmFuc2Zvcm06cm90YXRlKDkwZGVnKTsKICAgIH0KICAgIC5pbWdfcnRfMTgwewogICAgICAgIHRyYW5zZm9ybTpyb3RhdGUoMTgwZGVnKTsKICAgICAgICAtbXMtdHJhbnNmb3JtOnJvdGF0ZSgxODBkZWcpOwogICAgICAgIC1tb3otdHJhbnNmb3JtOnJvdGF0ZSgxODBkZWcpOwogICAgICAgIC13ZWJraXQtdHJhbnNmb3JtOnJvdGF0ZSgxODBkZWcpOwogICAgICAgIC1vLXRyYW5zZm9ybTpyb3RhdGUoMTgwZGVnKTsKICAgIH0KICAgIC5pbWdfcnRfMjcwewogICAgICAgIHRyYW5zZm9ybTpyb3RhdGUoMjcwZGVnKTsKICAgICAgICAtbXMtdHJhbnNmb3JtOnJvdGF0ZSgyNzBkZWcpOwogICAgICAgIC1tb3otdHJhbnNmb3JtOnJvdGF0ZSgyNzBkZWcpOwogICAgICAgIC13ZWJraXQtdHJhbnNmb3JtOnJvdGF0ZSgyNzBkZWcpOwogICAgICAgIC1vLXRyYW5zZm9ybTpyb3RhdGUoMjcwZGVnKTsKICAgIH0KCiAgICAubWRfaGFzX2Jsb2NrX2JlbG93ewogICAgICAgIG1hcmdpbi1ib3R0b206IDAuMWVtICFpbXBvcnRhbnQ7CiAgICB9CiAgICAubWRfaGFzX2Jsb2NrX2JlbG93X2ltZ3sKICAgICAgICBtYXJnaW4tYm90dG9tOiAtMC42ZW0gIWltcG9ydGFudDsKICAgIH0KCgogICAgLmNvZGVoaWxpdGUgLmVycnsKICAgICAgICBib3JkZXI6IG5vbmUgIWltcG9ydGFudDsKICAgICAgICBiYWNrZ3JvdW5kLWNvbG9yOiB0cmFuc3BhcmVudCAhaW1wb3J0YW50OwogICAgfQoKCgogICAgICAgIHNwYW4ubWRfbGluZXttYXJnaW4tYm90dG9tOjAuNWVtOyBkaXNwbGF5OmJsb2NrOyBsaW5lLWhlaWdodDoxLjk4OTV9CiAgICAgICAgLm1kX2xpbmUgYnJ7IGRpc3BsYXk6IG5vbmU7fQogICAgICAgIC5jb2RlaGlsaXRlIC5obGwgeyBiYWNrZ3JvdW5kLWNvbG9yOiAgfQouY29kZWhpbGl0ZSAgeyBiYWNrZ3JvdW5kOiAjZWVlZWRkOyBjb2xvcjogIzU1NTU1NSB9Ci5jb2RlaGlsaXRlIC5jIHsgY29sb3I6ICM5OTk5OTkgfSAvKiBDb21tZW50ICovCi5jb2RlaGlsaXRlIC5lcnIgeyBjb2xvcjogI2E2MTcxNzsgYmFja2dyb3VuZC1jb2xvcjogI2UzZDJkMiB9IC8qIEVycm9yICovCi5jb2RlaGlsaXRlIC5rIHsgY29sb3I6ICM4QjAwOEI7IGZvbnQtd2VpZ2h0OiBib2xkIH0gLyogS2V5d29yZCAqLwouY29kZWhpbGl0ZSAubCB7IGNvbG9yOiAjYWU4MWZmIH0gLyogTGl0ZXJhbCAqLwouY29kZWhpbGl0ZSAubiB7IGNvbG9yOiAjNTU1NTU1IH0gLyogTmFtZSAqLwouY29kZWhpbGl0ZSAubyB7IGNvbG9yOiAjNTU1NTU1IH0gLyogT3BlcmF0b3IgKi8KLmNvZGVoaWxpdGUgLnAgeyBjb2xvcjogIzU1NTU1NSB9IC8qIFB1bmN0dWF0aW9uICovCi5jb2RlaGlsaXRlIC5jaCB7IGNvbG9yOiAjOTk5OTk5IH0gLyogQ29tbWVudC5IYXNoYmFuZyAqLwouY29kZWhpbGl0ZSAuY20geyBjb2xvcjogIzk5OTk5OSB9IC8qIENvbW1lbnQuTXVsdGlsaW5lICovCi5jb2RlaGlsaXRlIC5jcCB7IGNvbG9yOiAjMWU4ODliIH0gLyogQ29tbWVudC5QcmVwcm9jICovCi5jb2RlaGlsaXRlIC5jcGYgeyBjb2xvcjogIzk5OTk5OSB9IC8qIENvbW1lbnQuUHJlcHJvY0ZpbGUgKi8KLmNvZGVoaWxpdGUgLmMxIHsgY29sb3I6ICM5OTk5OTkgfSAvKiBDb21tZW50LlNpbmdsZSAqLwouY29kZWhpbGl0ZSAuY3MgeyBjb2xvcjogIzhCMDA4QjsgZm9udC13ZWlnaHQ6IGJvbGQgfSAvKiBDb21tZW50LlNwZWNpYWwgKi8KLmNvZGVoaWxpdGUgLmdkIHsgY29sb3I6ICNhYTAwMDAgfSAvKiBHZW5lcmljLkRlbGV0ZWQgKi8KLmNvZGVoaWxpdGUgLmdlIHsgZm9udC1zdHlsZTogaXRhbGljIH0gLyogR2VuZXJpYy5FbXBoICovCi5jb2RlaGlsaXRlIC5nciB7IGNvbG9yOiAjYWEwMDAwIH0gLyogR2VuZXJpYy5FcnJvciAqLwouY29kZWhpbGl0ZSAuZ2ggeyBjb2xvcjogIzAwMDA4MDsgZm9udC13ZWlnaHQ6IGJvbGQgfSAvKiBHZW5lcmljLkhlYWRpbmcgKi8KLmNvZGVoaWxpdGUgLmdpIHsgY29sb3I6ICMwMGFhMDAgfSAvKiBHZW5lcmljLkluc2VydGVkICovCi5jb2RlaGlsaXRlIC5nbyB7IGNvbG9yOiAjODg4ODg4IH0gLyogR2VuZXJpYy5PdXRwdXQgKi8KLmNvZGVoaWxpdGUgLmdwIHsgY29sb3I6ICM1NTU1NTUgfSAvKiBHZW5lcmljLlByb21wdCAqLwouY29kZWhpbGl0ZSAuZ3MgeyBmb250LXdlaWdodDogYm9sZCB9IC8qIEdlbmVyaWMuU3Ryb25nICovCi5jb2RlaGlsaXRlIC5ndSB7IGNvbG9yOiAjODAwMDgwOyBmb250LXdlaWdodDogYm9sZCB9IC8qIEdlbmVyaWMuU3ViaGVhZGluZyAqLwouY29kZWhpbGl0ZSAuZ3QgeyBjb2xvcjogI2FhMDAwMCB9IC8qIEdlbmVyaWMuVHJhY2ViYWNrICovCi5jb2RlaGlsaXRlIC5rYyB7IGNvbG9yOiAjOEIwMDhCOyBmb250LXdlaWdodDogYm9sZCB9IC8qIEtleXdvcmQuQ29uc3RhbnQgKi8KLmNvZGVoaWxpdGUgLmtkIHsgY29sb3I6ICM4QjAwOEI7IGZvbnQtd2VpZ2h0OiBib2xkIH0gLyogS2V5d29yZC5EZWNsYXJhdGlvbiAqLwouY29kZWhpbGl0ZSAua24geyBjb2xvcjogIzhCMDA4QjsgZm9udC13ZWlnaHQ6IGJvbGQgfSAvKiBLZXl3b3JkLk5hbWVzcGFjZSAqLwouY29kZWhpbGl0ZSAua3AgeyBjb2xvcjogIzhCMDA4QjsgZm9udC13ZWlnaHQ6IGJvbGQgfSAvKiBLZXl3b3JkLlBzZXVkbyAqLwouY29kZWhpbGl0ZSAua3IgeyBjb2xvcjogIzhCMDA4QjsgZm9udC13ZWlnaHQ6IGJvbGQgfSAvKiBLZXl3b3JkLlJlc2VydmVkICovCi5jb2RlaGlsaXRlIC5rdCB7IGNvbG9yOiAjYTdhN2E3OyBmb250LXdlaWdodDogYm9sZCB9IC8qIEtleXdvcmQuVHlwZSAqLwouY29kZWhpbGl0ZSAubGQgeyBjb2xvcjogI2U2ZGI3NCB9IC8qIExpdGVyYWwuRGF0ZSAqLwouY29kZWhpbGl0ZSAubSB7IGNvbG9yOiAjQjQ1MkNEIH0gLyogTGl0ZXJhbC5OdW1iZXIgKi8KLmNvZGVoaWxpdGUgLnMgeyBjb2xvcjogI0NENTU1NSB9IC8qIExpdGVyYWwuU3RyaW5nICovCi5jb2RlaGlsaXRlIC5uYSB7IGNvbG9yOiAjNjU4YjAwIH0gLyogTmFtZS5BdHRyaWJ1dGUgKi8KLmNvZGVoaWxpdGUgLm5iIHsgY29sb3I6ICM2NThiMDAgfSAvKiBOYW1lLkJ1aWx0aW4gKi8KLmNvZGVoaWxpdGUgLm5jIHsgY29sb3I6ICMwMDhiNDU7IGZvbnQtd2VpZ2h0OiBib2xkIH0gLyogTmFtZS5DbGFzcyAqLwouY29kZWhpbGl0ZSAubm8geyBjb2xvcjogIzAwNjg4QiB9IC8qIE5hbWUuQ29uc3RhbnQgKi8KLmNvZGVoaWxpdGUgLm5kIHsgY29sb3I6ICM3MDdhN2MgfSAvKiBOYW1lLkRlY29yYXRvciAqLwouY29kZWhpbGl0ZSAubmkgeyBjb2xvcjogIzU1NTU1NSB9IC8qIE5hbWUuRW50aXR5ICovCi5jb2RlaGlsaXRlIC5uZSB7IGNvbG9yOiAjMDA4YjQ1OyBmb250LXdlaWdodDogYm9sZCB9IC8qIE5hbWUuRXhjZXB0aW9uICovCi5jb2RlaGlsaXRlIC5uZiB7IGNvbG9yOiAjMDA4YjQ1IH0gLyogTmFtZS5GdW5jdGlvbiAqLwouY29kZWhpbGl0ZSAubmwgeyBjb2xvcjogIzU1NTU1NSB9IC8qIE5hbWUuTGFiZWwgKi8KLmNvZGVoaWxpdGUgLm5uIHsgY29sb3I6ICMwMDhiNDU7IHRleHQtZGVjb3JhdGlvbjogdW5kZXJsaW5lIH0gLyogTmFtZS5OYW1lc3BhY2UgKi8KLmNvZGVoaWxpdGUgLm54IHsgY29sb3I6ICM1NTU1NTUgfSAvKiBOYW1lLk90aGVyICovCi5jb2RlaGlsaXRlIC5weSB7IGNvbG9yOiAjNTU1NTU1IH0gLyogTmFtZS5Qcm9wZXJ0eSAqLwouY29kZWhpbGl0ZSAubnQgeyBjb2xvcjogIzhCMDA4QjsgZm9udC13ZWlnaHQ6IGJvbGQgfSAvKiBOYW1lLlRhZyAqLwouY29kZWhpbGl0ZSAubnYgeyBjb2xvcjogIzAwNjg4QiB9IC8qIE5hbWUuVmFyaWFibGUgKi8KLmNvZGVoaWxpdGUgLm93IHsgY29sb3I6ICM4QjAwOEIgfSAvKiBPcGVyYXRvci5Xb3JkICovCi5jb2RlaGlsaXRlIC53IHsgY29sb3I6ICNiYmJiYmIgfSAvKiBUZXh0LldoaXRlc3BhY2UgKi8KLmNvZGVoaWxpdGUgLm1iIHsgY29sb3I6ICNCNDUyQ0QgfSAvKiBMaXRlcmFsLk51bWJlci5CaW4gKi8KLmNvZGVoaWxpdGUgLm1mIHsgY29sb3I6ICNCNDUyQ0QgfSAvKiBMaXRlcmFsLk51bWJlci5GbG9hdCAqLwouY29kZWhpbGl0ZSAubWggeyBjb2xvcjogI0I0NTJDRCB9IC8qIExpdGVyYWwuTnVtYmVyLkhleCAqLwouY29kZWhpbGl0ZSAubWkgeyBjb2xvcjogI0I0NTJDRCB9IC8qIExpdGVyYWwuTnVtYmVyLkludGVnZXIgKi8KLmNvZGVoaWxpdGUgLm1vIHsgY29sb3I6ICNCNDUyQ0QgfSAvKiBMaXRlcmFsLk51bWJlci5PY3QgKi8KLmNvZGVoaWxpdGUgLnNhIHsgY29sb3I6ICNDRDU1NTUgfSAvKiBMaXRlcmFsLlN0cmluZy5BZmZpeCAqLwouY29kZWhpbGl0ZSAuc2IgeyBjb2xvcjogI0NENTU1NSB9IC8qIExpdGVyYWwuU3RyaW5nLkJhY2t0aWNrICovCi5jb2RlaGlsaXRlIC5zYyB7IGNvbG9yOiAjQ0Q1NTU1IH0gLyogTGl0ZXJhbC5TdHJpbmcuQ2hhciAqLwouY29kZWhpbGl0ZSAuZGwgeyBjb2xvcjogI0NENTU1NSB9IC8qIExpdGVyYWwuU3RyaW5nLkRlbGltaXRlciAqLwouY29kZWhpbGl0ZSAuc2QgeyBjb2xvcjogI0NENTU1NSB9IC8qIExpdGVyYWwuU3RyaW5nLkRvYyAqLwouY29kZWhpbGl0ZSAuczIgeyBjb2xvcjogI0NENTU1NSB9IC8qIExpdGVyYWwuU3RyaW5nLkRvdWJsZSAqLwouY29kZWhpbGl0ZSAuc2UgeyBjb2xvcjogI2FlODFmZiB9IC8qIExpdGVyYWwuU3RyaW5nLkVzY2FwZSAqLwouY29kZWhpbGl0ZSAuc2ggeyBjb2xvcjogIzFjN2U3MTsgZm9udC1zdHlsZTogaXRhbGljIH0gLyogTGl0ZXJhbC5TdHJpbmcuSGVyZWRvYyAqLwouY29kZWhpbGl0ZSAuc2kgeyBjb2xvcjogI0NENTU1NSB9IC8qIExpdGVyYWwuU3RyaW5nLkludGVycG9sICovCi5jb2RlaGlsaXRlIC5zeCB7IGNvbG9yOiAjY2I2YzIwIH0gLyogTGl0ZXJhbC5TdHJpbmcuT3RoZXIgKi8KLmNvZGVoaWxpdGUgLnNyIHsgY29sb3I6ICMxYzdlNzEgfSAvKiBMaXRlcmFsLlN0cmluZy5SZWdleCAqLwouY29kZWhpbGl0ZSAuczEgeyBjb2xvcjogI0NENTU1NSB9IC8qIExpdGVyYWwuU3RyaW5nLlNpbmdsZSAqLwouY29kZWhpbGl0ZSAuc3MgeyBjb2xvcjogI0NENTU1NSB9IC8qIExpdGVyYWwuU3RyaW5nLlN5bWJvbCAqLwouY29kZWhpbGl0ZSAuYnAgeyBjb2xvcjogIzY1OGIwMCB9IC8qIE5hbWUuQnVpbHRpbi5Qc2V1ZG8gKi8KLmNvZGVoaWxpdGUgLmZtIHsgY29sb3I6ICMwMDhiNDUgfSAvKiBOYW1lLkZ1bmN0aW9uLk1hZ2ljICovCi5jb2RlaGlsaXRlIC52YyB7IGNvbG9yOiAjMDA2ODhCIH0gLyogTmFtZS5WYXJpYWJsZS5DbGFzcyAqLwouY29kZWhpbGl0ZSAudmcgeyBjb2xvcjogIzAwNjg4QiB9IC8qIE5hbWUuVmFyaWFibGUuR2xvYmFsICovCi5jb2RlaGlsaXRlIC52aSB7IGNvbG9yOiAjMDA2ODhCIH0gLyogTmFtZS5WYXJpYWJsZS5JbnN0YW5jZSAqLwouY29kZWhpbGl0ZSAudm0geyBjb2xvcjogIzAwNjg4QiB9IC8qIE5hbWUuVmFyaWFibGUuTWFnaWMgKi8KLmNvZGVoaWxpdGUgLmlsIHsgY29sb3I6ICNCNDUyQ0QgfSAvKiBMaXRlcmFsLk51bWJlci5JbnRlZ2VyLkxvbmcgKi8KICAgIC8qIHBhZ2VfY3NzICovCgogICAgCiAgICBodG1sewogICAgICAgIGJhY2tncm91bmQ6ICMyMjIyMjI7CiAgICB9CiAgICBib2R5ewogICAgICAgIHdpZHRoOiA5MCU7CiAgICAgICAgbWF4LXdpZHRoOiA5NjBweDsKICAgICAgICBiYWNrZ3JvdW5kOiAjRjlGNUU4OwogICAgICAgIG1hcmdpbjogM2VtIGF1dG8gMDsKICAgICAgICBwYWRkaW5nLXRvcDogMmVtOwogICAgICAgIGJvcmRlcjogMXB4IHNvbGlkICMyMjIyMjI7CiAgICAgICAgYm9yZGVyLXdpZHRoOiAwIDFweDsKICAgIH0KCiAgICAucG9zdHsKICAgICAgICBwYWRkaW5nOiA1JSAxMCU7CiAgICAgICAgbWFyZ2luLXRvcDogMDsKICAgICAgICBtYXJnaW4tYm90dG9tOiAwOwogICAgfQogICAgCgogICAgLnRpdGxlX2NvbnRhaW5lcnsKICAgICAgICBtYXJnaW46IC0yZW0gMCAzLjVlbTsKICAgICAgICBwYWRkaW5nLWJvdHRvbTogMmVtOwogICAgICAgIGJvcmRlci1ib3R0b206IDNweCBkb3VibGUgIzIyMjIyMjsKICAgIH0KICAgIC50aXRsZV9jb250YWluZXIgaDF7CiAgICAgICAgbWFyZ2luLXRvcDogMS4yZW07CiAgICAgICAgbWFyZ2luLWJvdHRvbTogMC42ZW07CiAgICAgICAgbGluZS1oZWlnaHQ6IDEuMzU7CiAgICAgICAgZm9udC1zaXplOiAyLjI1ZW07CiAgICB9CiAgICAudGl0bGVfY29udGFpbmVyIGgyewogICAgICAgIGNvbG9yOiAjODg4ODg4OwogICAgICAgIGZvbnQtc2l6ZTogMWVtOwogICAgICAgIGZvbnQtd2VpZ2h0OiBub3JtYWw7CiAgICAgICAgcGFkZGluZy1ib3R0b206IDJlbTsKICAgICAgICBsaW5lLWhlaWdodDogMS4zNTsKICAgICAgICBtYXJnaW4tYm90dG9tOiAtMmVtOwogICAgfQoKICAgIEBtZWRpYSBvbmx5IHNjcmVlbiBhbmQgKG1heC13aWR0aDogNzYwcHgpewogICAgICAgIGh0bWx7CiAgICAgICAgICAgIGJhY2tncm91bmQ6IHRyYW5zcGFyZW50OwogICAgICAgIH0KICAgICAgICBib2R5ewogICAgICAgICAgICBtYXJnaW46IDA7CiAgICAgICAgfQogICAgICAgIC5wb3N0ewogICAgICAgICAgICBwYWRkaW5nOiAwOwogICAgICAgIH0KICAgIH0KICAgIC8qIHBhZ2VfY3NzICovCgogICAg">
    <!--header_scripts-->
</head>
<body>
    <div class="post">
        <div class="post_body">
            
            <h1 id="toc_0" class="h16 md_first_h">ConfigConverter 使用说明</h1>
<div class="toc_container">
<div class="toc"><ul>
<li>
<a href="#toc_0">ConfigConverter 使用说明</a>
<ul>
<li>
<a href="#toc_1">参考信息</a>
</li>
<li>
<a href="#toc_2">部署方式</a>
</li>
<li>
<a href="#toc_3">功能说明</a>
<ul>
<li>
<a href="#toc_4">密码保护</a>
</li>
<li>
<a href="#toc_5">单一脚本加设备 ID</a>
</li>
<li>
<a href="#toc_6">脚本订阅生成设备 ID</a>
</li>
<li>
<a href="#toc_7">脚本订阅生成设备 ID - 预设版</a>
</li>
</ul>
</li>
<li>
<a href="#toc_8">更多</a>
<ul>
<li>
<a href="#toc_9">修改环境变量</a>
</li>
<li>
<a href="#toc_10">手动触发部署</a>
</li>
<li>
<a href="#toc_11">更新</a>
<ul>
<li>
<a href="#toc_12">Mac / Windows</a>
</li>
<li>
<a href="#toc_13">iPhone / iPad</a>
</li>
</ul>
</li>
</ul>
</li>
<li>
<a href="#toc_14">最后说明</a>
</li>
</ul>
</li>
</ul>
</div>
</div><h2 id="toc_1" class="h16">参考信息</h2>

<ul>
<li class="md_li"><span><a class="md_compiled" href="https://github.com/ImSingee/ConfigConverter">Github 本项目主页</a>
</span></li>
<li class="md_li"><span><a class="md_compiled" href="https://t.me/singee_daily">最新消息发布频道</a>
</span></li>
</ul>
<h2 id="toc_2" class="h16">部署方式</h2>

<p class="md_block">
    <span class="md_line md_line_start md_line_end">为了确保操作的稳定性，部署操作请尽量在电脑端完成，并保证使用了科学的上网方式。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">预先准备：一个 <a class="md_compiled" href="https://github.com/">Github</a> 账号。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start">在浏览器中打开 <a class="md_compiled" href="https://github.com/ImSingee/ConfigConverter">Github 本项目主页</a>，点击下方的「Deploy to netlify」按钮<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/0587fe861faa057411eadcb5776caeed.png" alt="" title="" ></p>


<p class="md_block">
    <span class="md_line md_line_start">点击 Connect to GitHub 按钮，登录你的 GitHub 账号并授权<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/fd75e017fdecfef55d9c560ad9fc2dd0.png" alt="" title="" >
    <span class="md_line md_line_end">（Netlify 最近服务器有点问题，如果这里一直显示 Loading Template 请多刷新几次）</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start">设定一定的变量<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/6e8979ee23a926cff1bd9c463d90365a.png" alt="" title="" >
    <span class="md_line md_line_end">如果你是第一次在 Netlify 授权 GitHub，可能会导致丢失这些配置项，此时请重新回到第一步点一次「Deploy to netlify」按钮即可。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">密码保护是由于 Netlify 对于 function 的用量有一定限制，因此可以设定一个密码使得相应 API 只有你自己可以使用。关于密码保护的说明可以参见后文。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">预设参数可以从 <a class="md_compiled" href="https://config-converter.netlify.com/generator/QuantumultXScriptSubscriptionAddDeviceIDPreset">预设生成器</a> 生成，如果还存有疑虑可用先不填写或阅读后文关于预设的讲解后使用。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start">点击「Save &amp; Deploy」按钮保存并部署，完成后会进入 Overview 面板<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/c67243b943c59e3b7abab3abcd0eb501.png" alt="" title="" ></p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">刚进入时候的状态为「Site deploy in progress」，第一次部署会比较慢，请耐心等待。</span>
</p>


<p class="md_block">
<img   class="md_compiled " src="https://www.markeditor.com/file/get/8cc4e32fc1b7e8729e0174eea0d59a2e.png" alt="" title="" >
    <span class="md_line md_line_end">待部署完成后，这里会变成一个网址，例如这里是 https://thirsty-leakey-f16fe3.netlify.com ，记录备用，<strong>以后所有的「打开 /xxx 」都是指的打开「这个网址后接 /xxx 」</strong>。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">部署完成。</span>
</p>

<h2 id="toc_3" class="h16">功能说明</h2>
<h3 id="toc_4" class="h16">密码保护</h3>

<p class="md_block">
    <span class="md_line md_line_start md_line_end">如果开启密码保护则下面相应的 API 使用都需要在末尾加一个 <code>&amp;pwd=你的密码</code>，为了避免麻烦，建议没有相关网络知识的用户只使用大小写字母与数字作为密码，否则可能涉及到 URLEncode 转义问题。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">密码保护功能开关与密码的设置可以在首次部署时设置，后续如需修改请修改 <code>FORCE_PASSWORD</code> 与 <code>PASSWORD</code> 环境变量，具体修改方式请看后文。</span>
</p>

<h3 id="toc_5" class="h16">单一脚本加设备 ID</h3>

<p class="md_block">
    <span class="md_line md_line_start md_line_end">可自动将相应 url 对应的脚本修改为已加入设备 ID 版本的脚本。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">打开 /generator/QuantumultXScriptAddDeviceID，输入自己的密码（未设定请留空）、设备 ID（多个 ID 请用空格分隔）、脚本链接（注意前后不要有空格），点击生成。生成的网址打开就是添加好了设备 ID 的版本。</span>
</p>

<h3 id="toc_6" class="h16">脚本订阅生成设备 ID</h3>

<p class="md_block">
    <span class="md_line md_line_start md_line_end">可自动将订阅网址中 script-response-body 类型的 url 对应的脚本修改为已加入设备 ID 版本的脚本。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">打开 /generator/QuantumultXScriptSubscriptionAddDeviceID，输入自己的密码（未设定请留空）、设备 ID（多个 ID 请用空格分隔）、脚本订阅链接（注意前后不要有空格），点击生成。将生成的网址添加到引用中。</span>
</p>

<h3 id="toc_7" class="h16">脚本订阅生成设备 ID - 预设版</h3>

<p class="md_block">
    <span class="md_line md_line_start md_line_end">是缩短上述「脚本订阅生成设备 ID」的功能增强，用于缩短网址、进一步加强防封功能。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start">环境变量 <code>PRESET_NUMBER</code> 用于设定开启的预设数量，要求值为 0-255 之间的数字，设定为 0 即为关闭预设。<br /></span>
    <span class="md_line md_line_end">环境变量 <code>PRESET_预设编号</code> 用于设定相应预设对应的参数，预设编号为 1-PRESET_NUMBER 之间的数字，参数可以通过 /generator/QuantumultXScriptSubscriptionAddDeviceIDPreset 生成。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">配置好环境变量后，使用 <code>/api/QuantumultXScriptSubscriptionAddDeviceID?preset=预设编号&amp;pwd=密码</code> （未开启密码可将后面的 <code>&amp;pwd=密码</code> 删除）可直接加载对应的配置信息。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">环境变量的修改方式请看后文。</span>
</p>

<h2 id="toc_8" class="h16">更多</h2>
<h3 id="toc_9" class="h16">修改环境变量</h3>

<p class="md_block">
    <span class="md_line md_line_start">依次进入 Settings - Build&amp;Deploy - Environment<br /></span>
 <img   class="md_compiled " src="https://www.markeditor.com/file/get/8836545d0e036f3e0946db1430a4b2b3.png" alt="" title="" >
<img   class="md_compiled " src="https://www.markeditor.com/file/get/232a6c956dc70c976a77c91eae16de5c.png" alt="" title="" ></p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">点击「Edit variables」，即可修改相应环境变量。如果相应的需要的环境变量这里没有那么点击 「New variable」新建一个并在 Key 输入相应的变量名、Value 输入值。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">修改完环境变量后需要重新部署一次，手动触发部署方式请看下文。</span>
</p>

<h3 id="toc_10" class="h16">手动触发部署</h3>

<p class="md_block">
    <span class="md_line md_line_start md_line_end">在 GitHub 仓库 push 时会自动触发一次部署，如果有需要（例如修改了环境变量）时也可以手动触发一次部署。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start">首先打开「Setting - Build&amp;Deploy - Continuous Deployment」，下滑找到 Build hooks<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/e24cf575a12cd418e30b4dab00dfb7c9.png" alt="" title="" ></p>


<p class="md_block">
    <span class="md_line md_line_start">点击「Add build hook」，设定一个名字，保存。<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/778e3fc2660d6ec334ac48351720f5bc.png" alt="" title="" >
    <span class="md_line">然后会得到一个网址，例如这里是 <code>https://api.netlify.com/build_hooks/5ddb71b290143934eb8da4af</code><br /></span>
    <span class="md_line">利用软件对这个网址发起一次 POST 请求即可触发部署；如果没有顺手的软件那么可以访问 <a class="md_compiled" href="https://reqbin.com/">ReqBin</a>，选择 POST 并输入相应的网址后点击 Send 。<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/c89ae7d8c09f7b165302b42b4404e1f5.png" alt="" title="" ></p>


<p class="md_block">
    <span class="md_line md_line_start">稍等片刻即可在 Netlify Overview 中看到这一手动触发的部署，等待部署完成即可。<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/4cb81bd77f2596689db780c077fc1a48.png" alt="" title="" ></p>

<h3 id="toc_11" class="h16">更新</h3>

<p class="md_block">
    <span class="md_line md_line_start md_line_end">Netlify 部署是无法直接更新的，如需更新可以删掉重建，也可以使用下面所叙的方式更新。</span>
</p>

<h4 id="toc_12" class="h16">Mac / Windows</h4>

<p class="md_block">
    <span class="md_line md_line_start md_line_end">下载并安装 <a class="md_compiled" href="https://git-fork.com/">Fork</a>，运行。首次运行可能需要输入姓名和邮箱，姓名输入自己常用网名邮箱输入 Github 对应邮箱即可。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">点击菜单栏 File - Clone，在下方选择 Github，登录自己的 Github 账号。选择仓库（如果你在前面部署过程中没改名那么就是 ConfigConverter，否则是相应改后的名字），点击 Clone。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start">等待克隆完成后，在左侧侧边栏右键点击 Remotes，选择 Add New Remote<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/7761fb684289b3907629ac3c1827cf16.png" alt="" title="" ></p>


<p class="md_block">
    <span class="md_line md_line_start">Remote 输入 <code>upstream</code>、Repository URL 输入 <code>git@github.com:ImSingee/ConfigConverter.git</code>，保存。确认 Remotes 多了一个 upstream。<br /></span>
    <span class="md_line md_line_with_image"><img   class="md_compiled " src="https://www.markeditor.com/file/get/99f112b66d6ce837e9f60464057f8977.png" alt="" title="" >（Remote 那里输入 upstream，图错了我懒得改了）<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/3685ec1adfa29fd7d67d9e3e33226b85.png" alt="" title="" ></p>

<span class="md_repeated_n md_repeated_n_1"></span>
<p class="md_block">
    <span class="md_line md_line_start">右键点击 upstream，选择 Fetch，保持默认选项不变，点击 Fetch。<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/4d9097c4f45ebdcac4e01eecfe2d75ec.png" alt="" title="" ><img   class="md_compiled " src="https://www.markeditor.com/file/get/d9230eb25cf29b1a0ecf03eb40dba927.png" alt="" title="" >
    <span class="md_line">稍等成功后，upstream 下会多出一个 master，右键点击 master，选择 「Pull &#39;upstream/master&#39; into &#39;master&#39;」，保持默认选项不变，点击 Pull。<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/fd8e8c35237344c66d768fafa23f329f.png" alt="" title="" ><img   class="md_compiled " src="https://www.markeditor.com/file/get/48dc2f7591a1edb6a9f339d1858c93b8.png" alt="" title="" >
    <span class="md_line">稍等完成后，右键点击 Branches 中的 master 下的「Push &#39;master&#39; to」，选择 origin，保持默认选项不变，点击 Push。<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/05b1f8af4fb47dda68ffaaa5121de4fd.png" alt="" title="" ><img   class="md_compiled " src="https://www.markeditor.com/file/get/a57ca26d7cb906fcc0976c1e6a933216.png" alt="" title="" ></p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">等待完成后检查 Netlify Overview 看是否触发了自动部署，触发成功等待部署完成后即更新完成。</span>
</p>

<h4 id="toc_13" class="h16">iPhone / iPad</h4>

<p class="md_block">
    <span class="md_line md_line_start md_line_end">打开 Working Copy，点击上方的加号，选择「Clone Repository」，选择 GitHub，登录你的 GitHub 账号，选择仓库（如果你在前面部署过程中没改名那么就是 ConfigConverter，否则是相应改后的名字），点击克隆。</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start">完成后点击上方的「Repository」<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/fac5cdf8c860f7e5012fbc0bf9c6173b.png" alt="" title="" ></p>


<p class="md_block">
    <span class="md_line md_line_start">滑动到下方点击「Add Remote」，Name 输入 <code>upstream</code>、URL 输入 <code>git@github.com:ImSingee/ConfigConverter.git</code>，关闭 Allow Push，右上角点 Save。确认 Remotes 多了一个 upstream。<br /></span>
<img   class="md_compiled " src="https://www.markeditor.com/file/get/3c0ab10b459b28b6cb974cf7e1ed8105.png" alt="" title="" ></p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">在 upstream 左滑选择 Pull、origin 左滑选择 push。（第一次 Push 时可能需要你输入个人信息，Name 输入常用网名、Email 输入 GitHub 绑定的邮箱即可）</span>
</p>


<p class="md_block">
    <span class="md_line md_line_start md_line_end">等待完成后检查 Netlify Overview 看是否触发了自动部署，触发成功等待部署完成后即更新完成。</span>
</p>

<h2 id="toc_14" class="h16">最后说明</h2>

<p class="md_block">
    <span class="md_line md_line_start md_line_end">如读完文档遇到了文档中未写到的问题请通过 <a class="md_compiled" href="https://t.me/atbryanbot">@Byran</a> 与我联系。</span>
</p>
        </div>
    </div>
    <!--mathjax-->
    <!--mermaid-->
</body>
</html>
