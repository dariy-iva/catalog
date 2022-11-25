<template>
  <form
    name="subscription"
    @submit.prevent="handleSubmitForm"
    @reset.prevent="handleResetForm"
    class="form-subscription">
    <label class="form-subscription__label">
      <input
        type="email"
        name="email"
        v-model="emailValue"
        @change="handleEmailChange"
        placeholder="Адрес электронной почты"
        required
        class="form-subscription__input form-subscription__text"
      />

      <span class="form-subscription__error">{{emailErrorText}}</span>

      <button
        type="reset"
        aria-label="очистить"
        class="form-subscription__reset"
      />
    </label>

    <button
      type="submit"
      :disabled="!isValidForm"
      aria-label="подписка"
      class="form-subscription__submit form-subscription__text">
      Подписаться
    </button>
  </form>
</template>

<script>
export default {
  name: "SubscriptionForm",

  data() {
    return {
      emailValue: '',
      emailErrorText: '',
      isValidForm: false,
    }
  },

  methods: {
    handleEmailChange(e) {
      this.emailErrorText = e.target.validationMessage;
      this.isValidForm = e.target.closest("form").checkValidity();
    },

    handleResetForm() {
      this.emailValue = '';
      this.emailErrorText = '';
      this.isValidForm = false;
    },

    handleSubmitForm() {
      this.handleResetForm();
    }
  }
}
</script>

<style scoped>
.form-subscription {
  display: flex;
  flex-direction: column;
  gap: 35px;
}

.form-subscription__label {
  position: relative;
  display: flex;
  width: 100%;
}

.form-subscription__text {
  font-weight: 400;
  font-size: 14px;
  line-height: 1.43;
  letter-spacing: .04em;
}

.form-subscription__input {
  padding: 12px 32px 12px 16px;
  min-width: 100%;
  box-sizing: border-box;
  border-bottom: 1px solid var(--light-gray-color);
  border-top: none;
  border-left: none;
  border-right: none;
  outline: none;
  color: var(--brand-black-color);
  transition: border-bottom-color .3s;
}

.form-subscription__input:focus {
  border-bottom-color: var(--dark-gray-color);
}

.form-subscription__input:invalid:not(:focus):not(:placeholder-shown) {
  border-bottom-color: var(--red-color);
}

.form-subscription__input::placeholder {
  color: var(--dark-gray-color);
}

.form-subscription__error {
  position: absolute;
  top: 100%;
  left: 0;
  font-weight: 400;
  font-size: 12px;
  line-height: 1;
  color: var(--red-color);
}

.form-subscription__reset {
  position: absolute;
  top: calc(50% - 8px);
  right: 8px;
  width: 16px;
  height: 16px;
  border: none;
  mask-size: 8.5px 8.4px;
  -webkit-mask-size: 8.5px 8.4px;
  mask-position: center;
  -webkit-mask-position: center;
  mask-repeat: no-repeat;
  -webkit-mask-repeat: no-repeat;
  mask-image: url("static/images/icons/close.svg");
  -webkit-mask-image: url("static/images/icons/close.svg");
  background-color: var(--light-gray-color);
  cursor: pointer;
  transition: background-color .3s;
}

.form-subscription__reset:hover {
  background-color: var(--brand-black-color);
}

.form-subscription__submit {
  padding: 8px 28px;
  align-self: end;
  width: max-content;
  color: var(--brand-black-color);
  background: none;
  outline: 1px solid var(--brand-black-color);
  border: none;
  box-sizing: border-box;
  transition: color .3s, background-color .3s;
}

.form-subscription__submit:not(:disabled):hover {
  cursor: pointer;
  color: var(--white-color);
  background-color: var(--yellow-color);
  outline: none;
}
</style>
