# Ejercicio 1 
Si no consideramos llamados y retornos el cfg seria: 

<img src="images/p7e1a.png" alt="cfg">

| Nodo n | IN[n]                        | OUT[n]                       |
|--------|------------------------------|------------------------------|
| m1     | -                            | $\{x \to \bot, y \to \bot\}$ |
| m2     | $\{x \to \bot, y \to \bot\}$ | $\{x \to \top, y \to \top\}$ |
| m3     | $\{x \to \top, y \to \top\}$ | $\{x \to >, y \to \top\}$    |
| m4     | $\{x \to >, y \to \top\}$    | $\{x \to >, y \to \top\}$    |
| m5     | $\{x \to >, y \to \top\}$    | $\{x \to 0, y \to \top\}$    |
| m6     | $\{x \to 0, y \to \top\}$    | $\{x \to 0, y \to \top\}$    |
| m7     | $\{x \to 0, y \to \top\}$    | $\{x \to 0, y \to \top\}$    |
| m8     | $\{x \to 0, y \to \top\}$    | -                            |

Asumo que print no modifica los parametros x e y, si lo hiciera habria que cambiar x a $\top$. 

Si ahora si consideramos los llamados y retornos del cfg: 

<img src="images/p7e1b.png" alt="cfg">


Ahora considerando llamados y retornos pero sin cloning: 
| Iteracion | Nodo n | IN[n]                                                                                           | OUT[n]                                       |
|-----------|--------|-------------------------------------------------------------------------------------------------|----------------------------------------------|
| 1         | m1     | -                                                                                               | $\{x \to \bot, y \to \bot\}$                 |
| 1         | m2     | $\{x \to \bot, y \to \bot\}$                                                                    | $\{x \to \top, y \to \top\}$                 |
| 1         | m3     | $\{x \to \top, y \to \top\}$                                                                    | $\{x \to +, y \to \top\}$                    |
| 1         | m4     | $\{x \to +, y \to \top\}$                                                                       | $\{x \to +, y \to \top\}$                    |
| 1         | mbt_11 | $\{x_mbt \to +, \text{result} \to \bot\}$ $\sqcup$ $\{x_mbt \to \bot, \text{result} \to \bot\}$ | $\{x_mbt \to +, \text{result} \to \bot\}$    |
| 1         | mbt_21 | $\{x_mbt \to +, \text{result} \to \bot\}$                                                       | $\{x_mbt \to +, \text{result} \to +\}$       |
| 1         | mbt_31 | $\{x_mbt \to +, \text{result} \to +\}$                                                          | $\{x_mbt \to +, \text{result} \to +\}$       |
| 1         | mbt_41 | $\{x_mbt \to +, \text{result} \to +\}$                                                          | $\{x_mbt \to +, \text{result} \to +\}$       |
| 1         | m5     | $\{x \to +, y \to \top\}$                                                                       | $\{x \to +, y \to +\}$                       |
| 1         | m6     | $\{x \to +, y \to \top\}$                                                                       | $\{x \to 0, y \to +\}$                       |
| 1         | m7     | $\{x \to 0, y \to +\}$                                                                          | $\{x \to 0, y \to +\}$                       |
| 1         | mbt_12 | $\{x_mbt \to +, \text{result} \to \bot\}$ $\sqcup$ $\{x_mbt \to 0, \text{result} \to \bot\}$    | $\{x_mbt \to \top, \text{result} \to \bot\}$ |
| 1         | mbt_22 | $\{x_mbt \to \top, \text{result} \to \bot\}$                                                    | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| 1         | mbt_32 | $\{x_mbt \to \top, \text{result} \to \bot\}$                                                    | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| 1         | mbt_42 | $\{x_mbt \to \top, \text{result} \to \bot\}$                                                    | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| 1         | m8     | $\{x \to 0, y \to +\}$                                                                          | $\{x \to 0, y \to \top\}$                    |
| 1         | m9     | $\{x \to 0, y \to \top\}$                                                                       | $\{x \to 0, y \to \top\}$                    |
| 1         | m10    | $\{x \to 0, y \to \top\}$                                                                       | -                                            |
| 2         | m1     | -                                                                                               | $\{x \to \bot, y \to \bot\}$                 |
| 2         | m2     | $\{x \to \bot, y \to \bot\}$                                                                    | $\{x \to \top, y \to \top\}$                 |
| 2         | m3     | $\{x \to \top, y \to \top\}$                                                                    | $\{x \to +, y \to \top\}$                    |
| 2         | m4     | $\{x \to +, y \to \top\}$                                                                       | $\{x \to +, y \to \top\}$                    |
| 2         | mbt_11 | $\{x_mbt \to +, \text{result} \to \bot\}$ $\sqcup$ $\{x_mbt \to 0, \text{result} \to \bot\}$    | $\{x_mbt \to \top, \text{result} \to \bot\}$ |
| 2         | mbt_21 | $\{x_mbt \to \top, \text{result} \to \bot\}$                                                    | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| 2         | mbt_31 | $\{x_mbt \to \top, \text{result} \to \top\}$                                                    | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| 2         | mbt_41 | $\{x_mbt \to \top, \text{result} \to \top\}$                                                    | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| 2         | m5     | $\{x \to +, y \to \top\}$                                                                       | $\{x \to +, y \to \top\}$                    |
| 2         | m6     | $\{x \to +, y \to \top\}$                                                                       | $\{x \to 0, y \to \top\}$                    |
| 2         | m7     | $\{x \to 0, y \to \top\}$                                                                       | $\{x \to 0, y \to \top\}$                    |
| 2         | mbt_12 | $\{x_mbt \to +, \text{result} \to \bot\}$ $\sqcup$ $\{x_mbt \to 0, \text{result} \to \bot\}$    | $\{x_mbt \to \top, \text{result} \to \bot\}$ |
| 2         | mbt_22 | $\{x_mbt \to \top, \text{result} \to \bot\}$                                                    | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| 2         | mbt_32 | $\{x_mbt \to \top, \text{result} \to \bot\}$                                                    | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| 2         | mbt_42 | $\{x_mbt \to \top, \text{result} \to \bot\}$                                                    | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| 2         | m8     | $\{x \to 0, y \to +\}$                                                                          | $\{x \to 0, y \to \top\}$                    |
| 2         | m9     | $\{x \to 0, y \to \top\}$                                                                       | $\{x \to 0, y \to \top\}$                    |
| 2         | m10    | $\{x \to 0, y \to \top\}$                                                                       | -                                            |

Entonces la tabla final queda: 

| Nodo n | IN[n]                                                                                        | OUT[n]                                       |
|--------|----------------------------------------------------------------------------------------------|----------------------------------------------|
| m1     | -                                                                                            | $\{x \to \bot, y \to \bot\}$                 |
| m2     | $\{x \to \bot, y \to \bot\}$                                                                 | $\{x \to \top, y \to \top\}$                 |
| m3     | $\{x \to \top, y \to \top\}$                                                                 | $\{x \to +, y \to \top\}$                    |
| m4     | $\{x \to +, y \to \top\}$                                                                    | $\{x \to +, y \to \top\}$                    |
| mbt_11 | $\{x_mbt \to +, \text{result} \to \bot\}$ $\sqcup$ $\{x_mbt \to 0, \text{result} \to \bot\}$ | $\{x_mbt \to \top, \text{result} \to \bot\}$ |
| mbt_21 | $\{x_mbt \to \top, \text{result} \to \bot\}$                                                 | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| mbt_31 | $\{x_mbt \to \top, \text{result} \to \top\}$                                                 | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| mbt_41 | $\{x_mbt \to \top, \text{result} \to \top\}$                                                 | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| m5     | $\{x \to +, y \to \top\}$                                                                    | $\{x \to +, y \to \top\}$                    |
| m6     | $\{x \to +, y \to \top\}$                                                                    | $\{x \to 0, y \to \top\}$                    |
| m7     | $\{x \to 0, y \to \top\}$                                                                    | $\{x \to 0, y \to \top\}$                    |
| mbt_12 | $\{x_mbt \to +, \text{result} \to \bot\}$ $\sqcup$ $\{x_mbt \to 0, \text{result} \to \bot\}$ | $\{x_mbt \to \top, \text{result} \to \bot\}$ |
| mbt_22 | $\{x_mbt \to \top, \text{result} \to \bot\}$                                                 | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| mbt_32 | $\{x_mbt \to \top, \text{result} \to \bot\}$                                                 | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| mbt_42 | $\{x_mbt \to \top, \text{result} \to \bot\}$                                                 | $\{x_mbt \to \top, \text{result} \to \top\}$ |
| m8     | $\{x \to 0, y \to +\}$                                                                       | $\{x \to 0, y \to \top\}$                    |
| m9     | $\{x \to 0, y \to \top\}$                                                                    | $\{x \to 0, y \to \top\}$                    |
| m10    | $\{x \to 0, y \to \top\}$                                                                    | -                                            |

La entrada para `print(x,y)` es $x \to 0, y \to \top$.

Con cloning:

| Nodo n | IN[n]                                     | OUT[n]                                    |
|--------|-------------------------------------------|-------------------------------------------|
| m1     | -                                         | $\{x \to \bot, y \to \bot\}$              |
| m2     | $\{x \to \bot, y \to \bot\}$              | $\{x \to \top, y \to \top\}$              |
| m3     | $\{x \to \top, y \to \top\}$              | $\{x \to >, y \to \top\}$                 |
| m4     | $\{x \to >, y \to \top\}$                 | $\{x \to >, y \to \top\}$                 |
| mbt_11 | $\{x_{m1} \to >, \text{res}_1 \to \bot\}$ | $\{x_{m1} \to >, \text{res}_1 \to \bot\}$ |
| mbt_12 | $\{x_{m1} \to >, \text{res}_1 \to \bot\}$ | $\{x_{m1} \to >, \text{res}_1 \to >\}$    |
| mbt_13 | $\{x_{m1} \to >, \text{res}_1 \to >\}$    | $\{x_{m1} \to >, \text{res}_1 \to >\}$    |
| mbt_14 | $\{x_{m1} \to >, \text{res}_1 \to >\}$    | $\{x_{m1} \to >, \text{res}_1 \to >\}$    |
| m5     | $\{x \to >, y \to \top\}$                 | $\{x \to >, y \to >\}$                    |
| m6     | $\{x \to >, y \to >\}$                    | $\{x \to 0, y \to >\}$                    |
| m7     | $\{x \to 0, y \to >\}$                    | $\{x \to 0, y \to >\}$                    |
| mbt_21 | $\{x_{m2} \to 0, \text{res}_1 \to \bot\}$ | $\{x_{m1} \to 0, \text{res}_1 \to \bot\}$ |
| mbt_22 | $\{x_{m2} \to 0, \text{res}_1 \to \bot\}$ | $\{x_{m1} \to 0, \text{res}_1 \to 0\}$    |
| mbt_23 | $\{x_{m2} \to 0, \text{res}_1 \to \bot\}$ | $\{x_{m1} \to 0, \text{res}_1 \to 0\}$    |
| mbt_24 | $\{x_{m2} \to 0, \text{res}_1 \to \bot\}$ | $\{x_{m1} \to 0, \text{res}_1 \to 0\}$    |
| m8     | $\{x \to 0, y \to >\}$                    | $\{x \to 0, y \to 0\}$                    |
| m9     | $\{x \to 0, y \to >\}$                    | $\{x \to 0, y \to 0\}$                    |
| m10    | $\{x \to 0, y \to >\}$                    | -                                         |

Con  cadenas de llamadas con k=1
| Iteracion | Nodo n | IN[n]                                                                                                                   | OUT[n]                                                                                                                  |
|-----------|--------|-------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| 1         | m1     | -                                                                                                                       | $\epsilon \to \{x \to \bot, y \to \bot\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                               |
| 1         | m2     | $\epsilon \to \{x \to \bot, y \to \bot\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                               | $\epsilon \to \{x \to \top, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                               |
| 1         | m3     | $\epsilon \to \{x \to \top, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                               | $\epsilon \to \{x \to +, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                  |
| 1         | m4     | $\epsilon \to \{x \to +, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                  | $\epsilon \to \{x \to +, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                  |
| 1         | mbt_1  | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to \bot\}, c_2 \to \text{unreach}$                      | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to \bot\}, c_2 \to \text{unreach}$                      |
| 1         | mbt_2  | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to \bot\}, c_2 \to \text{unreach}$                      | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to +\}, c_2 \to \text{unreach}$                         |
| 1         | mbt_3  | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to +\}, c_2 \to \text{unreach}$                         | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to +\}, c_2 \to \text{unreach}$                         |
| 1         | mbt_4  | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to +\}, c_2 \to \text{unreach}$                         | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to +\}, c_2 \to \text{unreach}$                         |
| 1         | m5     | $\epsilon \to \{x \to +, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                  | $\epsilon \to \{x \to +, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     |
| 1         | m6     | $\epsilon \to \{x \to +, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     | $\epsilon \to \{x \to Z, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     |
| 1         | m7     | $\epsilon \to \{x \to Z, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     | $\epsilon \to \{x \to Z, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     |
| 1         | m8     | $\epsilon \to \{x \to Z, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     | $\epsilon \to \text{unreach}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                           |
| 1         | m9     | $\epsilon \to \text{unreach}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                           | $\epsilon \to \text{unreach}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                           |
| 1         | m10    | $\epsilon \to \text{unreach}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                           | -                                                                                                                       |
| 2         | m1     | -                                                                                                                       | $\epsilon \to \{x \to \bot, y \to \bot\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                               |
| 2         | m2     | $\epsilon \to \{x \to \bot, y \to \bot\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                               | $\epsilon \to \{x \to \top, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                               |
| 2         | m3     | $\epsilon \to \{x \to \top, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                               | $\epsilon \to \{x \to +, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                  |
| 2         | m4     | $\epsilon \to \{x \to +, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                  | $\epsilon \to \{x \to +, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                  |
| 2         | mbt_1  | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to \bot\}, c_2 \to \{x \to Z, \text{result} \to \bot\}$ | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to \bot\}, c_2 \to \{x \to Z, \text{result} \to \bot\}$ |
| 2         | mbt_2  | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to \bot\}, c_2 \to \{x \to Z, \text{result} \to \bot\}$ | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to +\}, c_2 \to \{x \to Z, \text{result} \to Z\}$       |
| 2         | mbt_3  | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to \bot\}, c_2 \to \{x \to Z, \text{result} \to Z\}$    | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to \bot\}, c_2 \to \{x \to Z, \text{result} \to Z\}$    |
| 2         | mbt_4  | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to \bot\}, c_2 \to \{x \to Z, \text{result} \to Z\}$    | $\epsilon \to \text{unreach}, c_1 \to \{x \to +, \text{result} \to \bot\}, c_2 \to \{x \to Z, \text{result} \to Z\}$    |
| 2         | m5     | $\epsilon \to \{x \to +, y \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                  | $\epsilon \to \{x \to +, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     |
| 2         | m6     | $\epsilon \to \{x \to +, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     | $\epsilon \to \{x \to Z, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     |
| 2         | m7     | $\epsilon \to \{x \to Z, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     | $\epsilon \to \{x \to Z, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     |
| 2         | m8     | $\epsilon \to \{x \to Z, y \to +\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     | $\epsilon \to \{x \to Z, y \to Z\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     |
| 2         | m9     | $\epsilon \to \{x \to Z, y \to Z\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     | $\epsilon \to \{x \to Z, y \to Z\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     |
| 2         | m10    | $\epsilon \to \{x \to Z, y \to Z\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                     | -                                                                                                                       |


Con contextos funcionales: 

| Nodo n | IN[n]                                                                                                                                                                      | OUT[n]                                                                                                                                                                     |
|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| m1     | -                                                                                                                                                                          | $\{x \to \bot, y \to \bot\} \to \{x \to \bot, y \to \bot\}, \ldots \to \text{unreach}$                                                                                     |
| m2     | $\{x \to \bot, y \to \bot\} \to \{x \to \bot, y \to \bot\}, \ldots \to \text{unreach}$                                                                                     | $\{x \to \bot, y \to \bot\} \to \{x \to \bot, y \to \bot\}, \ldots \to \text{unreach}$                                                                                     |
| m3     | $\{x \to \bot, y \to \bot\} \to \{x \to \bot, y \to \bot\}, \ldots \to \text{unreach}$                                                                                     | $\{x \to \bot, y \to \bot\} \to \{x \to +, y \to \bot\}, \ldots \to \text{unreach}$                                                                                        |
| m4     | $\{x \to \bot, y \to \bot\} \to \{x \to +, y \to \bot\}, \ldots \to \text{unreach}$                                                                                        | $\{x \to \bot, y \to \bot\} \to \{x \to +, y \to \bot\}, \ldots \to \text{unreach}$                                                                                        |
| mbt_11 | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to \bot\} , \ldots \to \text{unreach}$                                                                        | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to \bot\} , \ldots \to \text{unreach}$                                                                        |
| mbt_12 | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to \bot\} , \ldots \to \text{unreach}$                                                                        | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to +\} , \ldots \to \text{unreach}$                                                                           |
| mbt_13 | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to +\} , \ldots \to \text{unreach}$                                                                           | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to +\} , \ldots \to \text{unreach}$                                                                           |
| mbt_14 | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to +\} , \ldots \to \text{unreach}$                                                                           | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to +\} , \ldots \to \text{unreach}$                                                                           |
| m5     | $\{x \to \bot, y \to \bot\} \to \{x \to +, y \to \bot\}, \ldots \to \text{unreach}$                                                                                        | $\{x \to \bot, y \to \bot\} \to \{x \to +, y \to +\}, \ldots \to \text{unreach}$                                                                                           |
| m6     | $\{x \to \bot, y \to \bot\} \to \{x \to +, y \to +\}, \ldots \to \text{unreach}$                                                                                           | $\{x \to \bot, y \to \bot\} \to \{x \to Z, y \to +\}, \ldots \to \text{unreach}$                                                                                           |
| m7     | $\{x \to \bot, y \to \bot\} \to \{x \to Z, y \to +\}, \ldots \to \text{unreach}$                                                                                           | $\{x \to \bot, y \to \bot\} \to \{x \to Z, y \to +\}, \ldots \to \text{unreach}$                                                                                           |
| mbt_21 | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to \bot\}, \{x \to Z, \text{res} \to \bot\} \to \{x \to Z, \text{res} \to \bot\},  \ldots \to \text{unreach}$ | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to \bot\}, \{x \to Z, \text{res} \to \bot\} \to \{x \to Z, \text{res} \to \bot\},  \ldots \to \text{unreach}$ |
| mbt_22 | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to \bot\}, \{x \to Z, \text{res} \to \bot\} \to \{x \to Z, \text{res} \to \bot\},  \ldots \to \text{unreach}$ | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to +\}, \{x \to Z, \text{res} \to \bot\} \to \{x \to Z, \text{res} \to Z\},  \ldots \to \text{unreach}$       |
| mbt_23 | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to +\}, \{x \to Z, \text{res} \to \bot\} \to \{x \to Z, \text{res} \to Z\},  \ldots \to \text{unreach}$       | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to +\}, \{x \to Z, \text{res} \to \bot\} \to \{x \to Z, \text{res} \to Z\},  \ldots \to \text{unreach}$       |
| mbt_24 | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to +\}, \{x \to Z, \text{res} \to \bot\} \to \{x \to Z, \text{res} \to Z\},  \ldots \to \text{unreach}$       | $\{x \to +, \text{res} \to \bot\} \to \{x \to +, \text{res} \to +\}, \{x \to Z, \text{res} \to \bot\} \to \{x \to Z, \text{res} \to Z\},  \ldots \to \text{unreach}$       |
| m8     | $\{x \to \bot, y \to \bot\} \to \{x \to Z, y \to +\}, \ldots \to \text{unreach}$                                                                                           | $\{x \to \bot, y \to \bot\} \to \{x \to Z, y \to Z\}, \ldots \to \text{unreach}$                                                                                           |
| m9     | $\{x \to \bot, y \to \bot\} \to \{x \to Z, y \to Z\}, \ldots \to \text{unreach}$                                                                                           | $\{x \to \bot, y \to \bot\} \to \{x \to Z, y \to Z\}, \ldots \to \text{unreach}$                                                                                           |
| m10    | $\{x \to \bot, y \to \bot\} \to \{x \to Z, y \to Z\}, \ldots \to \text{unreach}$                                                                                           | -                                                                                                                                                                          |

    
# Ejercicio 2 
Modificar el codigo haria en el punto D que si solo clonamos la funcion `multByTwo`, al llegar a `multByTwo_2` la primera vez pasando por `multByTwo` llamado por el nodo `m4` se haria un supremo entre $+$ y $\bot$ que da $+$ asi que no hay problema, pero en el segundo llamado desde el nodo `m7` se haria un supremo entre $Z$ y $+$ que da $\top$, por lo que como resultado final $y \to top$. Seria el mismo caso que sin hacer cloning. 

Modificarlo en el punto E haria que como la cadena de llamadas es de tamaño 1, al llegar al entry de `multByTwo_2` haya que tambien tomar supremo entre el out de los nodos llamadores, cuando pasamos en la iteracion 1 habria que tomar el supremo entre $+$ y $\text{unreach}$ que es $+$, pero en el segundo llamado habria que tomar el supremo de $+$ y $Z$, que es $\top$. 

Con contextos funcionales como tenemos "infinitos contextos", en ningun momento hay que tomar supremo y perder presicion. 

# Ejercicio 3 
<img src="images/p7e3.png" alt="cfg">

Asumiendo que `print` no modifica los valores de los parametros y que `input` devuelve $\top$, el zero análisis interprocedural usando el dominio del signo sin contextos va a ser: 

| Iteracion | Nodo n | IN[n]                        | OUT[n]                       |
|-----------|--------|------------------------------|------------------------------|
| 1         | m1     | -                            | $\{x \to \bot, y \to \bot\}$ |
| 1         | m2     | $\{x \to \bot, y \to \bot\}$ | $\{x \to \bot, y \to \bot\}$ |
| 1         | m3     | $\{x \to \bot, y \to \bot\}$ | $\{x \to \bot, y \to \top\}$ |
| 1         | m4     | $\{x \to \bot, y \to \top\}$ | $\{x \to Z, y \to \top\}$    |
| 1         | m5     | $\{x \to Z, y \to \top\}$    | $\{x \to Z, y \to \top\}$    |
| 1         | m6     | $\{x \to Z, y \to \top\}$    | $\{x \to Z, y \to \top\}$    |
| 1         | i1     | $\{a \to Z\}$                | $\{a \to Z\}$                |
| 1         | i2     | $\{a \to Z\}$                | $\{a \to Z\}$                |
| 1         | i3     | $\{a \to Z\}$                | $\{a \to Z\}$                |
| 1         | m7     | $\{x \to Z, y \to \top\}$    | $\{x \to +, y \to \top\}$    |
| 1         | m8     | $\{x \to +, y \to \top\}$    | $\{x \to +, y \to \top\}$    |
| 1         | m9     | $\{x \to Z, y \to \top\}$    | $\{x \to Z, y \to \top\}$    |
| 1         | m10    | $\{x \to Z, y \to \top\}$    | -                            |
| 2         | m1     | -                            | $\{x \to \bot, y \to \bot\}$ |
| 2         | m2     | $\{x \to \bot, y \to \bot\}$ | $\{x \to \bot, y \to \bot\}$ |
| 2         | m3     | $\{x \to \bot, y \to \bot\}$ | $\{x \to \bot, y \to \top\}$ |
| 2         | m4     | $\{x \to \bot, y \to \top\}$ | $\{x \to Z, y \to \top\}$    |
| 2         | m5     | $\{x \to \top, y \to \top\}$ | $\{x \to \top, y \to \top\}$ |
| 2         | m6     | $\{x \to \top, y \to \top\}$ | $\{x \to \top, y \to \top\}$ |
| 2         | i1     | $\{a \to \top\}$             | $\{a \to \top\}$             |
| 2         | i2     | $\{a \to \top\}$             | $\{a \to \top\}$             |
| 2         | i3     | $\{a \to \top\}$             | $\{a \to \top\}$             |
| 2         | m7     | $\{x \to \top, y \to \top\}$ | $\{x \to \top, y \to \top\}$ |
| 2         | m8     | $\{x \to \top, y \to \top\}$ | $\{x \to \top, y \to \top\}$ |
| 2         | m9     | $\{x \to \top, y \to \top\}$ | $\{x \to \top, y \to \top\}$ |
| 2         | m10    | $\{x \to \top, y \to \top\}$ | -                            |

Entonces la tabla final va a ser:

| Nodo n | IN[n]                        | OUT[n]                       |
|--------|------------------------------|------------------------------|
| m1     | -                            | $\{x \to \bot, y \to \bot\}$ |
| m2     | $\{x \to \bot, y \to \bot\}$ | $\{x \to \bot, y \to \bot\}$ |
| m3     | $\{x \to \bot, y \to \bot\}$ | $\{x \to \bot, y \to \top\}$ |
| m4     | $\{x \to \bot, y \to \top\}$ | $\{x \to Z, y \to \top\}$    |
| m5     | $\{x \to \top, y \to \top\}$ | $\{x \to \top, y \to \top\}$ |
| m6     | $\{x \to \top, y \to \top\}$ | $\{x \to \top, y \to \top\}$ |
| i1     | $\{a \to \top\}$             | $\{a \to \top\}$             |
| i2     | $\{a \to \top\}$             | $\{a \to \top\}$             |
| i3     | $\{a \to \top\}$             | $\{a \to \top\}$             |
| m7     | $\{x \to \top, y \to \top\}$ | $\{x \to \top, y \to \top\}$ |
| m8     | $\{x \to \top, y \to \top\}$ | $\{x \to \top, y \to \top\}$ |
| m9     | $\{x \to \top, y \to \top\}$ | $\{x \to \top, y \to \top\}$ |
| m10    | $\{x \to \top, y \to \top\}$ | -                            |


PREGUNTAR como seria con cloning porque hay algo que no estoy viendo de porque haria falta clonarlo. 

# Ejercicio 4 
<img src="images/p7e4.png" alt="cfg">

| Iteracion | Nodo n | IN[n]                      | OUT[n]                     |
|-----------|--------|----------------------------|----------------------------|
| 1         | m1     | -                          | $\{a \to \bot, b \to \bot\}$ |
| 1         | m2     | $\{a \to \bot, b \to \bot\}$ | $\{a \to \top, b \to \top\}$ |
| 1         | m3     | $\{a \to \top, b \to \top\}$ | $\{a \to I, b \to \top\}$    |
| 1         | m4     | $\{a \to I, b \to \top\}$    | $\{a \to I, b \to \top\}$    |
| 1         | g1     | $\{n \to I\}$                | $\{n \to I\}$                |
| 1         | g2     | $\{n \to I\}$                | $\{n \to I\}$                |
| 1         | m5     | $\{a \to I, b \to \top\}$    | $\{a \to I, b \to I\}$       |
| 1         | m6     | $\{a \to I, b \to I\}$       | $\{a \to P, b \to I\}$       |
| 1         | m7     | $\{a \to P, b \to I\}$       | $\{a \to P, b \to I\}$       |
| 1         | g1     | $\{n \to \top\}$             | $\{n \to \top\}$             |
| 1         | g2     | $\{n \to \top\}$             | $\{n \to \top\}$             |
| 1         | m8     | $\{a \to P, b \to I\}$       | $\{a \to P, b \to \top\}$    |
| 1         | m9     | $\{a \to P, b \to \top\}$    | $\{a \to P, b \to \top\}$    |
| 1         | m10    | $\{a \to P, b \to \top\}$    | -                          |
| 2         | m1     | -                          | $\{a \to \bot, b \to \bot\}$ |
| 2         | m2     | $\{a \to \bot, b \to \bot\}$ | $\{a \to \top, b \to \top\}$ |
| 2         | m3     | $\{a \to \top, b \to \top\}$ | $\{a \to I, b \to \top\}$    |
| 2         | m4     | $\{a \to I, b \to \top\}$    | $\{a \to I, b \to \top\}$    |
| 2         | g1     | $\{n \to \top\}$             | $\{n \to \top\}$             |
| 2         | g2     | $\{n \to \top\}$             | $\{n \to \top\}$             |
| 2         | m5     | $\{a \to I, b \to \top\}$    | $\{a \to I, b \to \top\}$    |
| 2         | m6     | $\{a \to I, b \to \top\}$    | $\{a \to P, b \to \top\}$    |
| 2         | m7     | $\{a \to P, b \to \top\}$    | $\{a \to P, b \to \top\}$    |
| 2         | g1     | $\{n \to \top\}$             | $\{n \to \top\}$             |
| 2         | g2     | $\{n \to \top\}$             | $\{n \to \top\}$             |
| 2         | m8     | $\{a \to P, b \to I\}$       | $\{a \to P, b \to \top\}$    |
| 2         | m9     | $\{a \to P, b \to \top\}$    | $\{a \to P, b \to \top\}$    |
| 2         | m10    | $\{a \to P, b \to \top\}$    | -                          |

Entonces la tabla final queda: 

| Nodo n | IN[n]                      | OUT[n]                     |
|--------|----------------------------|----------------------------|
| m1     | -                          | $\{a \to \bot, b \to \bot\}$ |
| m2     | $\{a \to \bot, b \to \bot\}$ | $\{a \to \top, b \to \top\}$ |
| m3     | $\{a \to \top, b \to \top\}$ | $\{a \to I, b \to \top\}$    |
| m4     | $\{a \to I, b \to \top\}$    | $\{a \to I, b \to \top\}$    |
| g1     | $\{n \to \top\}$             | $\{n \to \top\}$             |
| g2     | $\{n \to \top\}$             | $\{n \to \top\}$             |
| m5     | $\{a \to I, b \to \top\}$    | $\{a \to I, b \to \top\}$    |
| m6     | $\{a \to I, b \to \top\}$    | $\{a \to P, b \to \top\}$    |
| m7     | $\{a \to P, b \to \top\}$    | $\{a \to P, b \to \top\}$    |
| g1     | $\{n \to \top\}$             | $\{n \to \top\}$             |
| g2     | $\{n \to \top\}$             | $\{n \to \top\}$             |
| m8     | $\{a \to P, b \to I\}$       | $\{a \to P, b \to \top\}$    |
| m9     | $\{a \to P, b \to \top\}$    | $\{a \to P, b \to \top\}$    |
| m10    | $\{a \to P, b \to \top\}$    | -                          |


Usando cadenas de llamadas con $k = 1$: 

| Iteracion | Nodo n | IN[n]                                                                                     | OUT[n]                                                                                    |
|-----------|--------|-------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| 1         | m1     | -                                                                                         | $\epsilon \to \{a \to \bot, b \to \bot\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ |
| 1         | m2     | $\epsilon \to \{a \to \bot, b \to \bot\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ | $\epsilon \to \{a \to \top, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ |
| 1         | m3     | $\epsilon \to \{a \to \top, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    |
| 1         | m4     | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    |
| 1         | g1     | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \text{unreach}$                | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \text{unreach}$                |
| 1         | g2     | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \text{unreach}$                | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \text{unreach}$                |
| 1         | m5     | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    | $\epsilon \to \{a \to I, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| 1         | m6     | $\epsilon \to \{a \to I, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| 1         | m7     | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| 1         | m8     | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | $\epsilon \to \text{unreach}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$             |
| 1         | m9     | $\epsilon \to \text{unreach}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$             | $\epsilon \to \text{unreach}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$             |
| 1         | m10    | $\epsilon \to \text{unreach}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$             | -                                                                                         |
| 2         | m1     | -                                                                                         | $\epsilon \to \{a \to \bot, b \to \bot\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ |
| 2         | m2     | $\epsilon \to \{a \to \bot, b \to \bot\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ | $\epsilon \to \{a \to \top, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ |
| 2         | m3     | $\epsilon \to \{a \to \top, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    |
| 2         | m4     | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    |
| 2         | g1     | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \{n \to P\}$                   | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \{n \to P\}$                   |
| 2         | g2     | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \{n \to P\}$                   | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \{n \to P\}$                   |
| 2         | m5     | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    | $\epsilon \to \{a \to I, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| 2         | m6     | $\epsilon \to \{a \to I, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| 2         | m7     | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| 2         | m8     | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | $\epsilon \to \{a \to P, b \to P\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| 2         | m9     | $\epsilon \to \{a \to P, b \to P\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | $\epsilon \to \{a \to P, b \to P\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| 2         | m10    | $\epsilon \to \{a \to P, b \to P\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | -                                                                                         |

Entonces la tabla final va a ser: 

| Nodo n | IN[n]                                                                                     | OUT[n]                                                                                    |
|--------|-------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| m1     | -                                                                                         | $\epsilon \to \{a \to \bot, b \to \bot\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ |
| m2     | $\epsilon \to \{a \to \bot, b \to \bot\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ | $\epsilon \to \{a \to \top, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ |
| m3     | $\epsilon \to \{a \to \top, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$ | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    |
| m4     | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    |
| g1     | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \{n \to P\}$                   | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \{n \to P\}$                   |
| g2     | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \{n \to P\}$                   | $\epsilon \to \text{unreach}, c_1 \to \{n \to I\}, c_2 \to \{n \to P\}$                   |
| m5     | $\epsilon \to \{a \to I, b \to \top\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$    | $\epsilon \to \{a \to I, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| m6     | $\epsilon \to \{a \to I, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| m7     | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| m8     | $\epsilon \to \{a \to P, b \to I\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | $\epsilon \to \{a \to P, b \to P\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| m9     | $\epsilon \to \{a \to P, b \to P\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | $\epsilon \to \{a \to P, b \to P\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       |
| m10    | $\epsilon \to \{a \to P, b \to P\}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$       | -                                                                                         |

Usando contextos funcionales: 

| Nodo n | IN[n]                                                                                 | OUT[n]                                                                                |
|--------|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| m1     | -                                                                                     | $\{a \to \bot, b \to \bot\} \to \{a \to \bot, b \to \bot\} \ldots \to \text{unreach}$ |
| m2     | $\{a \to \bot, b \to \bot\} \to \{a \to \bot, b \to \bot\} \ldots \to \text{unreach}$ | $\{a \to \bot, b \to \bot\} \to \{a \to \top, b \to \top\} \ldots \to \text{unreach}$ |
| m3     | $\{a \to \bot, b \to \bot\} \to \{a \to \top, b \to \top\} \ldots \to \text{unreach}$ | $\{a \to \bot, b \to \bot\} \to \{a \to I, b \to \top\} \ldots \to \text{unreach}$    |
| m4     | $\{a \to \bot, b \to \bot\} \to \{a \to I, b \to \top\} \ldots \to \text{unreach}$    | $\{a \to \bot, b \to \bot\} \to \{a \to I, b \to \top\} \ldots \to \text{unreach}$    |
| g1     | $\{n \to I\} \to \{n \to I\} \ldots \to \text{unreach}$                               | $\{n \to I\} \to \{n \to I\} \ldots \to \text{unreach}$                               |
| g2     | $\{n \to I\} \to \{n \to I\} \ldots \to \text{unreach}$                               | $\{n \to I\} \to \{n \to I\} \ldots \to \text{unreach}$                               |
| m5     | $\{a \to \bot, b \to \bot\} \to \{a \to I, b \to \top\} \ldots \to \text{unreach}$    | $\{a \to \bot, b \to \bot\} \to \{a \to I, b \to I\} \ldots \to \text{unreach}$       |
| m6     | $\{a \to \bot, b \to \bot\} \to \{a \to I, b \to I\} \ldots \to \text{unreach}$       | $\{a \to \bot, b \to \bot\} \to \{a \to P, b \to I\} \ldots \to \text{unreach}$       |
| m7     | $\{a \to \bot, b \to \bot\} \to \{a \to P, b \to I\} \ldots \to \text{unreach}$       | $\{a \to \bot, b \to \bot\} \to \{a \to P, b \to I\} \ldots \to \text{unreach}$       |
| g1     | $\{n \to I\} \to \{n \to I\} \{n \to P\} \to \{n \to P\} \ldots \to \text{unreach}$   | $\{n \to I\} \to \{n \to I\} \{n \to P\} \to \{n \to P\} \ldots \to \text{unreach}$   |
| g2     | $\{n \to I\} \to \{n \to I\} \{n \to P\} \to \{n \to P\} \ldots \to \text{unreach}$   | $\{n \to I\} \to \{n \to I\} \{n \to P\} \to \{n \to P\} \ldots \to \text{unreach}$   |
| m8     | $\{a \to \bot, b \to \bot\} \to \{a \to P, b \to I\} \ldots \to \text{unreach}$       | $\{a \to \bot, b \to \bot\} \to \{a \to P, b \to P\} \ldots \to \text{unreach}$       |
| m9     | $\{a \to \bot, b \to \bot\} \to \{a \to P, b \to P\} \ldots \to \text{unreach}$       | $\{a \to \bot, b \to \bot\} \to \{a \to P, b \to P\} \ldots \to \text{unreach}$       |
| m10    | $\{a \to \bot, b \to \bot\} \to \{a \to P, b \to P\} \ldots \to \text{unreach}$       | -                                                                                     |

# Ejercicio 5
<img src="images/p7e5.png" alt="cfg">

Analisis sin contextos: 

| Iteracion | Nodo n | IN[n]                          | OUT[n]                         |
|-----------|--------|--------------------------------|--------------------------------|
| 1         | m1     | -                              | $\{x \to \bot, y \to \bot\}$   |
| 1         | m2     | $\{x \to \bot, y \to \bot\}$   | $\{x \to \top, y \to \top\}$   |
| 1         | m3     | $\{x \to \top, y \to \top\}$   | $\{x \to +, y \to \top\}$      |
| 1         | m4     | $\{x \to +, y \to \top\}$      | $\{x \to +, y \to \top\}$      |
| 1         | i1     | $\{n \to +, res \to \bot\}$    | $\{n \to +, res \to \bot\}$    |
| 1         | i2     | $\{n \to +, res \to \bot\}$    | $\{n \to +, res \to +\}$       |
| 1         | i3     | $\{n \to +, res \to +\}$       | $\{n \to +, res \to +\}$       |
| 1         | m5     | $\{x \to +, y \to \top\}$      | $\{x \to +, y \to +\}$         |
| 1         | m6     | $\{x \to +, y \to +\}$         | $\{x \to +, y \to +\}$         |
| 1         | d1     | $\{m \to Z, res \to \bot\}$    | $\{m \to Z, res \to \bot\}$    |
| 1         | d2     | $\{m \to Z, res \to \bot\}$    | $\{m \to Z, res \to Z\}$       |
| 1         | d3     | $\{m \to Z, res \to Z\}$       | $\{m \to Z, res \to Z\}$       |
| 1         | m7     | $\{x \to +, y \to +\}$         | $\{x \to Z, y \to +\}$         |
| 1         | m8     | $\{x \to Z, y \to +\}$         | $\{x \to Z, y \to +\}$         |
| 1         | i1     | $\{n \to \top, res \to \bot\}$ | $\{n \to \top, res \to \bot\}$ |
| 1         | i2     | $\{n \to \top, res \to \bot\}$ | $\{n \to \top, res \to \top\}$ |
| 1         | i3     | $\{n \to \top, res \to \top\}$ | $\{n \to \top, res \to \top\}$ |
| 1         | m9     | $\{x \to Z, y \to +\}$         | $\{x \to Z, y \to \top\}$      |
| 1         | m10    | $\{x \to Z, y \to \top\}$      | $\{x \to Z, y \to \top\}$      |
| 1         | m11    | $\{x \to Z, y \to \top\}$      | -                              |
| 2         | m1     | -                              | $\{x \to \bot, y \to \bot\}$   |
| 2         | m2     | $\{x \to \bot, y \to \bot\}$   | $\{x \to \top, y \to \top\}$   |
| 2         | m3     | $\{x \to \top, y \to \top\}$   | $\{x \to +, y \to \top\}$      |
| 2         | m4     | $\{x \to +, y \to \top\}$      | $\{x \to +, y \to \top\}$      |
| 2         | i1     | $\{n \to \top, res \to \bot\}$ | $\{n \to \top, res \to \bot\}$ |
| 2         | i2     | $\{n \to \top, res \to \bot\}$ | $\{n \to \top, res \to \top\}$ |
| 2         | i3     | $\{n \to \top, res \to \top\}$ | $\{n \to \top, res \to \top\}$ |
| 2         | m5     | $\{x \to +, y \to \top\}$      | $\{x \to +, y \to \top\}$      |
| 2         | m6     | $\{x \to +, y \to \top\}$      | $\{x \to +, y \to \top\}$      |
| 2         | d1     | $\{m \to Z, res \to \bot\}$    | $\{m \to Z, res \to \bot\}$    |
| 2         | d2     | $\{m \to Z, res \to \bot\}$    | $\{m \to Z, res \to Z\}$       |
| 2         | d3     | $\{m \to Z, res \to Z\}$       | $\{m \to Z, res \to Z\}$       |
| 2         | m7     | $\{x \to +, y \to \top\}$      | $\{x \to Z, y \to \top\}$      |
| 2         | m8     | $\{x \to Z, y \to \top\}$      | $\{x \to Z, y \to \top\}$      |
| 2         | i1     | $\{n \to \top, res \to \bot\}$ | $\{n \to \top, res \to \bot\}$ |
| 2         | i2     | $\{n \to \top, res \to \bot\}$ | $\{n \to \top, res \to \top\}$ |
| 2         | i3     | $\{n \to \top, res \to \top\}$ | $\{n \to \top, res \to \top\}$ |
| 2         | m9     | $\{x \to Z, y \to +\}$         | $\{x \to Z, y \to \top\}$      |
| 2         | m10    | $\{x \to Z, y \to \top\}$      | $\{x \to Z, y \to \top\}$      |
| 2         | m11    | $\{x \to Z, y \to \top\}$      | -                              |

Entonces la tabla final va a ser: 

| Nodo n | IN[n]                          | OUT[n]                         |
|--------|--------------------------------|--------------------------------|
| m1     | -                              | $\{x \to \bot, y \to \bot\}$   |
| m2     | $\{x \to \bot, y \to \bot\}$   | $\{x \to \top, y \to \top\}$   |
| m3     | $\{x \to \top, y \to \top\}$   | $\{x \to +, y \to \top\}$      |
| m4     | $\{x \to +, y \to \top\}$      | $\{x \to +, y \to \top\}$      |
| i1     | $\{n \to \top, res \to \bot\}$ | $\{n \to \top, res \to \bot\}$ |
| i2     | $\{n \to \top, res \to \bot\}$ | $\{n \to \top, res \to \top\}$ |
| i3     | $\{n \to \top, res \to \top\}$ | $\{n \to \top, res \to \top\}$ |
| m5     | $\{x \to +, y \to \top\}$      | $\{x \to +, y \to \top\}$      |
| m6     | $\{x \to +, y \to \top\}$      | $\{x \to +, y \to \top\}$      |
| d1     | $\{m \to Z, res \to \bot\}$    | $\{m \to Z, res \to \bot\}$    |
| d2     | $\{m \to Z, res \to \bot\}$    | $\{m \to Z, res \to Z\}$       |
| d3     | $\{m \to Z, res \to Z\}$       | $\{m \to Z, res \to Z\}$       |
| m7     | $\{x \to +, y \to \top\}$      | $\{x \to Z, y \to \top\}$      |
| m8     | $\{x \to Z, y \to \top\}$      | $\{x \to Z, y \to \top\}$      |
| i1     | $\{n \to \top, res \to \bot\}$ | $\{n \to \top, res \to \bot\}$ |
| i2     | $\{n \to \top, res \to \bot\}$ | $\{n \to \top, res \to \top\}$ |
| i3     | $\{n \to \top, res \to \top\}$ | $\{n \to \top, res \to \top\}$ |
| m9     | $\{x \to Z, y \to +\}$         | $\{x \to Z, y \to \top\}$      |
| m10    | $\{x \to Z, y \to \top\}$      | $\{x \to Z, y \to \top\}$      |
| m11    | $\{x \to Z, y \to \top\}$      | -                              |

Usando cadenas de llamadas con $k=1$: 

| Iteracion | Nodo n | IN[n]                                                                                                                          | OUT[n]                                                                                                                         |
|-----------|--------|--------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| 1         | m1     | -                                                                                                                              | $\epsilon \to \{x \to \bot, y \to \bot\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$           |
| 1         | m2     | $\epsilon \to \{x \to \bot, y \to \bot\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$           | $\epsilon \to \{x \to \top, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$           |
| 1         | m3     | $\epsilon \to \{x \to \top, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$           | $\epsilon \to \{x \to +, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$              |
| 1         | m4     | $\epsilon \to \{x \to +, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$              | $\epsilon \to \{x \to +, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$              |
| 1         | i1     | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to \bot\},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$            | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to \bot\},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$            |
| 1         | i2     | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to \bot\},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$            | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to +\},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$               |
| 1         | i3     | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to +\},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$               | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to +\},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$               |
| 1         | m5     | $\epsilon \to \{x \to +, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$              | $\epsilon \to \{x \to +, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 |
| 1         | m6     | $\epsilon \to \{x \to +, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 | $\epsilon \to \{x \to +, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 |
| 1         | d1     | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to \bot\},\ c_3 \to \text{unreach}$            | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to \bot\},\ c_3 \to \text{unreach}$            |
| 1         | d2     | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to \bot\},\ c_3 \to \text{unreach}$            | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to Z\},\ c_3 \to \text{unreach}$               |
| 1         | d3     | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to Z\},\ c_3 \to \text{unreach}$               | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to Z\},\ c_3 \to \text{unreach}$               |
| 1         | m7     | $\epsilon \to \{x \to +, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 |
| 1         | m8     | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 |
| 1         | m9     | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                       |
| 1         | m10    | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                       | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                       |
| 1         | m11    | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                       | -                                                                                                                              |
| 2         | m1     | -                                                                                                                              | $\epsilon \to \{x \to \bot, y \to \bot\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$           |
| 2         | m2     | $\epsilon \to \{x \to \bot, y \to \bot\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$           | $\epsilon \to \{x \to \top, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$           |
| 2         | m3     | $\epsilon \to \{x \to \top, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$           | $\epsilon \to \{x \to +, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$              |
| 2         | m4     | $\epsilon \to \{x \to +, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$              | $\epsilon \to \{x \to +, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$              |
| 2         | i1     | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to \bot\},\ c_2 \to \{n \to Z, res \to \bot\},\ c_3 \to \text{unreach}$ | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to \bot\},\ c_2 \to \{n \to Z, res \to \bot\},\ c_3 \to \text{unreach}$ |
| 2         | i2     | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to \bot\},\ c_2 \to \{n \to Z, res \to \bot\},\ c_3 \to \text{unreach}$ | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to +\},\ c_2 \to \{n \to Z, res \to +\},\ c_3 \to \text{unreach}$       |
| 2         | i3     | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to +\},\ c_2 \to \{n \to Z, res \to +\},\ c_3 \to \text{unreach}$       | $\epsilon \to \text{unreach},\ c_1 \to \{n \to +, res \to +\},\ c_2 \to \{n \to Z, res \to +\},\ c_3 \to \text{unreach}$       |
| 2         | m5     | $\epsilon \to \{x \to +, y \to \top\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$              | $\epsilon \to \{x \to +, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 |
| 2         | m6     | $\epsilon \to \{x \to +, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 | $\epsilon \to \{x \to +, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 |
| 2         | d1     | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to \bot\},\ c_3 \to \text{unreach}$            | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to \bot\},\ c_3 \to \text{unreach}$            |
| 2         | d2     | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to \bot\},\ c_3 \to \text{unreach}$            | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to Z\},\ c_3 \to \text{unreach}$               |
| 2         | d3     | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to Z\},\ c_3 \to \text{unreach}$               | $\epsilon \to \text{unreach},\ c_1 \to \text{unreach},\ c_2 \to \{m \to Z, res \to Z\},\ c_3 \to \text{unreach}$               |
| 2         | m7     | $\epsilon \to \{x \to +, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 |
| 2         | m8     | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 |
| 2         | m9     | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 |
| 2         | m10    | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 |
| 2         | m11    | $\epsilon \to \{x \to Z, y \to +\},\ c_1 \to \text{unreach},\ c_2 \to \text{unreach},\ c_3 \to \text{unreach}$                 | -                                                                                                                              |


