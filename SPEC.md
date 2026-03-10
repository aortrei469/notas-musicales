# Juego de Notas Musicales - Especificación

## 1. Project Overview

- **Nombre**: Notas Musicales - Memory Game
- **Tipo**: Juego interactivo HTML/CSS/JS
- **Funcionalidad**: Juego de memoria musical donde el sistema propone secuencias de notas y el jugador debe repetirlas
- **Target**: Jugadores individuales o múltiples

## 2. UI/UX Specification

### Layout Structure

- **Header**: Título del juego + selección de modo (1-4 jugadores)
- **Main Area**: 
  - Panel de 7 notas musicales (círculos grandes)
  - Indicador de turno/estado
  - Botón de inicio
- **Scoreboard**: Marcadores de cada jugador
- **Footer**: Instrucciones breves

### Visual Design

- **Color Palette**:
  - Background: #1a1a2e (azul oscuro)
  - Note colors (7 notas):
    - Do: #ff6b6b (rojo)
    - Re: #feca57 (amarillo)
    - Mi: #48dbfb (celeste)
    - Fa: #ff9ff3 (rosa)
    - Sol: #54a0ff (azul)
    - La: #5f27cd (púrpura)
    - Si: #00d2d3 (turquesa)
  - UI Elements: #2d3436 (gris oscuro)
  - Text: #ffffff
  - Active/Highlight: brightness(1.5) + box-shadow glow

- **Typography**:
  - Font: 'Segoe UI', system-ui, sans-serif
  - Title: 2.5rem, bold
  - Scores: 1.2rem
  - Buttons: 1rem

- **Spacing**: 16px base unit

### Components

- **Nota Button**: Círculo 80px, con color de nota, efecto hover/active
- **Score Card**: Tarjeta con nombre jugador y puntuación
- **Status Display**: Muestra secuencia actual / turno / mensajes
- **Mode Selector**: Botones para elegir 1-4 jugadores
- **Start Button**: Inicia el juego

### Interactive Behaviors

- Las notas brillan y suenan cuando:
  - El sistema reproduce la secuencia
  - El jugador hace click
- Transición suave de 300ms en cambios de estado

## 3. Functionality Specification

### Core Features

1. **7 Notas Musicales**:
   - Do, Re, Mi, Fa, Sol, La, Si
   - Cada nota tiene sonido único (Web Audio API)
   - Cada nota tiene color único

2. **Modo Single Player**:
   - Una secuencia que crece en cada ronda
   - Puntos: +n (n = notas acertadas en esa ronda)
   - Fallo: -n (n = notas de la secuencia que falló)
   - Mínimo score: 0

3. **Modo Multiplayer (2-4 jugadores)**:
   - Secuencia propuesta cada turno
   - Cada jugador intenta reproducir la secuencia
   - Si acierta: +n puntos, siguiente ronda (nueva secuencia)
   - Si falla: pierde turno, siguiente jugador intenta la misma secuencia
   - Gana quien alcance primero X puntos (opcional: sin límite, juego infinito)

4. **Flujo del juego**:
   - Seleccionar modo (1-4 jugadores)
   - Click en "Iniciar"
   - Sistema reproduce secuencia
   - Jugador reproduce secuencia
   - Verificar resultado
   - Actualizar puntuación
   - Continuar o pasar turno

### Edge Cases

- No permitir clicks durante reproducción del sistema
- Scores nunca negativos (mínimo 0)
- Reset de secuencia al cambiar de modo
- Manejar errores de audio gracefully

## 4. Acceptance Criteria

- [ ] 7 botones de notas visibles con colores distintos
- [ ] Cada nota produce sonido diferente al hacer click
- [ ] Las notas se iluminan durante reproducción
- [ ] Modo single player: puntuación aumenta con aciertos
- [ ] Modo single player: puntuación disminuye con fallos
- [ ] Modo multiplayer: pasa turno al siguiente jugador en fallo
- [ ] Todos los marcadores muestran números positivos (mínimo 0)
- [ ] Interfaz clara y responsiva
