<template>
	<form @submit.prevent="submitData">
		<div>
			<label> Name</label>
			<input type="text" v-model="enteredName" placeholder="User Name" />
		</div>
		<div>
			<label>E-mail</label>
			<input type="email" v-model="enteredEmail" placeholder="E-mail" />
		</div>
		<div>
			<label>Phone:</label>
			<input type="tel" v-model="enteredPhone" placeholder="Phone Number" />
		</div>
		<div>
			<label>Is Favorite</label>
			<input type="checkbox" v-model="favPeo" checked />
		</div>
		<div>
			<button :disabled="isFormIncomplete">Add Contact</button>
		</div>
	</form>
</template>

<script>
export default {
	emits: ['add-contact'],
	data() {
		return {
			enteredName: '',
			enteredPhone: '',
			enteredEmail: '',
			favPeo: false,
		};
	},
  computed: {
    isFormIncomplete() {
      console.log(  this.enteredName === '' ||
        this.enteredEmail === '' ||
        this.enteredPhone === '')
      return (
        this.enteredName.trim() === '' ||
        this.enteredEmail.trim() === '' ||
        this.enteredPhone.trim() === ''
      );

    },
  },
	methods: {
		submitData() {
			this.$emit(
				'add-contact',
				this.enteredName,
				this.enteredEmail,
				this.enteredPhone,
				this.favPeo
			);
		},
	},
};
</script>

<style></style>
