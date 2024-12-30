<template>
  <div id="app">
    <h1>App Vue.js</h1>
    <!-- Contenedor principal -->
    <div class="contenedor">
      <!-- Figura principal -->
      <div v-show="showFigure" :style="figureStyle" :class="figureClass" class="figure">
        <p v-if="showText" :style="{ color: fontColor, fontSize: fontSize, opacity: isOpaque ? 0.5 : 1, fontFamily: fontFamily }">
          {{ textContent }}
        </p>
      </div>

      <!-- formulario -->
      <div class="formulario">
        <div class="formulario__labels">
          <label>
            Color de fondo:
            <span>{{ backgroundName }}</span>
            <input type="color" v-model="backgroundColor" />
          </label>
          <label>
            Color de texto:
            <span>{{ textColorName }}</span>
            <input type="color" v-model="fontColor" />
          </label>
          <label>
            Mostrar texto:
            <input type="checkbox" v-model="showText" />
          </label>
          <label>
            Borde:
            <input
              type="range"
              v-model="borderWidth"
              min="0"
              max="10"
              step="1"
            />
            <span>{{ borderWidth }}px</span>
          </label>
          <label>
            Contenido textual:
            <input type="text" v-model="textContent" />
          </label>
          <label>
            Tipografía:
            <select v-model="fontFamilyOption">
              <option value="'Arial', sans-serif">Arial</option>
              <option value="'Courier New', Courier, monospace">Courier</option>
              <option value="'Georgia', serif">Georgia</option>
            </select>
          </label>
          <label>
            Opaco:
            <input type="checkbox" v-model="isOpaque" />
          </label>
          <label>
            Tamaño de la letra:
            <div class="letra-tamano">
              <label>
                <input type="radio" value="small" v-model="fontSizeOption" /> Pequeño
              </label>
              <label>
                <input type="radio" value="medium" v-model="fontSizeOption" /> Mediano
              </label>
              <label>
                <input type="radio" value="large" v-model="fontSizeOption" /> Grande
              </label>
            </div>
          </label>
          
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      backgroundColor: '#66a266', 
      fontColor: '#ffffff', 
      textContent: 'Awesome Vue.js', 
      fontSizeOption: 'medium', 
      isOpaque: false, 
      showText: true, 
      width: 300, 
      height: 300, 
      showFigure: true, 
      borderWidth: 0, 
      fontFamilyOption: "'Arial', sans-serif", 
    };
  },
  computed: {
    figureStyle() {
      return {
        backgroundColor: this.backgroundColor,
        color: this.fontColor,
        width: `${this.width}px`,
        height: `${this.height}px`,
        border: `${this.borderWidth}px solid black`, 
      };
    },
    fontSize() {
      return {
        small: '12px',
        medium: '16px',
        large: '24px',
      }[this.fontSizeOption];
    },
    figureClass() {
      return {
        'is-large': this.width > 200, 
        'is-small': this.width <= 200,
      };
    },
    backgroundName() {
      return this.backgroundColor === '#66a266' ? 'darkgreen' : 'custom';
    },
    textColorName() {
      return this.fontColor === '#ffffff' ? 'white' : 'custom';
    },
    fontFamily() {
      return this.fontFamilyOption; 
    },
  },
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
}

.formulario {
  margin-bottom: 20px;
}

.formulario__labels {
  background-color: #3a6355; 
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 20px;
  width: 400px;
  margin: 0 auto;
}

label {
  color: white;
  font-size: 16px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 5px;
}

input[type="color"] {
  width: 50px;
  height: 30px;
  border: none;
  cursor: pointer;
}

input[type="radio"],
input[type="checkbox"] {
  margin-right: 10px;
}

input[type="range"] {
  width: 100%;
}

.letra-tamano {
  display: flex;
  gap: 10px;
  justify-content: center;
}

.figure {
  margin: 20px auto;
  border-radius: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  font-size: 18px;
  margin: 5px 0;
}
</style>
