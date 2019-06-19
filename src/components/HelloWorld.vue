<template>
  <div>
    <label>День событии: </label><input type="date" v-model="myDate"><br><br>
    <label>Название событии: </label><input type="text" v-model="comment" placeholder="Название событии">
    <p>{{days3}} дней - {{hour3}} часов - {{minute3}} минут - {{second3}} секунд - до {{comment}}а</p>
  </div>
</template>

<script>
  import NewDate from './NewDate'
  export default {
    data() {
      return {
        // mdl: new Date('2011-04-11T10:20:30'),
        myDate: '2019-12-31',
        comment: 'Новый год',
        now: 0,
        now2: 0,
        newDate: '',
        count: 0,
        days3: 0,
        hour3: 0,
        minute3: 0,
        second3: 0,
      }
    },
    mounted () {
      this.updateNow()
      setInterval(this.updateNow.bind(this) , 1000)
    },
    
    methods: {
      updateNow() {
        this.now = Math.round(Date.now() / 1000)
        this.now2 = Math.round(Date.parse(this.myDate) / 1000)
        this.count = this.now2 - this.now;
        if(this.count >= 0){  
          this.second3 = this.count % 60
          this.minute3 = Math.floor(this.count / 60) % 60
          this.hour3 = Math.floor(this.count / 3600) % 24
          this.days3 = Math.floor(this.count / 60 / 60 / 24) 
        }        
      }
    },
    components: {
      NewDate,
    }
  }
</script>

<style scoped>

</style>