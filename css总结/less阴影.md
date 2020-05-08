# ps阴影函数

```css
/**
 * 阴影处理方法
 * @distance 距离
 * @angle 角度
 * @extend 扩展
 * @size 大小
 * @color 颜色
 */
.shadow(@distance, @angle, @extend, @size, @color) {
  @x-offset: @distance*cos (180-@angle);
  @y-offset: @distance*sin (180-@angle);
  @spread: @size* @extend;
  @blur: @size- @spread;
  box-shadow: @x-offset @y-offset @blur @spread @color;
}
```
