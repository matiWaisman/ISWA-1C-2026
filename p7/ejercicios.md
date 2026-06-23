# Ejercicio 1 
Si no consideramos llamados y retornos el cfg seria: 

<img src="images/p7e1a.png" alt="cfg">

| Nodo n | IN[n]                      | OUT[n]                     |
|--------|----------------------------|----------------------------|
| m1     | -                          | {$x \to \bot, y \to \bot$} |
| m2     | {$x \to \bot, y \to \bot$} | {$x \to \bot, y \to \bot$} |
| m3     | {$x \to \bot, y \to \bot$} | {$x \to >, y \to \bot$}    |
| m4     | {$x \to >, y \to \bot$}    | {$x \to >, y \to \top$}    |
| m5     | {$x \to >, y \to \top$}    | {$x \to 0, y \to \top$}    |
| m6     | {$x \to 0, y \to \top$}    | {$x \to 0, y \to \top$}    |
| m7     | {$x \to 0, y \to \top$}    | {$x \to 0, y \to \top$}    |
| m8     | {$x \to 0, y \to \top$}    | -                          |

Asumo que print no modifica los parametros x e y, si lo hiciera habria que cambiar x a $\top$. 

Si ahora si consideramos los llamados y retornos del cfg con cloning: 

<img src="images/p7e1b.png" alt="cfg">


Con cloning:

| Nodo n | IN[n]                                   | OUT[n]                                  |
|--------|-----------------------------------------|-----------------------------------------|
| m1     | -                                       | {$x \to \bot, y \to \bot$}              |
| m2     | {$x \to \bot, y \to \bot$}              | {$x \to \bot, y \to \bot$}              |
| m3     | {$x \to \bot, y \to \bot$}              | {$x \to >, y \to \bot$}                 |
| m4     | {$x \to >, y \to \bot$}                 | {$x \to >, y \to \bot$}                 |
| mbt_11 | {$x_{m1} \to >, \text{res}_1 \to \bot$} | {$x_{m1} \to >, \text{res}_1 \to \bot$} |
| mbt_12 | {$x_{m1} \to >, \text{res}_1 \to \bot$} | {$x_{m1} \to >, \text{res}_1 \to >$}    |
| mbt_13 | {$x_{m1} \to >, \text{res}_1 \to >$}    | {$x_{m1} \to >, \text{res}_1 \to >$}    |
| mbt_14 | {$x_{m1} \to >, \text{res}_1 \to >$}    | {$x_{m1} \to >, \text{res}_1 \to >$}    |
| m5     | {$x \to >, y \to \bot$}                 | {$x \to >, y \to >$}                    |
| m6     | {$x \to >, y \to >$}                    | {$x \to 0, y \to >$}                    |
| m7     | {$x \to 0, y \to >$}                    | {$x \to 0, y \to >$}                    |
| mbt_21 | {$x_{m2} \to 0, \text{res}_1 \to \bot$} | {$x_{m1} \to 0, \text{res}_1 \to \bot$} |
| mbt_22 | {$x_{m2} \to 0, \text{res}_1 \to \bot$} | {$x_{m1} \to 0, \text{res}_1 \to 0$}    |
| mbt_23 | {$x_{m2} \to 0, \text{res}_1 \to \bot$} | {$x_{m1} \to 0, \text{res}_1 \to 0$}    |
| mbt_24 | {$x_{m2} \to 0, \text{res}_1 \to \bot$} | {$x_{m1} \to 0, \text{res}_1 \to 0$}    |
| m8     | {$x \to 0, y \to >$}                    | {$x \to 0, y \to 0$}                    |
| m8     | {$x \to 0, y \to >$}                    | {$x \to 0, y \to 0$}                    |
| m8     | {$x \to 0, y \to >$}                    | -                                       |

Con contextos, donde el primer llamado es $c_1$ y el segundo $c_2$

| Iteracion | Nodo n | IN[n]                                                                                                                   | OUT[n]                                                                                                                  |
|-----------|--------|-------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| 1         | m1     | -                                                                                                                       | $\epsilon \to \{x \to \bot, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                              |
| 1         | m2     | $\epsilon \to \{x \to \bot, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                              | $\epsilon \to \{x \to \bot, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                              |
| 1         | m3     | $\epsilon \to \{x \to \bot, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                              | $\epsilon \to \{x \to +, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                 |
| 1         | m4     | $\epsilon \to \{x \to +, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                 | $\epsilon \to \{x \to +, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                 |
| 1         | mbt_1  | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to \bot \}, c_2 \to \text{unreach}$                       | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to \bot \}, c_2 \to \text{unreach}$                       |
| 1         | mbt_2  | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to \bot \}, c_2 \to \text{unreach}$                       | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to + \}, c_2 \to \text{unreach}$                          |
| 1         | mbt_3  | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to \bot \}, c_2 \to \text{unreach}$                       | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to + \}, c_2 \to \text{unreach}$                          |
| 1         | mbt_4  | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to \bot \}, c_2 \to \text{unreach}$                       | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to + \}, c_2 \to \text{unreach}$                          |
| 1         | m5     | $\epsilon \to \{x \to +, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                 | $\epsilon \to \{x \to +, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    |
| 1         | m6     | $\epsilon \to \{x \to +, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    | $\epsilon \to \{x \to 0, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    |
| 1         | m7     | $\epsilon \to \{x \to 0, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    | $\epsilon \to \{x \to 0, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    |
| 1         | m8     | $\epsilon \to \{x \to 0, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    | $\epsilon \to \text{unreach}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                           |
| 1         | m9     | $\epsilon \to \{x \to 0, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    | $\epsilon \to \text{unreach}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                           |
| 1         | m10    | $\epsilon \to \{x \to 0, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    | -                                                                                                                       |
| 2         | m1     | -                                                                                                                       | $\epsilon \to \{x \to \bot, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                              |
| 2         | m2     | $\epsilon \to \{x \to \bot, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                              | $\epsilon \to \{x \to \bot, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                              |
| 2         | m3     | $\epsilon \to \{x \to \bot, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                              | $\epsilon \to \{x \to +, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                 |
| 2         | m4     | $\epsilon \to \{x \to +, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                 | $\epsilon \to \{x \to +, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                 |
| 2         | mbt_1  | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to \bot \},  c_2 \to \{x_m \to 0, \text{res} \to \bot \}$ | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to \bot \},  c_2 \to \{x_m \to 0, \text{res} \to \bot \}$ |
| 2         | mbt_2  | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to \bot \},  c_2 \to \{x_m \to 0, \text{res} \to \bot \}$ | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to + \},  c_2 \to \{x_m \to 0, \text{res} \to 0 \}$       |
| 2         | mbt_3  | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to + \},  c_2 \to \{x_m \to 0, \text{res} \to 0 \}$       | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to + \},  c_2 \to \{x_m \to 0, \text{res} \to 0 \}$       |
| 2         | mbt_4  | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to + \},  c_2 \to \{x_m \to 0, \text{res} \to 0 \}$       | $\epsilon \to\text{unreach}, c_1 \to \{x_m \to +, \text{res} \to + \},  c_2 \to \{x_m \to 0, \text{res} \to 0 \}$       |
| 2         | m5     | $\epsilon \to \{x \to +, y \to \bot \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                 | $\epsilon \to \{x \to +, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    |
| 2         | m6     | $\epsilon \to \{x \to +, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    | $\epsilon \to \{x \to 0, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    |
| 2         | m7     | $\epsilon \to \{x \to 0, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    | $\epsilon \to \{x \to 0, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    |
| 2         | m8     | $\epsilon \to \{x \to 0, y \to + \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    | $\epsilon \to \{x \to 0, y \to 0 \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    |
| 2         | m9     | $\epsilon \to \{x \to 0, y \to 0 \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    | $\epsilon \to \{x \to 0, y \to 0 \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    |
| 2         | m10    | $\epsilon \to \{x \to 0, y \to 0 \}, c_1 \to \text{unreach}, c_2 \to \text{unreach}$                                    | -                                                                                                                       |


