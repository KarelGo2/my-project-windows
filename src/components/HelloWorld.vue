<template>
   <div id="ytt">
<div id = "computed_props">
    千米 : <input type = "text" v-model = "kilometers">
    米 : <input type = "text" v-model = "meters">
</div>
<p id="info"></p>
<div v-bind:class="{ active: isActive }"></div>
 <div class="static"
     v-bind:class="{ active: isActive, 'text-danger': hasError }">
  </div>

  <div v-bind:class="classObject"></div>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data : function(){
    return  {
      classObject: {
      active: true,
      'text-danger': true
    },
      hasError: true,
       isActive: true,
       kilometers : 0,
        meters: 0,
      // seen: true,
      // object: {
      // name: '菜鸟教程',
      // url: 'http://www.runoob.com',
      // slogan: '学的不仅是技术，更是梦想！'
      //  },
      // ok: true,
      // msg: 'Welcome to Your Vue.js App',
      message: 'helo',
      name: 'Google',
    url: 'http://www.google.com'
      // ,
      // type: 'C',
      // sites: [{ name: 'Runoob' }, { name: 'Google' }, { name: 'Taobao' }]
   }
  },
computed: {
    site: {
      // getter
      get: function () {
        return this.name + ' ' + this.url
      },
      // setter
      set: function (newValue) {
        var names = newValue.split(' ')
        this.name = names[0]
        this.url = names[names.length - 1]
      },
       classObject: function () {
      return {
        active: this.isActive && !this.error,
        'text-danger': this.error && this.error.type === 'fatal',
      }
    }
    }
  },
  watch : {
        kilometers:function(val) {
            this.kilometers = val;
            this.meters = val * 1000;
        },
        meters : function (val) {
            this.kilometers = val/ 1000;
            this.meters = val;
        }
    }
}

// 调用 setter， vm.name 和 vm.url 也会被对应更新
// vm.site = '菜鸟教程 http://www.runoob.com';
// document.write('name: ' + vm.name);
// document.write('<br>');
// document.write('url: ' + vm.url);
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.active {
	width: 100px;
	height: 100px;
	background: green;
}

.text-danger {
	background: red;
}
</style>
