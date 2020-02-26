<template>
  <div class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-title>Ion Select Issue</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <h1>Testing ion-select selected values</h1>
      <p>
        Example from
        <a href="https://ionicframework.com/docs/api/select#properties">
          documentation
        </a>
      </p>
      <ion-list class="ion-margin-top">
        <ion-item>
          <ion-label>Pets</ion-label>
                                            <!-- try setting defaultValues -->
          <ion-select id="my-select" multiple="true" :value="['bird', 'dog']">
            <ion-select-option value="bird">Bird</ion-select-option>
            <ion-select-option value="cat">Cat</ion-select-option>
            <ion-select-option value="dog">Dog</ion-select-option>
            <ion-select-option value="honeybadger">Honey Badger</ion-select-option>
          </ion-select>
        </ion-item>
      </ion-list>
      <ion-button @click="forceCheckingValues">
        Force Checking defaults
      </ion-button>
    </ion-content>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  data () {
    return {
      defaultValues: ['cat', 'dog'] // not working when bind this value to ion-select
    }
  },
  async mounted () {
    // not working when setting defaultValues to ion-select on mounted
    this.$set(this.$data, 'defaultValues', ['bird', 'honeybadger'])

    // uncomment the working example
    // await this.forceCheckingValues()
  },
  methods: {
    async forceCheckingValues () {
      const select = await document.querySelector('#my-select')
      if (select) {
        window.console.info('select input is ready')
      }
      select.value = ['bird', 'dog']
    }
  }
}
</script>
