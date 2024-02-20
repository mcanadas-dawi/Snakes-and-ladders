# SNAKES AND LEADERS
## CODEWARS 5KYU KATA
### TAREA
Tu objetivo es crear una clase  llamada SnakesLadders. Los test llamarán al método play(die1, die2) independientemente del estado del juego o del turno del jugador. Las variables die1 y die2 son el dado lanzado en un turno y ambas son números enteros entre 1 y 6. El jugador moverá la suma de die1 y die2.

###  REGLAS
1.  Hay dos jugadores y ambos comienzan el tablero en la casilla 0.

3. El jugador 1 comienza y se alterna con el jugador 2.

5. Sigues los números en el tablero en orden 1=>100.

7. Si el valor de ambos dados es el mismo, ese jugador tendrá otro turno.

9.  Las escaleras en el tablero de juego te permiten ascender y avanzar más rápido. Si aterrizas exactamente en un cuadrado que muestra una imagen de la parte inferior de una escalera, entonces puedes mover al jugador hasta el cuadrado en la parte superior de la escalera.

11.  Deslízate hacia abajo por las serpientes. Las serpientes te hacen retroceder en el tablero porque tienes que deslizarte hacia abajo. Si aterrizas exactamente en la parte superior de una serpiente, desliza y mueve al jugador hasta el cuadrado en la parte inferior de la serpiente o rampa.

13.  Aterriza exactamente en el último cuadrado para ganar. Gana la primera persona que llegue a la casilla más alta del tablero. ¡Pero hay un giro! Si tiras demasiado alto, tu jugador "rebota" en el último cuadrado y retrocede. Solo puedes ganar sacando el número exacto necesario para aterrizar en el último cuadrado. Por ejemplo, si estás en la casilla 98 y sacas un cinco, mueve tu pieza del juego a 100 (dos movimientos), luego "rebota" de regreso a 99, 98, 97 (tres, cuatro y luego cinco movimientos).

15.  Si el jugador obtuvo un doble y cae en la casilla final “100” sin ningún movimiento restante, entonces el jugador gana el juego y no tiene que volver a tirar.


**¡Return Player n Wins!**. Donde n es el jugador ganador que ha aterrizado en la casilla 100 sin que le queden movimientos restantes.

**Return ¡Game over!** si un jugador ha ganado y otro jugador intenta jugar.

De lo contrario, **return Player n is on square x**. Donde n es el jugador actual y x es el cuadrado en el que se encuentran actualmente.
### CÓDIGO
```java
public class SnakesLadders {
    static int[] jugadores = new int[]{0,0}; //casilla en la que estara cada jugador
    static int jugador = 0;
    static boolean fin = false;
    static int[] tablero = new int[] //tablero teniendo en cuenta escaleras y serpientes
        {0,1,38,3,4,5,6,14,31,9,10,
        11,12,13,14,26,6,17,18,19,20,
        42,22,23,24,25,26,27,84,29,30,
        31,32,33,34,35,44,37,38,39,40,
        41,42,43,44,45,25,47,48,11,50,
        67,52,53,54,55,56,57,58,59,60,
        61,19,63,60,65,66,67,68,69,70,
        91,72,73,53,75,76,77,98,79,80,
        81,82,83,84,85,86,94,88,68,90,
        91,88,93,94,75,96,97,98,80,100
      };  
    public SnakesLadders() {
      jugador = 0;
      jugadores[0] = 0;
      jugadores[1] = 0;
      fin = false;
    }
    public String play(int die1, int die2) {
            if(fin) return "Game over!";
            String ret = "";
            jugadores[jugador] += die1 + die2;
            if(jugadores[jugador] > 100) { //calculo rebote cuando no entro en la última casilla sacando número exacto
            jugadores[jugador] = 200-jugadores[jugador];
            }
            jugadores[jugador] = tablero[jugadores[jugador]]; //el jugador "x" esta en la casilla "y"
            ret = "Player "+(jugador+1)+" is on square "+jugadores[jugador];
            if(jugadores[jugador] == 100) { //ganador
              ret = "Player "+(jugador+1)+" Wins!";
              fin = true;
            }
            if(die1 != die2){ //cambio de turno
                jugador = 1-jugador;
            }      
            return ret;
    }
}
```
#### ENLACE AL KATA
[Snakes_and_Ladders](https://www.codewars.com/kata/587136ba2eefcb92a9000027 "Kata link")
