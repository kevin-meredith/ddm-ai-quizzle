<template>
  <div id="app">
    <b-container fluid>
      <b-row>
        <b-col
          cols="12"
          md="6"
        >
          <div class="header">
            <h1>DDM AI Quizzle</h1>
  
            <div class="text text--question">
              <h4>User question:</h4>
              <div class="text__box">
                <p>{{ displayQuestion }}</p>
              </div>
            </div>
          </div>

          <b-form
            ref="quizzleForm"
            class="form"
            @submit="onSubmit"
          >
            <b-form-group
              id="input-group-1"
              label="Ask a question:"
              label-for="input-1"
            >
              <b-form-input
                id="input-1"
                v-model="form.query"
                type="text"
                placeholder="Start the conversation"
                required
              ></b-form-input>
            </b-form-group>
            <b-button
              type="submit"
              variant="outline-light"
            >
              Submit
            </b-button>
          </b-form>
        </b-col>

        <b-col
          cols="12"
          md="6"
        >
          <div class="text text--answer">
            <h4>AI response:</h4>
            <div class="text__box">
              <div
                v-if="isLoading"
                class="spinner"
              >
                <b-spinner
                  type="grow"
                  label=""
                ></b-spinner>
              </div>
              <p
                v-else
              >
                I'm baby tacos bespoke typewriter keytar next level disrupt. 8-bit tattooed scenester ugh, palo santo pickled small batch jean shorts gorpcore pabst microdosing letterpress selvage. Brunch pop-up tbh hot chicken. Selvage synth pug, trust fund palo santo hoodie green juice asymmetrical flannel gentrify. Activated charcoal schlitz photo booth artisan air plant live-edge blue bottle banjo brunch fit poutine raclette. Post-ironic ramps grailed, palo santo etsy pour-over hell of gentrify beard art party yes plz chillwave fit. Photo booth sartorial jawn bruh beard schlitz microdosing biodiesel bespoke fingerstache hexagon.
            </p>
            </div>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        query: '',
      },
      isLoading: false,
      displayQuestion: '',
    }
  },
  methods: {
    onSubmit(event) {
      event.preventDefault()

      this.displayQuestion = this.form.query
      this.$refs.quizzleForm.reset()
    },
  }
}
</script>

<style scoped lang="scss">
h1,
h4 {
  font-weight: bold;
}

.row {
  overflow: hidden auto;
  height: 100vh;
}

.col-md-6 {
  overflow: hidden auto;
  max-height: 100vh;
  padding: 1.5rem;

  &:first-of-type {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    background-color: black;
    color: white;
  }
}

form {
  input {
    margin: 1rem 0;
  }
}

.spinner {
  display: flex;
  justify-content: center;
}
</style>
