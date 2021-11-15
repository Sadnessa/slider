<template>
    <div class=mycard>
        <slot></slot>
    </div>
</template>

<style lang="scss" scoped>
.mycard {
    width: 100%;
     height: 100%;
      display: flex;
     justify-content: center; 
     align-items: center;
    background-color: rgb(180, 179, 179);
    box-shadow: -1px -1px 15px 2px rgba(34, 60, 80, 0.2);
}

</style>