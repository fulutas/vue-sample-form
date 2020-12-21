<template>
  <div>
     <div style="margin-top:20px;">Açık/Kapalı</div>
    <label id="on" @click="switched(true)" :class="{ active: value }">Açık</label>
    <label id="off" @click="switched(false)" :class="{ active: !value }">Kapalı</label>
  </div>
</template>
<script>
export default {

    props : ["value"],
    methods : {
        switched(isOn){
             this.$emit("input", isOn);
        }
    }
    
};
</script>

<style scoped>

#off {
    width: 50px;
    height: 20px;
    padding: 5px;
    display: inline-block;
    margin: 10px -1px;
    box-sizing: content-box;
    cursor: pointer;
    text-align: center;
}

#off.active {
    background-color: tomato;
    color:white;
}

#on {
    width: 50px;
    height: 20px;
    padding: 5px;
    display: inline-block;
    margin: 10px -1px;
    box-sizing: content-box;
    cursor: pointer;
    text-align: center;
    background-color: peru;
    color: white;
}

#on.active {
    background-color: maroon;
    color: white;
}






</style>