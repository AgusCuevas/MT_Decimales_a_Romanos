# MT_Decimales_a_Romanos

## Función que Computa
La función principal de esta Máquina de Turing es recibir un número decimal (representado en base 10) y transformarlo en su equivalente en numeración romana, generando la salida en una cinta de trabajo.

### Entrada y Representación
- La entrada es un número decimal expresado en notación posicional (por ejemplo, "1987").
- La máquina lee la entrada dígito por dígito y la almacena en su cinta.

### Conversión de Dígitos
La máquina de Turing sigue un conjunto de reglas para traducir cada dígito según su posición (millares, centenas, decenas, unidades).  
Utiliza reglas como:

- **Unidades y decenas:**  
  - `1 → I`, `2 → II`, `3 → III`, ..., `9 → IX`  
  - `10 → X`, `20 → XX`, ..., `90 → XC`  

- **Centenas:**  
  - `100 → C`, `200 → CC`, ..., `900 → CM`  

- **Millares:**  
  - `1000 → M`, `2000 → MM`, `3000 → MMM`  

### Generación de la Salida
La máquina escribe la salida en la cinta, reemplazando cada dígito por su equivalente en números romanos.  

Ejemplo para **1987**:
- `1000 → M`
- `900 → CM`
- `80 → LXXX`
- `7 → VII`
- **Resultado:** `MCMLXXXVII`

## Límite de 3999 en los Números Romanos
El sistema de numeración romana clásico no incluye un símbolo específico para 5000 ni para potencias superiores de 10.  
Tradicionalmente, los números superiores a 3999 requerían una notación especial con líneas sobre los símbolos para multiplicarlos por 1000 (por ejemplo, `V̅` para representar `5000`).  

Dado que la máquina se basa en la notación romana convencional sin líneas o modificadores especiales, el máximo número que puede representar es **3999 (`MMMCMXCIX`)**.

---

## Formalismo
La Máquina de Turing se define formalmente como una **7-tupla** `(Q, Σ, Γ, δ, q0, qA, qR)`, donde:

- **Q**: Conjunto finito de estados.
- **Σ**: Alfabeto de entrada (dígitos decimales `0-9`).
- **Γ**: Alfabeto de la cinta (incluye `Σ` y los símbolos romanos `I, V, X, L, C, D, M` y el símbolo de espacio en blanco `_`).
- **δ**: Función de transición que describe los movimientos de la máquina.
- **q0**: Estado inicial.
- **qA**: Estado de aceptación.
- **qR**: Estado de rechazo.

---

## Diseño JFlap
Se modelará la Máquina de Turing en **JFlap**, donde se definen:

- Estados para identificar unidades, decenas, centenas y millares.
- Transiciones que transforman cada dígito decimal en su representación romana.
- Movimiento de la cabeza de la cinta según las reglas de transición.

---

## Programa Simulator
El programa leerá un número decimal, simulará el comportamiento de la máquina y devolverá el resultado en numeración romana.

---

## Inputs X 10: Configuraciones de Computación
Se evaluarán **10 entradas diferentes**, como:

| Entrada  | Salida | Movimientos| Celdas|
|----------|--------|------------|--------|
| 0000#     | #IV     |Steps: 4    |1       |
| 0004#    | #IV     |Steps: 9    |3       |
| 0009#     | #IX     |Steps: 9    |3       |
| 0014#     | #XIV    |Steps: 19   |4       |
| 0040#     | #XL     |Steps: 15   |2       |
| 0090#     | #XC     |Steps: 15   |3       |
| 3999#     | #MMMCMXCIX|Steps: 73 |10      |
| 0500#     | #D      |Steps: 15   |2       |
| 1000#     | #M      |Steps: 17   |2       |
| 2024#     | #MMXXIV |Steps: 43   |7       |
| 3888#     | #MMMDCCCLXXXVIII|Steps: 91   |16|

Para cada entrada, se analizará el comportamiento de la Máquina de Turing.

---

## Complejidad Temporal
La **complejidad temporal** mide cuántos pasos de cómputo realiza la Máquina de Turing en función del tamaño de la entrada.  
En este caso, el tamaño de la entrada es la cantidad de dígitos del número decimal que se quiere convertir a romano.

### **Análisis**
- Para cada dígito del número de entrada, la máquina necesita recorrer la cinta varias veces para reemplazarlo con los símbolos romanos correspondientes.
- Dado que los números romanos pueden tener una representación más larga que los decimales (por ejemplo, `3999 → "MMMCMXCIX"` con 9 caracteres), la máquina de Turing puede necesitar moverse múltiples veces sobre la cinta para insertar los caracteres correctos.
- La conversión implica principalmente **buscar equivalencias y escribir símbolos en la cinta**, lo que puede requerir movimientos proporcionales al número de caracteres generados.

### **Orden de Complejidad**
- Si **n** es la cantidad de dígitos del número decimal, la conversión puede tardar alrededor de **O(n)** en el peor caso.
- Sin embargo, dado que el número romano puede ser hasta **tres veces más largo** que el decimal en algunos casos, la máquina puede necesitar hasta **O(3n) = O(n)** pasos.

---

## Complejidad Espacial
La **complejidad espacial** mide cuánta memoria (**longitud de la cinta de la Máquina de Turing**) se usa durante la computación.

### **Análisis**
- La cantidad de espacio requerido depende de la longitud de la representación en números romanos.
- En el peor caso, un número decimal de **4 dígitos** puede convertirse en un número romano de hasta **9 caracteres** (ejemplo: `3999 → "MMMCMXCIX"`).
- La máquina necesita **suficiente cinta** para almacenar el resultado y operar los reemplazos de símbolos.

### **Orden de Complejidad**
- Si **n** es la cantidad de dígitos del número decimal, la representación romana puede ser hasta **tres veces más larga**, lo que da una **complejidad espacial de O(3n) = O(n)**.
