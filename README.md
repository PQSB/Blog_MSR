# Practica 3: Explicación gráficos obtenidos

## Posiciones de interés durante el pick and place:
Para el pick and place se utilizan las siguientes posiciones del brazo:
- **home:** posición origen cuando comienza la simulación del pick and place
- **target:** posición a la altura del suelo para agarrar el cubo (sólo se modifica la articulación prismática)
- **hold:** posición para sostener el cubo a la altura correcta (sólo se modifica la articulación prismática)
- **release:** posición para dejar caer el cubo en el contendor del rover

Por tanto, la trayectoria seguida por el brazo (sin contar el end effector) durante el pick and place es la siguiente:
<a id="trajectory"></a>

**home &rArr; target &rArr; hold &rArr; release &rArr; hold &rArr; home**

## Momentos de interés durante la ejecución completa:
Durante la ejecución del pick and place destacan los siguientes momentos:
<a id="table"></a>
| Nº | Descripción                                      | Intervalo        |
|:--:|:-------------------------------------------------|:-----------------|
| 1  | Desplazamiento hasta posición correcta para pick and place | ***0 s &rArr; 22 s*** |
| 2  | Agarrando cubo en posición target                | ***47 s &rArr; 57 s***|
| 3  | Movimiento del brazo a posición hold             | ***57 s &rArr; 58 s***|
| 4  | Sosteniendo cubo en posición hold                | ***58 s &rArr; 86 s***|
| 5  | Movimiento del brazo a posición release          | ***86 s &rArr; 91 s***|
| 6  | Sosteniendo cubo en posición release             | ***91 s &rArr; 100 s***|
| 7  | Abrir gripper para soltar cubo en posición release| ***100 s***      |
| 8  | Movimiento del brazo a posición home             | ***109 s &rArr; 115 s***|
---

## 1. Gráfico posición de las ruedas - tiempo
En este gráfico destacan los siguientes detalles:
- Las variaciones en posición ocurren durante el intervalo de desplazamiento hasta la posición de inicio del pick and place ([Nº1](#table)). Esto se debe a que solo se realiza teleoperación de la base del robot hasta que se alcanza dicha posición. Una vez alcanzada, como se puede comprobar, los valores se estabilizan durante el resto de la ejecución.

- Se puede observar que los valores correspondientes a las ruedas del lado derecho (right) son negativos. Esto se debe a que para ser compatible con los REP de ROS, el eje z del lado derecho está apuntando hacia fuera, lo que provoca que la dirección positiva de las ruedas en ese lado cause un desplazamiento hacia detrás.

- Se puede observar también que desde el segundo **13** hasta el **20** aproximadamente, se produce una breve parada y después un cierto decremento en los valores. Esto se debe a que primero se detuvo la teleoperación para evaluar si la posición era correcta y, al verificar que no lo era, se realizó un desplazamiento marcha atrás para rectificar. Después de realizar la corrección, se avanza hasta el segundo **22** en el que se alcanza las posición deseada y se detiene la teleoperación de la base por lo que los valores se estabilizan.

---

## 2. Gráfico aceleración ruedas - tiempo 
En este gráfico destacan los siguientes detalles:
- Las principales variaciones en aceleración ocurren durante el intervalo de desplazamiento hasta la posición de inicio del pick and place ([Nº1](#table)). Esto se debe a que, como se ha comentado previamente, solo se realiza teleoperación de la base del robot hasta que se alcanza dicha posición.

- Como se comentó en el gráfico anterior, se puede ver que se produce una pequeñas estabilización debido a la parada realizada de verificación entre los segundos **13** y **17** aproximadamente.

- A pesar de que las mayores variaciones se producen durante el intervalo comentado, se puede comprobar que una vez ya finalizada la teleoperación de la base se vuelven a encontrar ciertos picos. Estos coinciden con momentos en los que los links del brazo realizan los desplazamientos más destacables ([Nº5 y Nº8](#table)).

---

## 3. Gráfico gasto - tiempo
El movimiento del pick and place comienza una vez alcanzada la posición indicada, por lo que comienza a partir del segundo 22 aproximadamente ([Nº1](#table)).

En el gráfico se puede comprobar que se sigue la trayectoria descrita ([trayecto](#trajectory)) en la que destacan los momentos remarcados en la [tabla](#table) apreciándose los siguientes resultados en cada etapa:
- **Nº2 Agarrando cubo en posición target:** se puede observar que al cerrar los dedos del gripper y comenzar a sujetar el cubo se producen unos cambios ligeros en las fuerzas empeladas por los joints. La fuerza empleada por el joint prismático disminuye y, tanto la empleada por los dos joints revolute y como por la base del gripper aumenta. Es decir, el joint prismático necesita realizar menos esfuerzo para manetenerse en esa posición mientras que a los otros les cuesta más trabajo.

- **Nº3 Movimiento del brazo a posición hold y Nº4 Sosteniendo cubo en posición hold:** se puede observar que al subir el joint prismático a la posición hold, la fuerza necesitada por dicho joint para mantener esa posición aumenta a un valor mayor que el inicial, alcanzando su valor máximo constante. Este cambio se debe a que el cubo ya no reposa en el suelo y el joint debe manetenerlo elevado compensando el peso del mismo. Por otra parte, para el resto de joints este valor disminuye hasta prácticamente retornar al valor que tenían inicialmente.

- **Nº5 Movimiento del brazo a posición release y Nº6 Sosteniendo cubo en posición release:** se puede observar como durante el desplazamiento de la posición hold a la posición release, se producen varios picos de aumento y descenso en la fuerza empleada por el joint prismático debidos al propio movimiento ya que este dificulta el mantener el cubo a esa altura. Por otro lado, se puede observar un aumento en la fuerza empleado por el resto de joints puesto que todos están involucrados en dicho movimiento. Incluso el gripper_base_link_joint ya que es necesaria una rotación para alcanzar la posición requerida. Una vez alcanzada la posición se puede observar como los valors vuelven a estabilizarse con los valores que se tenían en la posición previa hold, verificando así que los aumentos se debieron al propio desplazamiento.

- 
---
