<template>
  <h1>Test</h1>
  <input type="text" v-model="message" @keyup.enter.prevent="go"/>
  <button @click="go">전송</button>
  <div v-for="(item,index) in testList" :key="index">
    <ul>
      <li>{{ item }}</li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      message: "",
      testList: []
    }
  },
  created() {
    // localstorge의 값을 가져와서 testList에 푸시를 해놓는다.
    try{
      for(let i = 0; i < window.localStorage.length; i++){
      // key 찾기  
      const key = window.localStorage.key(i);

      // value 찾기
      const value = window.localStorage.getItem(key);

      console.log(key + " / " + value);
      this.testList.push(key + " / " + value)
    }
    } catch {
      console.log('error');
    } 
    finally{
      this.testList.sort();
      this.testList.reverse();
    }

  },
  methods: {
    go() {
      try {
        let date = new Date();
      // console.log(date.toLocaleString()+ ':'+ date.getMilliseconds());
      let now = date.toLocaleString()+ '.'+ date.getMilliseconds();
      let item = {
        "time" : now,
        "text": this.message
      }
      console.log(item);
      this.testList.push(item.time + " / " + item.text);
      
      window.localStorage.setItem(now, this.message);
      } catch{
        console.log('에러');
      } finally{
        this.message = "";
        this.testList.sort();
        this.testList.reverse();
      }
      
    }
  },
}
</script>