## 更改icarus主题文件

### 使网站页面在大屏幕上显示的更宽

/themes/icarus/include/style/responsive.styl
修改`+fullhd()`如下

```styl
+fullhd()
    .is-2-column .container
        max-width: $fullhd - 2 * $gap
        width: $fullhd - 2 * $gap

    .is-1-column .container
        max-width: $widescreen - 2 * $gap
        width: $widescreen - 2 * $gap
```
