# vue-more-preview

vue-more-preview是基于[vue-preview](https://www.npmjs.com/package/vue-preview)的图片预览插件，它修复了vue-preview引用时报错的bug，同时为options参数增加了style字段，以解决同页面里多区块中需要图片预览时出现的问题。![效果图](https://www.moment16.com/likely6/images/VUE_vue-moew-preview-01.jpg)


>npm安装
```
npm i vue-more-preview --save
```

>main.js引入
```
import VueMorePreview from 'vue-more-preview'
Vue.use(VueMorePreview)
```

>例子 这个例子就展示了当要在两个区块内分别预览图片时的情况。

>vue-more-preview除了为options增加了一个style参数，其他使用都一样，具体使用参考[vue-preview](https://www.npmjs.com/package/vue-preview)
```
<template>
  <div class="showA">
	<img class="preview-imgA" v-for="(item, index) in listA" :src="item.src" @click="openA(index)">
  </div>
  <div class="showB">
	<img class="preview-imgB" v-for="(item, index) in listB" :src="item.src" @click="openB(index)">
  </div>
</template>
<script>
export default {
	data () {
		return {
			#注意这里的listA里的字段名必须按以下示例的名称命名
			listA: [{
				src: 'https://placekitten.com/600/400',
				w: 600,
				h: 400
			}],
			listB: [{
				src: 'https://placekitten.com/600/400',
				w: 600,
				h: 400
			}, {
				src: 'https://placekitten.com/1200/900',
				w: 1200,
				h: 900
			}]
		}
	},
	methods: {
		openA(index) {
			$preview.open(index, this.listA, {
				style: '.preview-imgA'
			})
		},
		openB(index) {
			$preview.open(index, this.listB, {
				style: '.preview-imgB'
			})
		}
	}
}
</script>
```
