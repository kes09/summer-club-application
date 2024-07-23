<template>
  <section>
    <base-card>
      <h2> Sign Up</h2>
      <form @submit.prevent="submitSurvey">
        <div class="form-control">
          <label for="name">Your Name</label>
          <input type="text" id="name" name="name" v-model.trim="enteredName" />
        </div>
        <div class="form-control">
          <label for="email">Your Email</label>
          <input type="text" id="email" name="email" v-model.trim="enteredEmail" />
        </div>
        <h3>Choose one of them</h3>
        <div class="form-control">
          <input
           type="radio"
           id="chosen-football"
           value="football" 
           name="football" 
           v-model="chosenClub" />
          <label for="chosen-football">Football Club</label>
        </div>
        <div class="form-control">
          <input
            type="radio"
            id="chosen-swimming"
            value="swimming"
            name="swimming"
            v-model="chosenClub"
          />
          <label for="chosen-swimming">Swiming Club</label>
        </div>
        <p
          v-if="invalidInput"
        >One or more input fields are invalid. Please check your provided data.</p>
        <div>
          <base-button>Submit</base-button>
        </div>
      </form>
    </base-card>
  </section>
</template>

<script>
export default {
  data() {
    return {
      enteredName: '',
      enteredEmail:'',
      chosenClub: null,
      invalidInput: false,
    };
  },
  // emits: ['survey-submit'],
  methods: {
    submitSurvey() {
      if (this.enteredName === '' || this.enteredEmail === '' || !this.chosenClub) {
        this.invalidInput = true;
        return;
      }
      this.invalidInput = false;

      // this.$emit('survey-submit', {
      //   userName: this.enteredName,
      //   userEmail: this.enteredEmail,
      //   club: this.chosenClub,
      // });
      fetch('https://test-mode-1be41-default-rtdb.firebaseio.com/surveys.json',{
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          name: this.enteredName,
          email: this.enteredEmail,
          club: this.chosenClub,
        }),
      });
      alert("Submitted");
      this.enteredName = '';
      this.enteredEmail ='';
      this.chosenClub = null;
    },
  },
};
</script>

<style scoped>
.form-control {
  margin: 0.5rem 0;
}

input[type='text'] {
  display: block;
  width: 20rem;
  margin-top: 0.5rem;
}
</style>