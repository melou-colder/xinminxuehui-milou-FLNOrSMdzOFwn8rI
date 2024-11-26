
hello，大家好，我是程序员海军，公众号已经快一年多没更新了，没更新的这段时间，我去哪了呢。这两年经历了很多事情，主要情感上占据大部分时间， 从失恋 \- 谈对象 \- 再失恋。


言归正传，近期我负责的公司人力资源系统中，薪酬统计模块的开发进度正稳步推进。在此过程中，我发现需要展示多种图表（如 ECharts）来直观反映数据。然而，ECharts 的配置过程相对复杂，频繁查阅官方文档不仅耗时，而且效率不高。为了提升开发效率，我萌生了这样一个想法：将 ECharts 中的一些通用属性进行提炼和整理，同时汇总常用的配置项以及在实际应用中需要注意的要点。这样一来，不仅能够简化配置过程，还能为团队提供一个便捷的参考指南。


## EChart 资源


### Vue\-EChart


***不想封装 Echart， 可以选用这种方案。***


Vue\-ECharts 是一个 Vue 组件，旨在简化在 Vue 应用中集成 ECharts 的过程。它封装了 ECharts 的初始化和使用逻辑，用户只需要在 Vue 模板中添加组件并传递相应的 props，即可轻松创建图表。


支持Vue2 \& Vue3 \& Nuxt3



> DOC： [https://github.com/ecomfe/vue\-echarts\#readme](https://github.com)


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102105928-1307485532.png)


优点：


1. Vue\-ECharts 组件会自动处理 ECharts 实例的生命周期，能够根据 Vue 组件的状态变化自动更新图表。这使得代码更加简洁，易于维护。
2. 通过 Vue 的数据绑定机制，可以直接将数据绑定到组件的 props 上，Vue\-ECharts 会自动将数据变化应用到图表上。
3. 作为 Vue 组件，可以很容易地与其他 Vue 组件组合，并且可以利用 Vue 的指令和事件系统。


### EChart 配置生成 option


目前只有三种图表状态，可生成图片和JSON.



> [https://github.com/BruceHenry/chart\-creator](https://github.com)


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102122155-608991319.png)


### EChart 速查手册 \[官网]



> [https://echarts.apache.org/zh/cheat\-sheet.html](https://github.com)


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102226665-320181068.png)


### EChart 主题配置 \[官网]



> [https://echarts.apache.org/zh/theme\-builder.html](https://github.com)


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102243439-1636521680.png)


### EChart 社区示例 \[社区，提供了大量的示例基本可以满足任何需求]


1. [MCChart](https://github.com):[樱花宇宙官网](https://yzygzn.com)


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102311531-452290577.png)


2. [isqqw](https://github.com)


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102322335-978583803.png)


3. [MakeAPie](https://github.com)


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102335832-1262313206.png)


4. [PPChart](https://github.com)


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102351187-426243284.png)


## 阅读导图


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102405947-1129758901.png)


## 常用属性配置


### title 标题配置


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102419927-1256711300.png)


1. ***text \- 标题文本，例如 "柱状图"***
2. ***subtext***\- 副标题文本\*\*\*
3. \***left 标题的水平位置，可以是像'left' 'center' 'right' 或者像'20%'** 这样的百分比
4. ***top***\*\*\* \*\*****\- 标题的垂直位置，可以是像****\*\* \*\*****'top'******,**\*\*\*\* **\_\_**'middle'**\_\_**,**\_\_\*\* **\_\_**'bottom'**\_\_\*\* **\_\_**或者像\*\*\_\_\*\* **\_\_**'20%'**\_\_** **\_\_**这样的百分比\*\*\*
5. ***textStyle***\*\*\* \*\*****\- 控制标题文本样式的对象，可以包括****\*\* \*\*\*\***color**\*\*\*\*，******fontStyle******，******fontWeight******，******fontFamily******，\******fontSize\*\*\*\*\*\* \*\*\*\***等***
6. ***subtextStyle***\*\*\* \*\*****\- 控制副标题文本样式的对象，属性同****\*\* \*\*\*\***textStyle**\*
7. ***textAlign***\*\*\* \*\*****\- 标题文本对齐，例如****\*\* \*\*****'left'******,**\*\*\*\* **\_\_**'right'**\_\_**,\*\*\_\_\*\* **\_\_**'center'\*\*\*
8. ***padding***\*\*\* \*\*****\- 标题内边距，可以是数字或数组****\*\* \*\*\*\***\[上, 右, 下, 左]**\*
9. ***itemGap \- 主副标题之间的间距***



```
option = {
    title: {
        // 主标题文本设置
        text: '主标题文本',
        // 副标题文本设置
        subtext: '副标题文本',
        // 标题水平位置设置，'center' 表示居中
        left: 'center',
        // 标题垂直位置设置，'top' 表示顶部
        top: 'top',
        // 主标题样式设置，包括文字颜色、字体风格、字体粗细、字体族、字体大小
        textStyle: {
            color: 'black',      // 文字颜色
            fontStyle: 'normal', // 字体风格，'normal'表示普通样式
            fontWeight: 'bold',  // 字体粗细，'bold'表示加粗
            fontFamily: 'Arial', // 字体族，这里设置为Arial
            fontSize: 18,        // 字体大小，单位像素
        },
        // 副标题样式设置，属性同主标题textStyle
        subtextStyle: {
            color: '#aaa',       // 文字颜色
            fontStyle: 'normal', // 字体风格
            fontWeight: 'normal',// 字体粗细
            fontFamily: 'Arial', // 字体族
            fontSize: 12,        // 字体大小
        },
        // 标题文本对齐方式，'center' 表示居中对齐
        textAlign: 'center',
        // 标题内边距，第一个值表示上边距，第二个值表示右边距
        padding: [5, 10],
        // 主副标题之间的间距
        itemGap: 10
    },
    // 此处省略其他的图表配置选项…
};

```

### tooltip 提示框


1. ***formatter******\- 提示框浮层的内容格式器，支持字符串模板和回调函数两种形式***
2. ***axisPointer******\- 坐标轴指示器配置，指定其类型如******'line'******、******'shadow'******等***
3. ***show******\- 是否显示提示框组件，包括提示框浮层和 axisPointer，默认为***\*\*\* \*\*\****true***
4. ***backgroundColor******\- 提示框浮层的背景颜色***
5. ***borderColor******\- 提示框浮层的边框颜色***
6. ***borderWidth******\- 提示框浮层的边框宽***
7. ***padding \- 提示框浮层内边距，可以是数字或数组** \_\_**\[上, 右, 下, 左]*\*\*



```
// 工具提示配置
    tooltip: {
        // 触发类型，'item' 表示数据项图形触发，用于散点图等无类目轴的图表，'axis' 表示坐标轴触发，用于柱状图等有类目轴的图表
        trigger: 'axis',
        // 自定义提示框内容
        formatter: function (params) {
            // `params` 是一个数组，包含了当前鼠标所在点的所有数据信息
            let res = params[0].name + '';
            params.forEach(function (item) {
                // 添加信息，这里只是个简单示例，具体格式可以自由配置
                res += item.seriesName + ': ' + item.value + '';
            });
            return res;
        },
        // 坐标轴指示器配置
        axisPointer: {
            type: 'shadow' // 'line' 表示直线指示器，'shadow' 表示阴影指示器
        },
        // 控制浮层显示
        show: true,
        // 浮层背景颜色
        backgroundColor: 'rgba(50,50,50,0.7)',
        // 浮层边框颜色
        borderColor: '#333',
        // 浮层边框宽度
        borderWidth: 0,
        // 浮层内边距
        padding: 10 // 或者使用数组形式，例如 [5, 10, 5, 10]
    },

```



1. ***formatter******\- 提示框浮层的内容格式器，支持字符串模板和回调函数两种形式***
2. ***axisPointer******\- 坐标轴指示器配置，指定其类型如******'line'******、******'shadow'******等***
3. ***show******\- 是否显示提示框组件，包括提示框浮层和 axisPointer，默认为***\*\*\* \*\*\****true***
4. ***backgroundColor******\- 提示框浮层的背景颜色***
5. ***borderColor******\- 提示框浮层的边框颜色***
6. ***borderWidth******\- 提示框浮层的边框宽***
7. ***padding \- 提示框浮层内边距，可以是数字或数组** \_\_**\[上, 右, 下, 左]*\*\*



```
// 工具提示配置
    tooltip: {
        // 触发类型，'item' 表示数据项图形触发，用于散点图等无类目轴的图表，'axis' 表示坐标轴触发，用于柱状图等有类目轴的图表
        trigger: 'axis',
        // 自定义提示框内容
        formatter: function (params) {
            // `params` 是一个数组，包含了当前鼠标所在点的所有数据信息
            let res = params[0].name + '';
            params.forEach(function (item) {
                // 添加信息，这里只是个简单示例，具体格式可以自由配置
                res += item.seriesName + ': ' + item.value + '';
            });
            return res;
        },
        // 坐标轴指示器配置
        axisPointer: {
            type: 'shadow' // 'line' 表示直线指示器，'shadow' 表示阴影指示器
        },
        // 控制浮层显示
        show: true,
        // 浮层背景颜色
        backgroundColor: 'rgba(50,50,50,0.7)',
        // 浮层边框颜色
        borderColor: '#333',
        // 浮层边框宽度
        borderWidth: 0,
        // 浮层内边距
        padding: 10 // 或者使用数组形式，例如 [5, 10, 5, 10]
    },

```



### legend（图例组件）


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102452091-1972381074.png)


**图表的图例，表示不同系列的标识。**



```
legend: {
    top: '5%',
    left: 'center',
    data: ['直接访问', '联盟广告', '搜索引擎']
}

```



### series（系列列表）


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102510501-345124520.png)


**每个 ****series**** 代表一组数据项的集合，对于饼图配置的主要部分。**


series 属性及其可能的值包括：


* *type: **'pie'** // 必须设置为 'pie' 表示这是一个饼图。*
* *radius: 半径，可以是百分比或固定像素值，也可以是数组形式表示内外半径。*
* *center: Pie图的中心位置。*
* *data: 数据项数组，每个数据项包括value**（数值）和** **name**（名称）。*
* *stillShowZeroSum: 如果所有数据值都是0，是否显示图形。*
* *label: 用于设置数据标签，如是否显示、位置、格式等。*




```
series: [
    {
        name: '访问来源',
        type: 'pie',
        radius: '50%', // 半径大小，支持百分比
        center: ['50%', '50%'], // 饼图的中心位置
        data: [
            {value: 335, name: '直接访问'},
            {value: 234, name: '联盟广告'},
            {value: 1548, name: '搜索引擎'}
        ],
        emphasis: {
            itemStyle: {
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowColor: 'rgba(0, 0, 0, 0.5)'
            }
        },
        stillShowZeroSum: true,
        label: {
            normal: {
                show: true,
                position: 'outside' // 标签的位置
            },
            emphasis: {
                show: true,
                textStyle: {
                    fontSize: '30',
                    fontWeight: 'bold'
                }
            }
        }
    }
]

```

### **toolbox** (工具栏配置)


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102523327-1327313095.png)


### **color** (配色方案)


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102534112-1819704173.png)


 定义颜色数组，用于系列中每个扇形的默认颜色：


* 示例：`['#5470C6', '#91CC75', '#FAC858', '#EE6666']`





### **animation** (动画配置)


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102544399-834337338.png)


### 完整配置示例代码



```
option = {
    title: {
        // 饼图的标题
        text: 'Pie Chart Example'
    },
    tooltip: {
        // 鼠标悬浮时的提示框设置
        trigger: 'item' // item: 数据项图形触发
    },
    legend: {
        // 图例组件，展示不同系列的标识颜色和名称
        top: '5%',    // 距离容器上方的距离
        left: 'center', // 水平居中
        // 对应系列名称的数据
        data: ['Direct Visit', 'Union Ad', 'Search Engine']
    },
    toolbox: {
    show: true, // 显示工具栏
    feature: {
      saveAsImage: {}, // 保存为图片功能
      restore: {} // 还原功能
    }
  },
    series: [
        {
            // 系列名称，用于tooltip的显示
            name: 'Access From',
            type: 'pie', // 类型必须为饼图
            // 饼图的半径大小
            radius: '55%',
            // 饼图的中心（圆心）位置
            center: ['50%', '60%'],
            // 数据数组，包含每个扇区的大小和名称
            data: [
                { value: 335, name: 'Direct Visit' },
                { value: 234, name: 'Union Ad' },
                { value: 1548, name: 'Search Engine' }
            ],
            // 强调样式，当鼠标悬浮时显示阴影等效果
            emphasis: {
                itemStyle: {
                    shadowBlur: 10, // 阴影的模糊大小
                    shadowOffsetX: 0, // 阴影水平方向上的偏移距离
                    shadowColor: 'rgba(0, 0, 0, 0.5)' // 阴影颜色
                }
            },
            // 标签的显示方式设定
            label: {
                normal: {
                    // 常规状态下的标签显示设置
                    show: true, // 是否展示标签
                    position: 'outside', // 标签的位置
                    // 标签的格式化器
                    formatter: '{b}: {c} ({d}%)'
                },
                emphasis: {
                    // 高亮状态下的文本样式定义
                    show: true,
                    textStyle: {
                        fontSize: '30', // 字体大小
                        fontWeight: 'bold' // 字体粗细
                    }
                }
            }
        }
    ]
};

```

## EChart 在 Vue3 中实战



```
// 图表实例的引用
  const chart = ref(null);

  // 初始化图表
  const initChart = () => {
    if (chart.value) {
      const myChart = echarts.init(chart.value); // 初始化 ECharts 实例
      myChart.setOption(props.option); // 设置配置项
    }
  };

  // 监听 props 的变化，动态更新图表
  watch(
    () => props.option,
    (newOption) => {
      if (chart.value) {
        const myChart = echarts.getInstanceByDom(chart.value); // 获取已初始化的图表实例
        myChart.setOption(newOption); // 更新配置项
      }
    }
  );


```

## 响应式处理


图表在窗口大小变化时能够自动调整。可以使用 `resize()` 方法手动调整图表大小，通常是在 `updated` 生命周期钩子中调用。



```
// 响应式调整图表大小， 监听窗口大小变化，确保图表自适应容器的大小。
const resizeChart = () => {
  if (chart.value) {
    const myChart = echarts.getInstanceByDom(chart.value);
    myChart.resize(); // 调整图表尺寸
  }
};

// 生命周期钩子
onMounted(() => {
  initChart(); // 组件挂载后初始化图表
  window.addEventListener('resize', resizeChart); // 监听窗口大小变化
});

```

## 动态数据更新


使用 Vue 的响应式数据（如 `ref` 或 `reactive`）配合 `watch`，在数据变化时调用 `chart.setOption()` 重新渲染图表。



```
const chartOption = ref({
      title: { text: '实时数据' },
      tooltip: { trigger: 'axis' },
      xAxis: { data: ['1', '2', '3', '4', '5'] },
      yAxis: {},
      series: [{
        name: '销量',
        type: 'line',
        data: [120, 132, 101, 134, 90]
      }]
    });



watch(
  () => props.option,
  (newOption) => {
    if (chartInstance.value) {
      chartInstance.value.setOption(newOption); // 动态更新图表配置
    }
  },
  { deep: true } // 深度监听
);



chartOption.value.series[0].data.push(Math.random() * 100);
chartOption.value.xAxis.data.push(String(chartOption.value.xAxis.data.length + 1));

```

## 图表容器大小自适应


父容器尺寸发生变化时，图表可能不会自动调整大小。 我们可以通过 监听 `resize` 事件或使用 Vue 的响应式布局方案，调用 `chart.resize()` 更新图表尺寸。



```
const observer = new ResizeObserver(() => {
  chartInstance.value?.resize(); // 动态调整大小
});
observer.observe(containerElement); // 监听容器


```

## 国际化与多语言支持


图表中包含的文案（如标题、提示）需要支持多语言。 我们可以使用 Vue I18n 或其他国际化工具动态替换文本。



```
npm install vue-i18n

```


```
import { useI18n } from 'vue-i18n';

const { t } = useI18n();
const option = reactive({
  title: { text: t('chart.title') },
});


```

## ECharts 图表导出



```
toolbox: {
  feature: {
    saveAsImage: { show: true },
  },
};


```

## 性能优化


### 销毁 ECharts 实例


在组件销毁时，确保销毁 ECharts 实例，防止内存泄漏。



```
 onBeforeUnmount(() => {
      if (chart.value) {
        const myChart = echarts.getInstanceByDom(chart.value);
        myChart.dispose(); // 销毁 ECharts 实例
      }
      window.removeEventListener('resize', resizeChart); // 移除事件监听
    });

```

### 


### 大数据渲染性能优化


数据量大时，ECharts 的渲染可能会导致性能瓶颈。 我们可以通过以下三种方式来达到优化作用


* **使用 **`**dataZoom**`**:** 允许用户缩放数据区域，减少可视数据点。
* **启用分片渲染:**



```

series: [
  {
    type: 'line',
    large: true, // 启用大数据优化
    largeThreshold: 4000, // 数据量门槛
  },
];

```

* **降级动画：** 动态数据场景中禁用或简化动画。



```
animation: false,
progressive: 4000, // 分步渲染
progressiveThreshold: 10000, // 数据点门槛

```

### 图表配置项太长，分离配置项


配置项代码过长，组件可读性降低。我们可以将配置项提取到单独的模块，便于复用和维护。


![image](https://img2024.cnblogs.com/blog/1654515/202411/1654515-20241126102604674-1391962725.png)


## EChart 知识点常考


### 如何初始化和销毁 ECharts 实例？


* `echarts.init(dom)` 初始化。
* `chart.dispose()` 销毁实例，避免内存泄漏。


### ECharts 常见配置项有哪些？


* `title`, `legend`, `tooltip`, `grid`, `xAxis`, `yAxis`, `series`, `toolbox`, `dataZoom`。


### 动态数据更新



```
- 如何实现图表数据的动态更新？
- 如何监听 `props` 变化并更新图表配置？

```

### 性能优化



```
- 大数据渲染场景如何优化？
- 什么是 `progressive` 渲染模式？

```

### 图表事件



```
- 如何捕获图表点击、悬停事件并执行对应的业务逻辑？

```

### 如何处理数据较多导致渲染卡顿的情况？


* 使用数据分片渲染（`progressive`）。
* 禁用动画。
* 使用 `dataZoom` 限制显示范围。


### 如何实现图表导出功能？


使用 `toolbox.feature.saveAsImage` 或通过 `chart.getDataURL()` 获取图表数据并导出。


## 最后


通过对 ECharts 通用属性的深入提炼与系统整理，以及常用配置项的归纳总结，我们能够迅速实现图表的搭建与展示，极大地提升了开发效率。此外，借助丰富的 ECharts 资源和示例，我们基本上能够满足大部分业务场景的需求。这样一来，我们不仅能够更加快捷地实现功能需求，还能腾出更多宝贵的时间，专注于其他重要任务。 


欢迎关注我的微信公众号[【前端自学社区】](https://github.com)，在那里我将分享更多关于前端技术的心得与实用技巧。


