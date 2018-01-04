# 微信跳一跳辅助工具

这是一个需要手动来玩的辅脚本，也是最为保险，官方无法禁封的辅助工具；

支持`Mac OS`、`windows`、`Linux`系统，无需要手动设置`adb`环境。


## 安装

本地环境只需要安装好`Node.js 7.6`以上的版本即可（推荐`8.9.3`）;

国内网络环境建议安装好`cnpm`:

```bash
# cnpm安装
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

## 使用

- Android手机打开USB调试（一般操作步骤：设置-->开发人员工具-->打开USB调试）
- 连接手机到电脑，并在弹出的询问窗口中点击信任设备
- `clone`或下载项目文件到本地并解压
- 使用`bash`或`cmd`进入到解压好的目录
- `cnpm install`或`npm install`安装相关依赖
- `node index.js`运行即可
- 打开《跳一跳》游戏并点击开始
- 浏览器访问`http://localhost:5200`
- 不出意外，此时电脑上会显示手机截图，在画面区域用鼠标连接两个方块的中心点，然后点击右侧的【GO】按钮。手机上跳完之后，新的截图会同步到浏览器中，手动重复该步骤即可

**提示：**

- 各手机型号分辩率不一样，可根据自身设备在右侧的`Time/px`输入框中微调设置合适的值，直到每次能能跳到最中心；
- 连接两点之间，建议找好对应的参考点，例如：`小人的菊花` --> `目标中心`，见下图所示。

<video src="https://rawcdn.githack.com/sbfkcel/WechatJumpGameHelper/master/static/images/demo.mp4" width="888" height="500"></video>

![连接点示意图](https://rawcdn.githack.com/sbfkcel/WechatJumpGameHelper/master/static/images/Snipaste_2018-01-04_11-24-08.png?v=6)


## 原理

使用`Node.js`调用`adb`命令，拉取手机截图到浏览器。

用户在浏览器手动完成两个点的标记之后，点击【GO】按钮，通过`socket`消息告诉`Node`去执行`adb`操作。

之后将新的画面传回到前台...

## PS

**目前现成其它方案：**
- 拦截数据包伪造数据请求的 （修改数据提交加密方式就可被封掉）
- 自动识别画面完成跳跃的 （画面添加不规则的图案或干扰画面，自动识别即可能较难做到）
