1. > Web基于DOM，而DOM很慢。浏览器打开网页时，需要解析文档，在内存中生成DOM结构，如果遇到复杂的文档，这个过程是很慢的。可以想象一下，如果网页上有上万个、甚至几十万个形状（不管是图片或CSS），生成DOM需要多久？更不要提与其中某一个形状互动了。
2. >  DOM拖慢JavaScript。所有的DOM操作都是同步的，会堵塞浏览器。JavaScript操作DOM时，必须等前一个操作结束，才能执行后一个操作。只要一个操作有卡顿，整个网页就会短暂失去响应。浏览器重绘网页的频率是60FPS（即16毫秒/帧），JavaScript做不到在16毫秒内完成DOM操作，因此产生了跳帧。用户体验上的不流畅、不连贯就源于此。
3. > 网页是单线程的。现在的浏览器对于每个网页，只用一个线程处理。所有工作都在这一个线程上完成，包括布局、渲染、JavaScript执行、图像解码等等，怎么可能不慢？
4. > 网页没有硬件加速。网页都是由CPU处理的，没用GPU进行图形加速。



### 设想

1. > 多线程浏览器。每个网页应该由多个线程进行处理，主线程只负责布局和渲染，而且应该在16毫秒内完成，JavaScript由worker线程执行，这样就不会发生堵塞了。Mozilla正在开发的Servo就是这样一个项目。
2. > DOM的异步操作。JavaScript对DOM的操作不再是同步的，而是触发后，交给Event Loop机制进行监听。
3. > 非DOM方案。浏览器不再将网页处理成DOM结构，而是变为其他结构。React的Virtual DOM方案就是这一类的尝试，还有更激进的方案，比如用数据库取代DOM。


### Typescript
TypeScript从今天数以百万计的JavaScript开发者所熟悉的语法和语义开始。使用现有的JavaScript代码，包括流行的JavaScript库，并从JavaScript代码中调用TypeScript代码。

TypeScript可以编译出纯净、 简洁的JavaScript代码，并且可以运行在任何浏览器上、Node.js环境中和任何支持ECMAScript 3（或更高版本）的JavaScript引擎中



## React
## Angular2
## Typescript