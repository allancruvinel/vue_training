<template>
  <div class="tile">
    <div class="tile-icon">
      <div>
        <i class="icon icon-time centered"></i>
      </div>
    </div>
    <div class="tile-content">
      <p class="tiles-subtitle">{{ todo.frase }}</p>
      <div>{{todo.checked}}</div>
    </div>
    <div class="tile-action">
      <button @click="$emit('toogle',todo)" class="btn btn-link">Concluir</button>
      <button class="btn btn-link">
        <span class="text-error">Remover</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: { todo: { type: Object, required: true } },
};
</script>