<template>
  <div class="tasks-progress">
    <span class="progress-value"> {{ progress }}% </span>
    <div class="progress-bar" :style="{ width: progress + '%' }"></div>
  </div>
</template>

<script>
export default {
  props: {
    progress: { type: Number, default: 0 },
  },
};
</script>

<style>
     .tasks-progress {
       position: relative;
       width: 80%;
       border: 1px solid #fff;
       color: #fff;
       border-radius: 8px;
       margin-bottom: 15px;
       display: flex;
       flex-direction: column;
       align-items: center;

}

       .progress-bar {
            position: absolute;
            border-radius: 8px;
            height: 100%;
            background-color: #4caf50;
            align-self: flex-start;
            /* align-self acima serve para começar 
            a barra do início corretamente. 
            */  
       }

       .progress-value {
           z-index: 1;
           /* z-index coloca o valor da porcentagem
           na frente da barra verde */
           font-size: 1.5rem;

       }
</style>