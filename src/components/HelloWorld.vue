<template>
  <div>
    <!-- <input id="test" type="text" v-model="dataList"> -->
    <div>
      {{dataList}}
      <br/>
      {{ testList}}
      <!-- {{ parseInt('10%')}} -->
    </div>
    <button @click="change"> chagne </button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      count: 0,
      testList:[],
      dataList:[0,3,6,9,12,15,18,21,24,27,30,33,36,39,42],
      times : 0,
      testlist : [],
      testCount : 0,
    }
  },
  mounted(){
    this.testlist = []

    setInterval(()=>{
      console.log(this.testCount)
      this.testlist[this.testCount] ='0'
      this.testlist.push('12')
      console.log(this.testlist)
    }, 1000)
    
    setInterval(() => {
      this.testCount += 1
      if(this.testCount > 14){
        this.testCount = 0
      }
    }, 1000);
    
    // 3초마다 3씩 증가해서 1분마다 리셋
    setInterval(() => {
      this.times += 3 
      
      this.testList.push(this.count * 3);
      this.count += 1;

      if(this.times > 59){
        this.times = 0
        this.count = 0
      }

      if(this.testList.length>15){
        this.testList.shift()
      }

      // if(this.count > 15){
      //   if(this.count > 20){
      //     this.count = 0
      //   }
      //   this.testList.shift()
      // }
    }, 3000);
  },
  watch:{
  },
  methods:{
    change(){
      this.testList.shift()
      
      // const item = this.dataList.splice(0, 1);
      // 15초 마다 실행?? 배열 자리가 꽉차면 실행?  3초마다 backend socket이 들어오는 점을 감안
      // this.dataList.splice(this.dataList.length,0, item[0])
    }
  }
}
</script>
