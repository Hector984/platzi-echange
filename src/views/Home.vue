<template>
    <div>
      <bounce-loader v-bind:loading="isLoading" v-bind:color="'#68d391'" v-bind:size="100"></bounce-loader>
        <px-assets-table v-if="!isLoading" v-bind:assets="assets"></px-assets-table>
    </div>
</template>

<script>
import PxAssetsTable from '@/components/PxAssetsTable';
import api from '@/api';

export default {
  name: 'PxHome',
  components: {
    PxAssetsTable,
  },

  data(){
    return {
      assets: [],
      isLoading: false
    }
  },

  created(){
    this.isLoading = true;
    api.getAssets()
    .then(assets => (this.assets = assets))
    .finally(() => this.isLoading = false);
  }
}
</script>
