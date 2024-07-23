<template>
  <li>
    <p>
      <span class="highlight">{{ name }}</span> chose
      <span :class="clubClass">{{ club }} Club</span>.
       Email:<span class="email">{{ email }}</span>
    </p>
  </li>
</template>

<script>
export default {
  props: ['name', 'club','email'],
  computed: {
    clubClass() {
      return 'highlight club--' + this.club;
    },
  },
};
</script>

<style scoped>
li {
  margin: 1rem 0;
  border: 1px solid #ccc;
  padding: 1rem;
}

h3,
p {
  font-size: 1rem;
  margin: 0.5rem 0;
}

.highlight {
  font-weight: bold;
}

.club--football {
  color: #b80056;
}

.club--swimming {
  color: #330075;
}
.email{
  color: red;
}

</style>