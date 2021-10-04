<template>
   <div class="friend" > 
          <img :src="data.avatar" class="friend__img" />
          <h3 class="friend__name">{{data.name}}</h3>
        </div>
</template>

<script>
export default {
    name:"Card",
    props:{
        data:{
            type:Object,
            required: true,
        }
    }

}
</script>
