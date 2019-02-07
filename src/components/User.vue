<template>
  <div class="hello">
    
     Nama      : Judz'an Hazim P<br>
     Kelas     : XII RPL 2<br>
     Nis       : 1617116717       
     {{firstName}}
     {{lastName}}
  </div>
</template>

<script>
export default {
	name : "User",
	props: [
		'firstName',
		'lastName'
	]	
}
</script>

<style scoped>

</style>
