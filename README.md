# Debounce

用于按键消抖的占用资源很小的 Arduino 库。例见 http://arduino.cc/en/Tutorial/Debounce 。

非常易于使用，包含三个例子。

**仅在 Arduino Due 测试过**

## 介绍

引入库头文件到你的程序。

    #include <Debounce.h>

### 构造

有如下两种：

#### 创建默认延时50ms的消抖按钮对象

    Debounce Button(4); // 4 is the pin, could be a variable too.

#### 创建自定义延时时间的消抖按钮对象

    Debounce Button(4, 80); // 4 is the pin, 80 is the delay, in ms.

## 函数仅有两个

### read()

在你的代码中， **Button.read();** 读取消抖后的你的按钮状态返回 HIGH 或 LOW，按压按钮当使用 **INPUT** 时会返回 HIGH ，当使用 **INPUT_PULLUP** 时会返回 LOW 。

下面的例子当按压并消抖按钮时会点亮13引脚的LED，直到你释放按钮。

    void loop() {
      digitalWrite(13, Button.read());
    }

### count()

返回每次你操作按钮之后按钮发生改变的次数，按压和释放都会次数+1.

下面的语句会只有在按钮被按压和释放5次时点亮LED。

    if (Button.count() == 10) {
      digitalWrite(13, HIGH);
    } else {
      digitalWrite(13, LOW);
    }
    
### resetCount()

返回按钮变化的次数。
