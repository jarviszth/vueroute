<template>
  <div class="about">
    <div class="form">
      <div class="title">
        <h1>จำนวนคงเหลือ</h1>
      </div>
      <div class="ticket">
        <h1>{{ticket}} ใบ</h1>
      </div>
    <div class="button">
      <button @click="addTicket()">
          Admin
        </button>
    </div>
    </div>
  </div>
</template>

<script>
import {mapActions,mapGetters} from 'vuex';

export default {
  name: 'About',
  data(){
    return{
      fristT:'',
      eco:''
    }
  },
  computed:{
    ...mapGetters({
      ticket: 'ticket'
    }),
    
    
  },
  methods: {
    ...mapActions({
      getTicketFromStore: 'getTicketFromStore'
    }),
    goToHome(){
      this.$router.push('/')
    },
    addTicket(){
      var person = prompt("ID", "Admin");
      if (person == "Admin") {
        var add = prompt("จำนวนที่ต้องการเพิ่ม ");
        let ticketLeft = this.ticket
        ticketLeft = Number(this.ticket) + Number(add) 
        this.getTicketFromStore(ticketLeft)
        
      }
    }


  }
}
</script>>
<style>
  .about {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
  }
  .form{
    width: 450px;
    height: 300px;
    background-color: aliceblue;
    box-shadow: 1px 1px 25px 2px #888888;
    text-align: center;
  }.title{
    margin-top: 50px;
    
  }.ticket {
    margin-top: 60px;
  }
  .link {
    margin-top: 50px;
    margin-right: 10px;
    text-align: right;
    text-decoration: underline;
    cursor: pointer;
  }
  .button{
    margin-top: 10%;
  }
  button{
    outline: none;
    cursor: pointer;
    border: 1px solid black;
    border-radius: 5%;
    padding: 10px 40%;
  }
</style>