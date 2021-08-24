<template>
  <div id="app">
    <div class="title">
      <h2>Zgłoszenie naprawy / serwisu auta</h2>
    </div>
    <main class="service">
      <form @submit.prevent="saveData">
        <div class="personReport">
          <label for="name">Imię zgłaszającego</label>
          <input
            type="text"
            placeholder="Imię zgłaszającego..."
            v-model="serviceName"
          />
          <label for="surname">Nazwisko zgłaszającego</label>
          <input
            type="text"
            placeholder="Nazwisko zgłaszającego..."
            v-model="serviceSurname"
          />
        </div>
        <div class="carInformations">
          <label for="brand">Marka samochodu</label>
          <input
            type="text"
            placeholder="Wpisz markę samochodu..."
            v-model="serviceBrand"
          />
          <label for="model">Model samochodu</label>
          <input
            type="text"
            placeholder="Wpisz model samochodu..."
            v-model="serviceModel"
          />
          <label for="carYear">Rok produkcji auta</label>
          <input
            type="text"
            placeholder="Wpisz rok produkcji auta..."
            v-model="serviceProductionYear"
          />
          <label for="fuel">Rodzaj paliwa</label>
          <select name="fuel" id="fuel" v-model="serviceFuel">
            <option value="" disabled selected
              >-- Wybierz rodzaj paliwa --</option
            >
            <option value="Benzyna">Benzyna</option>
            <option value="Diesel">Diesel</option>
            <option value="Hybryda">Hybryda</option>
            <option value="Elektryczny">Elektryczny</option>
            <option value="Benzyna + LPG">Benzyna + LPG</option>
          </select>
          <label for="vin">Numer VIN auta</label>
          <input
            type="text"
            placeholder="Wpisz numer VIN auta..."
            v-model="serviceVin"
          />
          <label for="miles">Aktualny stan licznika (przebieg)</label>
          <input
            type="text"
            placeholder="Wpisz przebieg auta..."
            v-model="serviceMiles"
          />
          <label for="plates">Numer rejestracyjny auta</label>
          <input
            type="text"
            placeholder="Wpisz numer rejestracjny auta..."
            v-model="servicePlate"
          />
          <label for="serviceDescription">Opis zgłoszenia</label>
          <textarea
            name="desc"
            id="desc"
            cols="30"
            rows="10"
            placeholder="Opisz czego dotyczy zgłoszenie..."
            v-model="serviceDescription"
          ></textarea>
        </div>
        <button class="sendServiceReport">
          Wyślij zgłoszenie
        </button>
      </form>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      serviceName: "",
      serviceSurname: "",
      serviceBrand: "",
      serviceModel: "",
      serviceProductionYear: "",
      serviceFuel: "",
      serviceVin: "",
      serviceMiles: "",
      servicePlate: "",
      serviceDescription: "",
    };
  },
  methods: {
    save() {
      let CarRepairAndService = {
        serviceName: this.serviceName,
        serviceSurname: this.serviceSurname,
        serviceBrand: this.serviceBrand,
        serviceModel: this.serviceModel,
        serviceProductionYear: this.serviceProductionYear,
        serviceFuel: this.serviceFuel,
        serviceVin: this.serviceVin,
        serviceMiles: this.serviceMiles,
        servicePlate: this.servicePlate,
        serviceDescription: this.serviceDescription,
      };
      this.coachViewContext.binding.set("value", CarRepairAndService);
      this.coachViewContext.trigger();
    },
    saveData() {
      const allInputs = document.querySelectorAll("input");
      const select = document.querySelector("select");
      const textArea = document.querySelector("textarea");
      if (
        this.serviceName !== "" &&
        this.serviceSurname !== "" &&
        this.serviceBrand !== "" &&
        this.serviceModel !== "" &&
        this.serviceProductionYear !== "" &&
        this.serviceFuel !== "" &&
        this.serviceVin !== "" &&
        this.serviceMiles !== "" &&
        this.servicePlate !== "" &&
        this.serviceDescription !== ""
      ) {
        this.save();
        (this.serviceName = ""),
          (this.serviceSurname = ""),
          (this.serviceBrand = ""),
          (this.serviceModel = ""),
          (this.serviceProductionYear = ""),
          (this.serviceFuel = ""),
          (this.serviceVin = ""),
          (this.serviceMiles = ""),
          (this.servicePlate = ""),
          (this.serviceDescription = "");
        textArea.classList.remove("active");
        select.classList.remove("active");
        allInputs.forEach((input) => {
          input.classList.remove("active");
        });
      } else {
        if (select.value === "") {
          select.classList.add("active");
        } else {
          select.classList.remove("active");
        }
        if (textArea.value === "") {
          textArea.classList.add("active");
        } else {
          textArea.classList.remove("active");
        }
        allInputs.forEach((input) => {
          if (input.value === "") {
            input.classList.add("active");
          } else {
            input.classList.remove("active");
          }
        });
      }
    },
  },
};
</script>

<style scoped>
@import "./styles/style.css";
</style>
