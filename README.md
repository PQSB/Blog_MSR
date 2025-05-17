# Practica 3
## Explicación gráficos obtenidos

### Posiciones de interés durante el pick and place:
Para el pick and place se utilizan las siguientes posiciones del brazo:
- home: posición origen cuando comienza la simulación
- target: posición a la altura del suelo para agarrar el cubo (sólo se modifica la articulación prismática)
- hold (posición para sostener el cubo a la altura correcta (sólo se modifica la articulación prismática)
- release (posición para dejar caer el cubo en el contendor del rover)

Por tanto, la trayectoria seguida por el brazo (sin contar el end effector) durante el pick and place es la siguiente:

**home &rArr; target &rArr; hold &rArr; release &rArr; hold &rArr; home**

### Momentos de interés en la teleoperación:
Durante la ejecución del pick and place destacan los siguientes momentos:

| Nº | Descripción                                      | Intervalo        |
|:--:|:-------------------------------------------------|:-----------------|
| 1  | Desplazamiento hasta posición de extracción cubo | ***0 s &rArr; 22 s*** |
| 2  | Agarrando cubo en posición target                | ***47 s &rArr; 57 s***|
| 3  | Movimiento del brazo a posición hold             | ***57 s &rArr; 58 s***|
| 4  | Sosteniendo cubo en posición hold                | ***58 s &rArr; 86 s***|
| 5  | Movimiento del brazo a posición release          | ***86 s &rArr; 91 s***|
| 6  | Sosteniendo cubo en posición release             | ***91 s &rArr; 100 s***|
| 7  | Abrir gripper para soltar cubo en posición release| ***100 s***      |
| 8  | Movimiento del brazo a posición home             | ***109 s &rArr; 115 s***|
---

### 1. Gráfico posición de las ruedas - tiempo


---

### 2. Gráfico aceleración ruedas - tiempo 

---

### 3. Gráfico gasto - tiempo


---
