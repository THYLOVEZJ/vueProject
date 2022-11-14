<template>
    <div class="container">
      <div class="card">
      <div class="card-body">
        <!--slot可以读取外面的值-->
        <slot></slot>
      </div>  
    </div>
    </div>
</template>

<style scope>
.container{
    margin-top: 20px;
}
</style>

<script>
    export default{
        name:"ContentBase",
    }
</script>