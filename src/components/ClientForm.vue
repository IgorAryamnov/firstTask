<template>
  <div>
    <div class="formContainer" style="background: white">
      <h1 class="header">Анкета</h1>
      <form>
        <div class="inputContainer">
          <label class="styledLabel" for="firstName">Имя:</label>
          <input
            v-model="firstName"
            class="styledInput"
            type="text"
            id="firstName"
          />
        </div>
        <p v-if="v$.firstName.$error" class="errorMessage">
          Пожалуйста, введите имя.
        </p>
        <div class="inputContainer">
          <label class="styledLabel" for="lastName">Фамилия:</label>
          <input
            v-model="lastName"
            class="styledInput"
            type="text"
            id="lastName"
          />
        </div>
        <p v-if="v$.lastName.$error" class="errorMessage">
          Пожалуйста, введите фамилию.
        </p>
        <div class="inputContainer">
          <label class="styledLabel" for="sname" id="sn">Отчество:</label>
          <input class="styledInput" type="text" id="sname" />
        </div>
        <div class="dobAndGenderContainer">
          <div>
            <div style="padding: 5px 0px 5px 0px" class="inputContainer">
              <label class="dobLabel" for="dob">Дата рождения:</label>
              <input v-model="dob" class="dobInput" type="text" id="dob" />
            </div>
            <p
              style="display: flex; align-items: center"
              v-if="v$.dob.$error"
              class="errorMessage"
            >
              Пожалуйста, введите дату рождения.
            </p>
          </div>
          <div style="padding: 5px 0px 5px 0px" class="inputContainer">
            <label style="margin-left: 10px" for="gender" id="gen">Пол:</label>
            <input class="genderInput" type="text" id="gender" />
          </div>
        </div>
        <div class="inputContainer">
          <label class="styledLabel" for="phoneNumber">Номер телефона:</label>
          <span class="firstNumber">+7</span>
          <input
            v-model="phoneNumber"
            class="numberInput"
            type="text"
            id="phoneNumber"
          />
        </div>
        <p v-if="v$.phoneNumber.$error" class="errorMessage">
          Пожалуйста, введите номер телефона.
        </p>
        <div class="selecterContainer">
          <div
            style="
              margin: 5px;
              display: flex;
              align-items: center;
              justify-content: center;
            "
          >
            <label
              style="margin: 10px 5px 10px 10px"
              for="client-select"
              class="clientSelect"
              >Группа клиентов:</label
            >
            <select
              class="styledSelect"
              v-model="clients"
              id="client-select"
              multiple
            >
              <option value="VIP">VIP</option>
              <option value="Проблемные">Проблемные</option>
              <option value="ОМС">ОМС</option>
            </select>
          </div>
          <div style="display: flex; align-items: center; margin: 5px">
            <label style="margin: 10px 5px 10px 10px" for="doctor-select">
              Лечащий врач:</label
            >
            <select class="styledSelect" name="doctors" id="doctor-select">
              <option value="">Выберите врача</option>
              <option value="Иванов">Иванов</option>
              <option value="Захаров">Захаров</option>
              <option value="Чернышева">Чернышева</option>
            </select>
          </div>
        </div>
        <p v-if="v$.clients.$error" class="errorMessage">
          Пожалуйста, укажите группу клиента
        </p>
        <div class="checkBoxConteiner">
          <input type="checkbox" id="sms" name="sms" />
          <label for="sms">Не отправлять СМС.</label>
        </div>
        <div>
          <div>
            <h2 style="margin: 10px">Адрес:</h2>
            <div>
              <div class="adressContainer">
                <label class="adressLabel notValidate" for="index"
                  >Индекс:</label
                >
                <input
                  class="adressInput"
                  type="text"
                  id="index"
                  name="index"
                />
                <label class="adressLabel notValidate" for="country"
                  >Страна:</label
                >
                <input
                  class="adressInput"
                  type="text"
                  id="country"
                  name="country"
                />
              </div>
              <div class="adressContainer">
                <label class="adressLabel notValidate" for="region"
                  >Область:</label
                >
                <input
                  class="adressInput"
                  type="text"
                  id="region"
                  name="region"
                />
                <label class="adressLabel" for="city">Город:</label>
                <input
                  v-model="city"
                  class="adressInput"
                  type="text"
                  id="city"
                  name="city"
                />
              </div>
              <p v-if="v$.city.$error" class="errorMessage">
                Пожалуйста, введите название города.
              </p>
              <div class="adressContainer">
                <label class="adressLabel notValidate" for="street"
                  >Улица:</label
                >
                <input
                  class="adressInput"
                  type="text"
                  id="street"
                  name="street"
                />
                <label class="adressLabel notValidate" for="house">Дом:</label>
                <input
                  class="adressInput"
                  type="text"
                  id="house"
                  name="house"
                />
              </div>
            </div>
          </div>
          <div>
            <h2 style="margin: 10px">Паспорт:</h2>
            <label class="pasportLabel" for="document-select">
              Тип документа:</label
            >
            <select
              class="styledSelect"
              style="margin: 5px"
              v-model="document"
              name="document"
              id="document-select"
            >
              <option value=""></option>
              <option value="Паспорт">Паспорт</option>
              <option value="Свидетельство о рождении">
                Свидетельство о рождении
              </option>
              <option value="Вод. удостоверение">Вод. удостоверение</option>
            </select>
            <p v-if="v$.document.$error" class="errorMessage">
              Пожалуйста, выберите тип документа.
            </p>
            <div class="pasportInputContainer">
              <label class="pasportLabel notValidate" for="Series"
                >Серия:</label
              >
              <input class="pasportImport" type="text" id="Series" />
            </div>
            <div class="pasportInputContainer">
              <label class="pasportLabel notValidate" for="number"
                >Номер:</label
              >
              <input class="pasportImport" type="text" id="number" />
            </div>
            <div class="pasportInputContainer">
              <label class="pasportLabel notValidate" for="issuedBy"
                >Кем выдан:</label
              >
              <input class="pasportImport" type="text" id="issuedBy" />
            </div>
            <div class="pasportInputContainer">
              <label class="pasportLabel" for="dateOfIssue">Дата выдачи:</label>
              <input
                v-model="dateOfIssue"
                class="pasportImport"
                type="text"
                id="dateOfIssue"
              />
            </div>
            <p v-if="v$.dateOfIssue.$error" class="errorMessage">
              Пожалуйста, введите дату выдачи.
            </p>
          </div>
        </div>
      </form>
      <div class="footer">
        <button class="submitButton" @click="submit">Отправить анкету</button>
      </div>
    </div>
  </div>
</template>

<script>
import { useVuelidate } from "@vuelidate/core";
import { required, integer, maxLength, minLength } from "@vuelidate/validators";

export default {
  setup() {
    return {
      v$: useVuelidate(),
    };
  },
  data() {
    return {
      firstName: "",
      lastName: "",
      dob: "",
      phoneNumber: "",
      clients: [],
      city: "",
      dateOfIssue: "",
      document: "",
    };
  },
  validations() {
    return {
      firstName: { required, $autoDirty: true },
      lastName: { required, $autoDirty: true },
      dob: { required, $autoDirty: true },
      phoneNumber: {
        required,
        $autoDirty: true,
        integer,
        maxLength: maxLength(10),
        minLength: minLength(10),
      },
      city: { required, $autoDirty: true },
      clients: { required, $autoDirty: true },
      dateOfIssue: { required, $autoDirty: true },
      document: { required, $autoDirty: true },
    };
  },

  name: "ClientForm",
  methods: {
    async submit() {
      const result = await this.v$.$validate();
      if (!result) {
        return;
      }
      return alert("Новый клиент успешно создан.");
    },
  },
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.formContainer {
  max-width: 1000px;
  min-width: 320px;
  border: 1px solid black;
  border-radius: 8px;
  margin: auto;
}

.styledSelect {
  border: 1px solid #d4d0d0;
  height: 25px;
  border-radius: 5px;
}
.styledSelect[multiple] {
  height: 55px;
}

.submitButton {
  height: 50px;
  width: 100px;
  border-radius: 40px;
  border: 1px solid rgb(39, 74, 190);
  background: #1677ff;
  color: white;
  outline: none;
}

.submitButton:hover {
  background: #3989f8;
}

.footer {
  height: 78px;
  border-radius: 0px 0px 8px 8px;
  background: #dad9de;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 10px;
}

.pasportInputContainer {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 5px;
}

.pasportLabel {
  max-width: 120px;
  width: 100%;
  text-align: end;
}

.dobAndGenderContainer {
  display: flex;
  justify-content: center;
  margin-left: 20px;
  padding: 0px 10px 0px 0px;
}

.selecterContainer {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
}

.checkBoxConteiner {
  padding: 10px 5px 10px 5px;
}

.adressContainer {
  display: flex;
  align-items: center;
  justify-content: center;
}

.inputContainer {
  padding: 5px 10px 5px 10px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.pasportImport {
  width: 100%;
  display: block;
  max-width: 300px;
  min-width: 100px;
  border: 1px solid white;
  border-radius: 4px;
  background: #f1f0f0;
  height: 25px;
}

.header {
  margin: 0px;
  padding: 21px 0px 21px 0px;
  border-radius: 8px 8px 0px 0px;
  background: #dad9de;
}

.errorMessage {
  color: red;
  margin: 0px;
}

.adressContainer {
  display: flex;
  align-items: center;
  justify-content: center;
}
@media screen and (max-width: 350px) {
  .adressContainer {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
  }
}

.adressInput {
  width: 100%;
  max-width: 150px;
  min-width: 50px;
  border: 1px solid white;
  border-radius: 4px;
  background: #f1f0f0;
  height: 25px;
  margin: 10px 5px 10px 0px;
}

.firstNumber {
  border: 1px solid #f1f0f0;
  height: 27px;
  border-radius: 4px 0 0 4px;
  display: flex;
  align-items: center;
  font-size: 15px;
  padding: 0px 2px 0px 2px;
}

.numberInput {
  width: 275.62px;
  border: 1px solid #f1f0f0;
  border-radius: 0 4px 4px 0;
  background: #f1f0f0;
  height: 25px;
  font-size: 15px;
}

.numberInput:hover {
  background: #dad7d7;
}

.numberInput:focus {
  outline: none;
  background: white;
  border: 1px solid #1677ff;
  border-radius: 0 4px 4px 0;
}

.styledLabel {
  width: 130px;
  text-align: end;
  margin-right: 5px;
}

.adressLabel {
  max-width: 75px;
  width: 100%;
  text-align: end;
  margin-right: 5px;
  margin-left: 5px;
}

.pasportLabel::before,
.adressLabel::before,
.styledLabel::before,
.dobLabel::before,
.clientSelect::before {
  color: rgb(219, 51, 51);
  content: "*";
}

.dobLabel {
  display: block;
  max-width: 150px;
}

.clientSelect {
  margin-left: 10px;
}

#sn::before,
#gen::before {
  display: none;
}

.notValidate::before {
  display: none;
}

.styledInput {
  width: 100%;
  display: block;
  max-width: 300px;
  min-width: 100px;
  border: 1px solid white;
  border-radius: 4px;
  background: #f1f0f0;
  height: 25px;
}

.genderInput {
  width: 100%;
  display: block;
  max-width: 100px;
  min-width: 25px;
  border: 1px solid white;
  border-radius: 4px;
  background: #f1f0f0;
  height: 25px;
}

.dobInput {
  width: 100%;
  display: block;
  max-width: 150px;
  min-width: 25px;
  border: 1px solid white;
  border-radius: 4px;
  background: #f1f0f0;
  height: 25px;
}

.pasportImport:hover,
.dobInput:hover,
.genderInput:hover,
.adressInput:hover,
.styledInput:hover {
  background: #dad7d7;
}

.pasportImport:focus,
.dobInput:focus,
.genderInput:focus,
.adressInput:focus,
.styledInput:focus {
  background: white;
  outline: none;
  border: 1px solid #1677ff;
}
</style>
