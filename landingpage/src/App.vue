<template>
  <div>
    <div class="container-fluid">
      <div class="container main">
        <div class="row">
          <div class="col-md-12">
            <!-- Menu -->
            <div class="menu-holder">
              <input type="checkbox" name="checkbox" id="check" />
              <label for="check" class="checkbtn">
                <img
                  src="@/assets/logo.png"
                  alt="hamburger icon logo "
                  class="icon-hamburger"
                  id="icon-open"
                />
                <img
                  src="@/assets/logo.png"
                  alt="hamburger icon logo "
                  class="icon-close"
                  id="icon-closed"
                />
              </label>
              <div class="logo">
                <a href="">
                  <img src="@/assets/logo.png" alt="logo" />
                </a>
              </div>
              <ul class="main-menu">
                <li>
                  <a href="http://195.154.113.18:8000/swagger/index.html" target="_blank"
                    >API Swagger</a
                  >
                </li>
                <li>
                  <a
                    href="https://github.com/Ismail-Mouyahada/NegosudAPI-Master"
                    target="_blank"
                    >Github</a
                  >
                </li>
                <li>
                  <a href="https://unexpected-salt-c05.notion.site/Documentation-de-l-API-Negosud-ASP-net-Core-7-45857da0a78a40adb691b77005d5fe18" target="_b
                  ">
                    Documentation
                  </a>
                </li>
                <li>
                  <a
                    href=""
                    @click.prevent="getData"
                    class="text-white bg-primary"
                    :id="APIstatus ? 'ledAPIStatusGreen' : 'ledAPIStatusRed'"
                    >Satut de l'API
                  </a>
                </li>
                <hr />
                <li class="d-none">
                  <a href="" class="btn right-btn-btn font-weight-bold pb-2"
                    >Se connecter</a
                  >
                </li>
                <li class="d-none">
                  <a href="" class="btn right-btn-btn font-weight-bold pb-2"
                    >S'inscrire</a
                  >
                </li>
              </ul>
              <ul class="right-btn">
                <li>
                  <a href="" class="btn right-btn-btn font-weight-bold pb-2"
                    >Se connecter</a
                  >
                </li>
                <li>
                  <a href="" class="btn right-btn-btn font-weight-bold pb-2"
                    >S'inscrire</a
                  >
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <!-- banner -->
      <section class="my-banner mt-3 d-flex justify-content-end" style="">
        <div class="container banner">
          <div class="row">
            <div class="col-md-7 banner-text">
              <h2 class="font-weight-bold">NegoSud REST API</h2>
              <p class="mt-4">
                Récupéz les données de notre API Rest, Nous ne nous pouvons pas boire un
                verre ici mais nous vous envoyerons une boutielle en HTTP .
              </p>
              <a
                href="http://195.154.113.18:8000/swagger/index.html"
                target="_blank"
                class="btn banner-btn text-white font-weight-bold mt-3"
                >Découverir l'API</a
              >
            </div>
            <div class="col-md-5 banner-img">
              <img
                src="@/assets/images/Cocktailbartender-bro.svg"
                alt="illustration"
                class="d-block mx-auto"
              />
            </div>
          </div>
        </div>
      </section>
      <!-- url link -->
      <!-- boost -->
      <section class="row">
        <div class="col-md-12 boost">
          <h1 class="text-center text-white font-weight-bold">
            Solutions Degitales Negosud
          </h1>
          <!-- eslint-disable-next-line vue/no-parsing-error -->
          <a
            href="https://github.com/Ismail-Mouyahada/Master-ASP.Net-Project/tree/main/appNegoSudWinForms/appNegoSudWinForms/bin/Debug/net7.0-windows"
            v-if="role"
            class="btn btn-lg banner-btn font-weight-bold text-white py-3 d-block mx-auto mt-4"
          >
            Télécharger Desktop Negosudversion essaie (1.0.0)
          </a>
          <button
            class="btn btn-lg banner-btn font-weight-bold text-white py-3 d-block mx-auto mt-4"
          >
            Site Internet
          </button>
        </div>
      </section>
      <!-- footer -->
      <section class="row footer">
        <div class="container-fluid">
          <div class="row">
            <div class="col-md-3">
              <img src="@/assets/logo.png" alt="logo" style="width: 15em" />
            </div>
            <div class="col-md-3 footer-two">
              <h6 class="font-weight-bold text-white mb-4">Général</h6>
              <ul>
                <li><a href="">Condtions d'utilisations</a></li>
                <li><a href="">Politique de confidentialité</a></li>
                <li><a href="">Supprissions des données</a></li>
              </ul>
            </div>
            <div class="col-md-3 footer-three">
              <h6 class="font-weight-bold text-white mb-4">Clients</h6>
              <ul>
                <li><a href="">Boutique</a></li>
                <li><a href="">Professionnel</a></li>
                <li><a href="">Particulier</a></li>
              </ul>
            </div>
            <div class="col-md-3 footer-four">
              <h6 class="font-weight-bold text-white mb-4">NegoSud</h6>
              <ul>
                <li><a href="">à propos</a></li>
                <li><a href="">Produits</a></li>
                <li><a href="">Categories</a></li>
                <li><a href="">Contact</a></li>
              </ul>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name:"bienvenue",
  data() {
    return {
      role: false,
      admin: false,
      APIstatus: true,
      activeIndex: false,
    };
  },
  methods: {
    getData() {
      var myHeaders = new Headers();
      myHeaders.append("Accept", "text/plain");

      var requestOptions = {
        method: "GET",
        headers: myHeaders,
        redirect: "follow",
      };

      fetch("http://195.154.113.18:8000/api/Produits", requestOptions)
        .then((response) => response.text())
        .then((result) => {
          if (result.length > 0) {
            this.APIstatus = true;
            alert("L'API Negosud est disponible !");
          }
        })
        .catch((error) => {
          this.APIstatus = false;
          alert("L'API Negosud est en panne ! :" + error);
        });
    },
  },
  mounted() {},
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Comfortaa", sans-serif !important;
}
.container-fluid {
  background-image: linear-gradient(338deg, #0000004a, #0000) !important;
}
.menu-holder .logo img {
  padding-top: 10px;
  float: left;
  width: 10em;
}

.menu-holder .logo {
  padding-top: 10px;
  float: left;
  width: fit-content;
}
.copyText {
  background: transparent !important;
}

#ledAPIStatusGreen {
  background-color: hsl(66, 81%, 46%) !important;
  height: 10px !important;
  width: 10px !important;
  border-radius: 20% !important;
}

#ledAPIStatusRed {
  background-color: hsl(19, 82%, 48%) !important;
  height: 10px !important;
  width: 10px !important;
  border-radius: 20% !important;
}

.ledAPIStatusOrange {
  background-color: hsl(46, 95%, 47%) !important;
  height: 10px !important;
  width: 10px !important;
  border-radius: 50% !important;
}

.active {
  background: hsl(260, 8%, 14%) !important;
}

.redBorder {
  border: 2px solid red;
}

.preloader {
  width: 30px;
  height: 30px;
  position: absolute;
  right: 0px;
  top: 10px;
  margin-right: 25px;
  border-top: 4px solid hsl(66, 81%, 46%);
  border-right: 4px solid hsl(260, 8%, 14%);
  border-bottom: 4px solid hsl(260, 8%, 14%);
  border-left: 4px solid hsl(260, 8%, 14%);
  border-radius: 50%;
  animation: roll 1s linear infinite;
}

@keyframes roll {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
}

.copyText:focus {
  border: none !important;
  box-shadow: none !important;
}

@media screen and (max-width: 600px) {
  .copyText {
    text-align: left !important;
    padding-left: 0;
  }
}
</style>
