<template>
  <ul class="list">
    <li class="list-item" v-for="comment in dataComments" :key="comment.id">
      <div>
        <p>
          <strong>{{ comment.email }}</strong>
        </p>
        <small>{{ comment.body }}</small>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  props: { dataComments: Array },
}
</script>
