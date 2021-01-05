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
    <section class='flex flex-wrap border h-48'>
       <p class='text-center' style='width:14.28%;' v-for="num in startDay()" :key='num'></p>
      <p class='text-center' 
      style='width:14.28%;' 
      v-for="num in daysInMonths()" 
      :key='num'
      :class="currentDate(num) ? 'border text-blue-500 font-bold' : '' "
     >
        {{num}}</p>
      
    </section>

    <!-- BUTTON NEXT AND PREV -->
    <section class='flex justify-between mt-2'>
      <button class='px-4 border rounded py-1 bg-blue-600 hover:bg-blue-700 focus:outline-none  text-white' @click="previous">Prev</button>
      <button class='px-4 border rounded py-1 bg-blue-600 hover:bg-blue-700 focus:outline-none text-white' @click="next">Next</button>
    </section>
  </div>
</template>

<script>

export default {
    
    data(){
      return{
        days:["Sun" ,"Mon" ,"Tues" ,"Wed" ,"Thurs" , "Fri" ,"Sat"],
        currentMonth: new Date().getMonth(),
        currentYear: new Date().getFullYear(),
      }
    },

    methods:{
      daysInMonths(){
        return new Date(this.currentYear, this.currentMonth, 0).getDate();
       },

       startDay(){
         return new Date(this.currentYear, this.currentMonth).getDay();
       },

       next(){
         if(this.currentMonth === 11){
           this.currentMonth =0;
           this.currentYear++;
         }else{
         this.currentMonth++;
         }
       },

        previous(){
          if(this.currentMonth === 0){
           this.currentMonth =11;
           this.currentYear--;
         }else{
         this.currentMonth--;
         }
       },

       currentDate(num){
        if(new Date(this.currentYear, this.currentMonth, num).toLocaleDateString()== new Date().toLocaleDateString())
        {
          return true;
        }else{
          return false;
        }
       }
    },

    computed: {
      currentMonthName(){
        return new Date(this.currentYear, this.currentMonth).toLocaleString('Defualt' , {month:'long'});
      },
    }, 
   
};
</script>

<style>

</style>