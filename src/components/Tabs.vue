<template>
    <ul class="nav nav-tabs">
        <li role="presentation" :class="{'active':tab.active}" v-for="tab in tablist" ><a href="#{{tab.name}}" aria-controls="{{tab.name}}" role="tab" data-toggle="tab">{{tab.title}}</a></li>
    </ul>
    <div class="tab-content">
        <slot></slot>
    </div>
</template>
<script>
    export default{
       data () {
          return {
            tablist: []
          }
      },
      ready(){
        this.$children.forEach(c=>{
            this.tablist.push({
                    "name": c.name,
                    "title": c.title,
                    "active": c.active
                });
        })
      }
  }
</script>
<style>
  .nav-tabs {
    background-color: #eeeeee;
    padding-top:5px;
    padding-left:5px;
    border: 1px solid #ddd;

  }

  .tab-content {
    color : #000000;
    background-color: #ffffff;
    padding : 5px 15px;
    margin-top: -1px;
    border: 1px solid #ddd;
  }
</style>
