<template>
  <div class="havadurumu">
    <div class="ikili_flex">
      <div>
        <div class="konum">
          <h2>
            <!-- {weather.weather.name.toUpperCase()} -->
            ÇANAKKALE
          </h2>
        </div>
        <div class="tarih">
          {new Date(weather.dt * 1000).toLocaleDateString()}
          31.03.2023
        </div>
        <br />
        <div class="derece">
          <!-- {weather.main.temp.toFixed(0)} -->
          15°
        </div>
      </div>
      <div class="aciklama">
        <!-- <h3>{weather.weather.map((data) => data.description).join(",")}</h3> -->
        açık
      </div>
    </div>

    <!-- <div className="icon">
          <p id="yagmur" className="rain">
            {icon === "Rain" && (
              <WiHail style={{ color: "white", marginTop: "0px" }} size={90} />
            )}
          </p>
          <p>
            {icon === "Drizzle" && (
              <WiHail style={{ color: "white" }} size={90} />
            )}
          </p>
          <p id="kar">
            {icon === "Snow" && (
              <WiSnowWind style={{ color: "white" }} size={90} />
            )}
          </p>
          <p>
            {icon === "Clouds" && (
              <WiDayCloudyHigh style={{ color: "white" }} size={90} />
            )}
          </p>
          <p>
            {icon === "Clear" && (
              <WiDaySunny style={{ color: "white" }} size={90} />
            )}
          </p>
          <p>
            {icon === "Thunderstorm" && (
              <WiNightThunderstorm style={{ color: "white" }} size={90} />
            )}
          </p>
        </div> -->
    <div class="gorsel">
      <div class="nem">
        <!-- {{weather.weather[0].main.humidity}} -->
        25% <br />
        Nem
      </div>
      <div class="rüzgar">
        <!-- {weather.wind.speed} -->
        12km
        <br />
        Rüzgar
      </div>
      <div class="basinc">
        700
        <!-- {weather.main.pressure} -->
        <br />
        Basınç
      </div>
    </div>
    <!-- {/* <Arama data_={data_} setData_={setData_} />
        <Sonuc data_={data_} /> */} -->
  </div>
</template>

// <script>
import axios from "axios";

export default {
  data() {
    return {
      weather: [],
      errors: [],
      enlem: 40.1467,
      boylam:26.4086
    };
  },

  created() {
    this.getWeatherInfo()
  },

  methods: {
    getWeatherInfo() {
      axios
        .get(
          `https://api.openweathermap.org/data/2.5/weather?lat=${this.enlem}&lon=${this.boylam}&appid=c544de50d68a25ff466bd1b84a4a8604&units=metric`
        )
        .then((response) => {
          this.weather = response.data;

          console.log("burdayım",this.weather)
        })
        .catch((e) => {
          this.errors.push(e);
        });
        
    },
  },
};
</script>



<style>
.havadurumu {
  background-color: rgb(12, 12, 131);
  background-repeat: no-repeat;
  background-size: cover;
  opacity: 0.8;
  border-radius: 20px;
  background-size: 100% 100%;
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: left;
  padding-left: 10px;
  padding-right: 10px;
  font-family: "Times New Roman", Times, serif;
  width: 18%;
  height: 530px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 4rem;
  border-radius: 20px;
}

.konum {
  font-size: small;
  font-weight: lighter; /*daha ince normal değere göre*/
  font-family: "Varela Round";
  opacity: 0.9;
}

.tarih {
  font-family: Comfortaa;
}

.derece {
  font-size: 140px;
  font-family: Rubik;
}
.ikili_flex {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}

.gorsel {
  display: flex;
  justify-content: space-around;
  margin-top: 12rem;
  align-items: center;
  font-size: small;
  font-family: cursive;
  border-style: solid;
  border-width: 3px;
  padding: 0.5rem;
  border-radius: 15px;
}
.nem {
  width: 50%;
  text-align: center;
}
.rüzgar {
  width: 50%;
}
.basinc {
  width: 50%;
}

.aciklama {
  font-family: Comfortaa;
  font-size: small;
  margin-bottom: 0px;
  padding-bottom: 0px;
  writing-mode: vertical-rl;
  text-orientation: mixed;
  color: white;
  width: fit-content;
  margin-top: 50px;
  opacity: 0.8;
}

/* .dunya {
  width: 120px;
  height: 120px;
  background-color: aquamarine;
  border-radius: 50%;
  overflow: hidden;
  position: absolute;
  right: 540px;
  margin-top: 20px;
} */

/* 
.dunyaHarita {
  background: url("C:\Users\sumey\Desktop\dunya.jpg");
  width: 120px;
  height: 120px;
  background-size: cover;
  animation: donus 15s linear 0s infinite;
}
@keyframes donus {
  from {
  }
  to {
    background-position: -100px 0;
  }
}
#animasyon {
  border-style: solid;
  border-width: 1px;
  color: white;
  border-radius: 5px;
  width: 100px;
  height: 200px;
  position: absolute;
  right: 550px;
  margin-top: 160px;
 
} */

/* .rain {
  background-image: linear-gradient(white 1px, transparent 1px), url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='10' viewBox='0 0 10 10'%3E%3Cpath d='M0 10L10 0' stroke='%23000' stroke-width='2'/%3E%3C/svg%3E");
  background-repeat: repeat-y;
  animation: rain 10s linear infinite;
} */

/* @keyframes rain {
  0% {
    background-position: 0px 0px;
  }
  100% {
    background-position: 0px 100px;
  }
} */
</style>