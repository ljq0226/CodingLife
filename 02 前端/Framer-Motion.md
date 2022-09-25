

# Motion
今天我们来学习**framer-motion**这个超炫酷的动画库。
>Framer Motion is a production-ready motion library for React from [Framer](https://www.framer.com/).

motion 简单但功能强大，允许使用健壮的语义标记来表示复杂的用户交互。接下来我们将逐一探索motion中的强大功能。

## Animation
###  Transitions
默认情况下，Motion会根据动画值的类型为一个流畅的过渡创建一个适当的动画。例如，像`x`或`scale`这样的物理属性将通过`spring`模拟进行动画化。而`opacity`(不透明度)或`颜色`等值将使用补间动画。  

但是，您可以通过将默认转换传递给转换道具来定义不同类型的动画。


+ 设置initial为false 禁止进入动画
```tsx
<motion.div animate={{ x: 100 }} initial={false} />
```

###  Exit Animation 
在React中，当一个组件从DOM树中移除时，它会立即被移除。Framer Motion提供AnimatePresence组件，在组件执行退出动画时将组件保留在DOM中。
```tsx
<AnimatePresence>
  {isVisible && (
    <motion.div
      initial={{ opacity: 0 }}
      animate={{ opacity: 1 }}
      exit={{ opacity: 0 }}
    />
  )}
</AnimatePresence>
```

###  KeyFrames（关键帧）

animate中的值也可以设置为一系列关键帧，这将按顺序通过每个值制作动画。
```tsx
<motion.div
  animate={{ x: [0, 100, 0] }}
/>
```