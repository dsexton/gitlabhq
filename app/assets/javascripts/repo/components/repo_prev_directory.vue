<script>
  import eventHub from '../event_hub';
  import repoMixin from '../mixins/repo_mixin';

  export default {
    mixins: [
      repoMixin,
    ],
    props: {
      prevUrl: {
        type: String,
        required: true,
      },
    },
    computed: {
      colSpanCondition() {
        return this.isMini ? undefined : 3;
      },
    },
    methods: {
      linkClicked(file) {
        eventHub.$emit('goToPreviousDirectoryClicked', file);
      },
    },
  };
</script>

<template>
  <tr class="file prev-directory">
    <td
      :colspan="colSpanCondition"
      class="table-cell"
      @click.prevent="linkClicked(prevUrl)"
    >
      <a :href="prevUrl">...</a>
    </td>
  </tr>
</template>
