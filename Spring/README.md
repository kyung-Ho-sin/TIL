2020-06-17 오늘의 목표
- vue에서 quill-editor 적용시키기

### vue에서 quill-editor 적용시키기
오늘은 quill-editor 를 vue 에 적용시켜 게시판을 만드는 작업을 진행했다.

quill-editor라고 검색을 하면 친절하게 설명이 잘안되있었다.여러가지를 찾던중 아래 부분을 보고 quill-editor를 vue에 적용시켰다.

```
  <template>
   <div id="app">
     <vue-editor v-model="content"></vue-editor>
   </div>
 </template>
 <script>
   import { VueEditor } from 'vue2-quill-editor'

   export default {

   components: {
      VueEditor
   },

   data() {
       return {
         content: '<h1>Some initial content<h1>'  
       }
     }
   }
 </script>
```
이와 같이 적용하면 qill-editor를 사용할수있다. custom을 하고 싶으면 아래 링크를 참조하면 된다.

### 내일 목표
- Spring boot 와 vue 통신 axios 와 proxy 에 대해서 공부
- 내일은 포트폴리오 강좌를 들으러간다. 잘준비해보자. 

[참고]https://developer.aliyun.com/mirror/npm/package/vue2-quill-editor

