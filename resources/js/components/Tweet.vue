<template>
  <div v-if="item" class="col">
    <nav class="panel panel-default">
      <div class="list-group">
        <RouterLink
          class="tweet__overlay"
          :to="`/users/${item.owner.id}`"
          :title="`View the user detail`"
          :item="item.owner"
        >
          <div class="list-group-item">
            <span class="name">
              {{ item.owner.name }}さん
            </span>
          </div>
        </RouterLink>
        <RouterLink
          class="tweet__overlay"
          :to="`/tweets/${item.id}`"
          :title="`View the tweet by ${item.owner.name}`"
        >
          <div class="list-group-item">
            <span class="text">
              {{ item.text }}
            </span>
          </div>
        </RouterLink>
        <div class="tweet__controls">
          <button
            class="tweet__action tweet__action--like"
            title="Like tweet"
          >
            <i class="icon ion-md-heart"></i>12
          </button>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true
    },
  }
}
</script>

<style scoped>
  .name {
    color: #434a54;
  }
  .name:hover {
    text-decoration: underline;
  }
  .text {
    color: #434a54;
  }
  .tweet__controls {
    text-align: right;
  }
  .tweet__action {
    background: #fff;
    border: 0;
    border-radius: .25rem;
    color: #222;
    cursor: pointer;
    display: inline-block;
    font-size: 1rem;
    line-height: 1;
    margin-left: .25rem;
    opacity: .8;
    outline: none;
    padding: .5em .75em;
  }
  .tweet--like .icon {
    color: #e4406f;
    margin-right: .5em;
  }
</style>