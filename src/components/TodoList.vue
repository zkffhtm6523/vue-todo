<template>
  <section>
    <transition-group name="list" tag="ul">
      <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
        <i class="checkBtn fas fa-check" aria-hidden="true"></i>
        {{ todoItem }}
        <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
          <i class="far fa-trash-alt" aria-hidden="true"></i>
        </span>
      </li>
    </transition-group>
  </section>
</template>

<script>
export default {
  props: ['propsdata'],
  methods:{
    removeTodo(todoItem, index){
      this.$emit('removeTodo', todoItem, index);
      // $emit API : $emit('이벤트 이름), 하위 컴포넌트에서 이벤트 발생 -> 상위 컴포넌트로 신호 전
    }
  }
}

</script>

<style scoped>
  .list-enter-active, .list-leave-active{
    transition: all 1s;
  }

  .list-enter, .list-leave-to{
    opacity: 0;
    transform: translateY(30px);
  }

  ul {
    list-style-type: none;
    padding-left: 0;
    margin: 0;
    text-align: left;
  }

  li {
   display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }

  .checkBtn{
    line-height: 45px;
    color: #62acde;
    margin-left: 5px;
  }

  .removeBtn{
    margin-left: auto;
    color: #de4343;
  }
</style>
