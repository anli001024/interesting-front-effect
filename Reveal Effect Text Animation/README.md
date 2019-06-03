# 有趣的交互系列 - 文字遮罩入场效果
在这个系列里分享一些简单，但是很有意思的交互效果~

![效果图](https://an-l.oss-cn-beijing.aliyuncs.com/img/reveal_effect_text_animation.gif)


实现思路：
1. 监听滚动，添加对应加载的class(比如`loaded`)
2. 巧用animation实现文字和遮罩层的动画效果
3. 文字动画: `opacity 0 -> 1`;
4. 遮罩层动画: 首先`width 0 -> 100%`,然后把`width 100% -> 0`且`left 0 -> 100%`，这样就实现了遮罩层的进场和退出效果;

``` css
[data-reveal="cover"] {
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 100%;
    z-index: 1;
}

[data-reveal="text"] {
    opacity: 0;
}


[data-js="reveal"].loaded [data-reveal="cover"] {
    animation: reveal-cover 1.5s ease-in-out;
}

[data-js="reveal"].loaded [data-reveal="text"] {
    opacity: 1;
    animation: reveal-text 1.5s ease-in-out;
}

@keyframes reveal-cover {
    0% {
        width: 0;
        left: 0;
    }

    44% {
        width: 100%;
        left: 0;
    }

    54% {
        width: 100%;
        left: 0;
    }

    100% {
        width: 0;
        left: 100%;
    }
}

@keyframes reveal-text {
    0% {
        opacity: 0;
    }

    44% {
        opacity: 0;
    }

    54% {
        opacity: 1;
    }
}

```