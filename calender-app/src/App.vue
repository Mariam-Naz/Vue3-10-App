<template>
  <div class="m-auto w-96">
    <h1  class='text-center text-3xl my-4 mt-11'>Vue Calender</h1>
  
    <section class='flex justify-between py-2'>
      <h2 class='font-bold text-xl'>{{currentMonthName}}</h2>
      <h2 class='font-bold text-xl'>{{currentYear}}</h2>
    </section>
    <section class='flex'>
      <p class='text-center' v-for='day in days' :key="day" style='width:14.28%;'>{{day}}</p>
    </section>
    <section class='flex flex-wrap'>
       <p class='text-center' style='width:14.28%;' v-for="num in startDay(currentYear , currentMonth )" :key='num'></p>
      <p class='text-center' style='width:14.28%;' v-for="num in daysInMonths(currentYear , currentMonth )" :key='num'>{{num}}</p>
      
    </section>

    <!-- BUTTON NEXT AND PREV -->
    <section class='flex justify-between'>
      <button>Prev</button>
      <button>Next</button>
    </section>
  </div>
</template>

<script>
export default {
    data(){
      return{
        days:["Sun" ,"Mon" ,"Tues" ,"Wed" ,"Thurs" , "Fri" ,"Sat"],
        currentMonth: new Date().getMonth()+1,
        currentMonthName: new Date().toLocaleString('Defualt' , {month:'long'}),
        currentYear: new Date().getFullYear(),
      }
    },

    methods:{
      daysInMonths(year, month){
        return new Date(year, month, 0).getDate();
       },

       startDay(year,month){
         return new Date(year, month-1).getDay();
       }
    }
}
</script>

<style>

</style>