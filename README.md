# vue-croppa-upload

[Vue Croppa](https://zhanziyang.github.io/vue-croppa/#/) - A simple straightforward customizable image cropper

`npm install --save vue-croppa`  

## install

`$ vue create vue-croppa-upload`   
merge   
`$ cd vue-croppa-upload`    
`$ npm run serve`  

[![NPM](https://nodei.co/npm/gh-pages.png?downloads=true&stars=true)](https://nodei.co/npm/gh-pages/)  
> Publish files to a gh-pages branch on GitHub (or any other branch anywhere else).

`$ npm run deploy`

## study

[cropper.vue](https://github.com/zhanziyang/vue-croppa/blob/master/src/cropper.vue)  

##　Quick Start

[quick-start](https://zhanziyang.github.io/vue-croppa/#/quick-start)  

index.html
```html
<link href="https://unpkg.com/vue-croppa/dist/vue-croppa.min.css" rel="stylesheet" type="text/css">
```

main.js
```js
// If your build tool supports css module
import 'vue-croppa/dist/vue-croppa.css';
```


## Docs

[Appearance](https://zhanziyang.github.io/vue-croppa/#/customization)  
[Image Placeholder](https://zhanziyang.github.io/vue-croppa/#/demos) 


[Customization](https://zhanziyang.github.io/vue-croppa/#/customization)
Use the  `initial` slot. It's more flexible than the first method.  
NOTE: If the image resouce is not host on your site (under diffrent domain), you need to set  `crossOrigin="anonymous"`  
codepen [Vue Croppa Initial Image 1](https://codepen.io/zhanziyang/pen/mMOKXo)     
codepen [Vue Croppa remove file](https://codepen.io/zhanziyang/pen/RZKEbr) 

## Notes

前端canvas把url轉為base64，存在跨域問題
[canvas 圖片跨域（二）](https://blog.csdn.net/qq_37837134/article/details/80215617)

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
