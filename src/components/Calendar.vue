<template>
  <div class="m-auto bg-gray-200 rounded-xl p-8">
      <h1 class="text-2xl my-2 text-center font-bold">Vue Calendar - {{ currentYear }}</h1>      
      <section class="mx-2 flex justify-between">         
        <h2 class="font-bold"> {{ currentMonthName }}</h2>
        <h2 class="font-bold"> {{ currentYear }}</h2>
      </section>
      
        <section class="flex my-2">
            <p 
                class="text-center" 
                style="width:14.28%" 
                v-for="day in days" 
                :key="day"
                >
                    {{ day }}
            </p>
        </section>
        <section class="flex flex-wrap">
            <p 
                class="text-center" 
                style="width:14.28%" 
                v-for="num in startDay()" 
                :key="num"
            >                
            </p>
            <p 
                class="text-center" 
                style="width:14.28%" 
                v-for="num in daysInMonth()" 
                :key="num"
                :class="currentDayClass(num)"
            > 
                {{ num }}
            </p>
          
        </section>
        <section class="flex justify-between my-4">
            <button class="px-2 border rounded bg-green-600 text-white" @click="prev">Prev</button>
            <button class="px-2 border rounded bg-green-600 text-white" @click="next">Next</button>
        </section>
  </div>
</template>

<script>
export default {
    data() {
        return{
            currentMonth: new Date().getMonth(),
            // currentMonthName: new Date().toLocaleString("default", { month: "long" }),            
            currentYear: new Date().getFullYear(),
            days: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'],

        }
    },
    methods: {
        daysInMonth() {
            return new Date(this.currentYear, this.currentMonth+1, 0).getDate();
        },
        startDay() {
            return new Date(this.currentYear, this.currentMonth, 1).getDay();
        },
        next() {
            if(this.currentMonth == 11) {
                this.currentMonth = 0;
                this.currentYear++;
            } else {
                this.currentMonth++;
            }            
        },
        prev() {
            if(this.currentMonth == 0) {
                this.currentMonth = 11;
                this.currentYear--;
            } else {
                this.currentMonth--;
            } 
        },
        currentDayClass(num) {
            const calendarFullDate = new Date(
                this.currentYear, 
                this.currentMonth, 
                num
            ).toDateString();
            const currentFullDate = new Date().toDateString();
            return  calendarFullDate === currentFullDate ? "text-yellow-600 font-bold" : "";
        },
    },
    computed: {
        currentMonthName() {
            return new Date(
                this.currentYear, 
                this.currentMonth
            ).toLocaleString("default", { month: "long" });
        },
    },
}
</script>

<style>

</style>