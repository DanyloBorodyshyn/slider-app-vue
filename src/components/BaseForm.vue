<script lang="ts" setup>
//@ts-ignore
import { computed } from "vue";
//@ts-ignore
import { vMaska } from "maska/vue";
import { useFormData } from "../composable/useFormData";

import BaseInput from "../components/BaseInput.vue";
import BaseRadioButton from "./BaseRadioButton.vue";
import BaseTextarea from "../components/BaseTextarea.vue";

const {
  form,
  isValidName,
  isValidSurname,
  isValidEmail,
  isValidSubject,
  isValidРhone,
  isValidAddress,
  isValidMessage,
  isValidCountry,
  isValidCity,
  errorsMessage,
} = useFormData();

const getErrors = computed(() => {
  const values = [
    isValidName.value,
    isValidSurname.value,
    isValidEmail.value,
    isValidSubject.value,
    isValidРhone.value,
    isValidAddress.value,
    isValidMessage.value,
    isValidCountry.value,
    isValidCity.value,
  ].map((el) => {
    const error = el.errors();
    if (error) {
        //@ts-ignore
      errorsMessage.value[el.alias] = error;
      return false;
    }

    return true;
  });

  return values.every((el) => Boolean(el));
});

const sendData = () => {
  errorsMessage.value = {};
  const invalid = getErrors.value;

  if (invalid) {
    errorsMessage.value = {};

    setTimeout(() => {
      alert("відправлено");
    }, 500);
  }
};
</script>

<template>
  <div class="form">
    <form class="form-content" @submit.prevent="sendData">
      <div class="form-content__field">
        <div class="form-content__title">ПРЕДСТАВТЕСЯ, БУДЬ ЛАСКА</div>
        <div class="form-content__item">
          <BaseInput
            label="*ПРІЗВИЩЕ"
            v-model="form.name"
            :message="errorsMessage.name"
          />
        </div>
        <div class="form-content__lower">
          <BaseInput
            label="* ІМ’Я"
            v-model="form.surname"
            :message="errorsMessage.surname"
          />
        </div>
        <div class="form-content__higher">
          <BaseInput
            v-model="form.position"
            :message="errorsMessage.position"
            label="Організа́ція ТА ПОСАДА"
          />
        </div>
        <div class="form-content__item radio">
          <BaseRadioButton
            label="СПОЖИВАЧ"
            v-model="form.role"
            value="customer"
            name="radio-role"
          />
        </div>
        <div class="form-content__item radio">
          <BaseRadioButton
            label="МЕДИЧНИЙ ПРАЦІВНИК"
            v-model="form.role"
            value="medic"
            name="radio-role"
          />
        </div>
        <div class="form-content__item radio">
          <BaseRadioButton
            label="ЖурналІст"
            v-model="form.role"
            value="journalist"
            name="radio-role"
          />
        </div>
        <div class="form-content__item">
          <div class="form-content__caption">ПОВІДОМЛЕННЯ</div>
        </div>
        <div class="form-content__item">
          <BaseInput label="Тема ПОВІДОМЛЕННЯ" />
        </div>
        <div class="form-content__item">
          <BaseTextarea
            label="* ПОВІДОМЛЕННЯ"
            v-model="form.subject"
            :message="errorsMessage.subject"
          />
        </div>
      </div>
      <div class="form-content__field">
        <div class="form-content__title">Контактна Інформація</div>

        <div class="form-content__item">
          <BaseInput
            label="* Email"
            v-model="form.email"
            :message="errorsMessage.email"
          />
        </div>
        <div class="form-content__item">
          <BaseInput
            v-model="form.country"
            :message="errorsMessage.country"
            label="КРАЇНА"
          />
        </div>
        <div class="form-content__item">
          <BaseInput
            v-model="form.city"
            :message="errorsMessage.city"
            label="МІСТО"
          />
        </div>
        <div class="form-content__item">
          <BaseInput
            v-model="form.index"
            :message="errorsMessage.index"
            type="number"
            label="ІНДЕКС"
          />
        </div>
        <div class="form-content__item">
          <BaseInput
            v-model="form.address"
            :message="errorsMessage.address"
            label="АдресА"
          />
        </div>
        <div class="form-content__item">
          <BaseInput
            v-maska="'+(38) ###-##-###-##'"
            placeholder="(__) ___-__-___-__"
            v-model="form.phone"
            :message="errorsMessage.phone"
            label="* Телефон"
          />
        </div>

        <button class="form-content__submit" type="submit">відправити</button>
      </div>
    </form>
  </div>
</template>

<style lang="scss">
.form-content__title{
    text-transform: uppercase;
}
.form {
  max-width: 700px;
  margin: 0 auto;
}
.form-content {
  display: flex;
  gap: 32px;

  @media (max-width: 767px) {
    flex-direction: column;
    gap: 24px;
  }

  & > div {
    width: 50%;

    @media (max-width: 767px) {
      width: 100%;
    }
  }

  &__title {
    margin-bottom: 50px;
    font-size: 18px;
    color: #000;

    @media (max-width: 767px) {
      margin-bottom: 24px;
    }
  }

  &__item {
    & + & {
      margin-top: 16px;
    }
  }

  &__item.radio{
    & + & {
      margin-top: 10px;
    }
  }

  &__lower {
    margin-top: 10px;
  }
  &__higher {
    margin-top: 16px;
    margin-bottom: 14px;
  }

  &__caption {
    font-size: 18px;
  }

  &__field {
    display: flex;
    flex-direction: column;
  }

  &__submit {
    margin-top: auto;
    width: 100%;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    padding: 12px 0;
    font-size: 22px;
    background: #464646;
    color: #fff;
    border: none;
    cursor: pointer;

    &:hover {
      filter: brightness(110%);
    }

    @media (max-width: 767px) {
      margin-top: 16px;
    }
  }
}
</style>
