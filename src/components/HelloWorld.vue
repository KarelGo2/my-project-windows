<template>
   <div id="ytt">

 

     <div v-runoob="{ color: 'green', text: '菜鸟教程!' }"></div>
     <div id="app"  v-runoob:hello.a.b="message">
</div>
<p>页面载入时，input 元素自动获取焦点：</p>
    <input v-focus>
      <ol>
    <todo-item v-for="item in sites" v-bind:todo="item" :key="item.text"></todo-item>
      </ol>
 <div>
      <input v-model="parentMsg">
      <br>
      <child v-bind:message="parentMsg"></child>
    </div>
	<p>
		全选：
	</p>
	<input type="checkbox" id="checkbox" v-model="checked" @change="changeAllChecked()">
	<label for="checkbox">
		{{checked}}
	</label>
	<p>
		多个复选框：
	</p>
	<input type="checkbox" id="runoob" value="Runoob" v-model="checkedNames">
	<label for="runoob">
		Runoob
	</label>
	<input type="checkbox" id="google" value="Google" v-model="checkedNames">
	<label for="google">
		Google
	</label>
	<input type="checkbox" id="taobao" value="Taobao" v-model="checkedNames">
	<label for="taobao">
		taobao
	</label>
	<br>
	<span>
		选择的值为:{{checkedNames}}
	</span>


 <p>input 元素：</p>
  <input v-model="message" placeholder="编辑我……">
  <p>消息是: {{ message }}</p>
	
  <p>textarea 元素：</p>
  <p style="white-space: pre">{{ message2 }}</p>
  <textarea v-model="message2" placeholder="多行文本输入……"></textarea>


<p>单个复选框：</p>
  <input type="checkbox" id="checkbox" v-model="checked">
  <label for="checkbox">{{ checked }}</label>
    
  <p>多个复选框：</p>
  <input type="checkbox" id="runoob" value="Runoob" v-model="checkedNames">
  <label for="runoob">Runoob</label>
  <input type="checkbox" id="google" value="Google" v-model="checkedNames">
  <label for="google">Google</label>
  <input type="checkbox" id="taobao" value="Taobao" v-model="checkedNames">
  <label for="taobao">taobao</label>
  <br>
  <span>选择的值为: {{ checkedNames }}</span>


  <input type="radio" id="runoob" value="Runoob" v-model="picked">
  <label for="runoob">Runoob</label>
  <br>
  <input type="radio" id="google" value="Google" v-model="picked">
  <label for="google">Google</label>
  <br>
  <span>选中值为: {{ picked }}</span>

  <select v-model="selected" name="fruit">
    <option value="">选择一个网站</option>
    <option value="www.runoob.com">Runoob</option>
    <option value="www.google.com">Google</option>
  </select>
 
  <div id="output">
      选择的网站是: {{selected}}
  </div>

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
  <div v-bind:class="[activeClass, errorClass2]"></div>
  <div v-bind:class="[errorClass ,isActive ? activeClass : '']"></div>
  <div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }">菜鸟教程</div>
   <div v-bind:style="[baseStyles, overridingStyles]">菜鸟教程</div>
    <button v-on:click="counter += 1">增加 1</button>
  <p>这个按钮被点击了 {{ counter }} 次。</p>
  <button v-on:click="greet">Greet</button>
   <button v-on:click="say('hi')">Say hi</button>
  <button v-on:click="say('what')">Say what</button>
  <input v-on:keyup.13="submit('submit')">
  <button v-on:click="say('hi',$event)">say hi</button>
</div>
</template>

<script>

export default {
  name: "HelloWorld",
  data: function() {
    return {
      classObject: {
        active: true,
        "text-danger": true
      }, parentMsg: '父组件内容',
      checked: false,total : 0,
      checkedNames: [],
       sites: [
      { text: 'Runoob' },
      { text: 'Google' },
      { text: 'Taobao' }
    ],
      checkedArr: ["Runoob", "Taobao", "Google"],
      picked: "Runoob",
      checked: false,
      checkedNames: [],
      counter: 0,
      message: "Runoob",
      message2: "菜鸟教程\r\nhttp://www.runoob.com",
      baseStyles: {
        color: "green",
        fontSize: "30px"
      },
      overridingStyles: {
        "font-weight": "bold"
      },
      parentMsg: '父组件内容',
      selected: "",
      hasError: true,
      isActive: true,
      kilometers: 0,
      meters: 0,
      // seen: true,
      // object: {
      // name: '菜鸟教程',
      // url: 'http://www.runoob.com',
      // slogan: '学的不仅是技术，更是梦想！'
      //  },
      // ok: true,
      // msg: 'Welcome to Your Vue.js App',
      // message: 'helo',
      name: "Google",
      activeColor: "green",
      fontSize: 30,
      errorClass2: "text-danger2",
      activeClass: "active",
      errorClass: "text-danger",
      url: "http://www.google.com"
      // ,
      // type: 'C',
      // sites: [{ name: 'Runoob' }, { name: 'Google' }, { name: 'Taobao' }]
    };
  },
  methods: {
    changeAllChecked: function() {
      if (this.checked) {
        this.checkedNames = this.checkedArr;
      } else {
        this.checkedNames = [];
      }
    },incrementTotal: function () {
      this.total += 1
    },
    greet: function(event) {
      // `this` 在方法里指当前 Vue 实例
      alert("Hello " + this.name + "!");
      // `event` 是原生 DOM 事件
      if (event) {
        alert(event.target.tagName);
      }
    },
    say: function(message) {
      alert(message);
    },
    submit: function(message) {
      alert(message);
    },
    say: function(message, e) {
      alert(message);
      console.log(e.currentTarget);
    }
  },
  computed: {
    site: {
      // getter
      get: function() {
        return this.name + " " + this.url;
      },
      // setter
      set: function(newValue) {
        var names = newValue.split(" ");
        this.name = names[0];
        this.url = names[names.length - 1];
      },
      classObject: function() {
        return {
          active: this.isActive && !this.error,
          "text-danger": this.error && this.error.type === "fatal"
        };
      }
    }
  },
  watch: {
    checkedNames: function() {
      if (this.checkedNames.length == this.checkedArr.length) {
        this.checked = true;
      } else {
        this.checked = false;
      }
    },
    kilometers: function(val) {
      this.kilometers = val;
      this.meters = val * 1000;
    },
    meters: function(val) {
      this.kilometers = val / 1000;
      this.meters = val;
    }
  }
};

// 调用 setter， vm.name 和 vm.url 也会被对应更新
// vm.site = '菜鸟教程 http://www.runoob.com';
// document.write('name: ' + vm.name);
// document.write('<br>');
// document.write('url: ' + vm.url);
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
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

.text-danger2 {
  background: pink;
}
</style>
