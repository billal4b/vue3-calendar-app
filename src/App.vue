<template>
<AppHeader/>

<div class="w-full flex"> 
  <Calendar/>
</div>
</template>

<script>
import AppHeader from './components/AppHeader';
import Calendar from './components/Calendar';
import './assets/tailwind.css';
export default {
  name: 'App',
  components: { AppHeader, Calendar },
}
</script>


