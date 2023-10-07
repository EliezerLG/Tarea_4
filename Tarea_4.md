
## Ejercicio 1
escriba una aplicación para resolver el siguiente enunciado. Un estacionamiento cobra una
cuota mínima de $2.00 por estacionarse hasta tres horas. El estacionamiento cobra $0.50 adicionales
por cada hora o fracción que se pase de tres horas. El cargo máximo para cualquier periodo dado de 24
horas es de $10.00. Suponga que ningún automóvil se estaciona durante más de 24 horas a la vez.
Escriba un programa que calcule e imprima los cargos por estacionamiento para cada uno de tres
clientes que estacionaron su automóvil ayer en este estacionamiento. Debe introducir las horas de
estacionamiento para cada cliente. El programa debe imprimir los resultados en un formato tabular
ordenado, debe calcular e imprimir el total de los recibos de ayer. El programa debe utilizar la función
calcularCargos para determinar el cargo para cada cliente. Sus resultados deben aparecer en el siguiente
formato:
# C++
```
#include <iostream>
#include <vector>
#include <string>

using namespace std;

// Función para calcular los cargos por estacionamiento
double calcularCargos(double horas) {
    double cargo = 2.0; // Tarifa base

    if (horas > 3.0) {
        cargo += min(10.0, (horas - 3.0) * 0.5); // Cargo adicional por hora después de 3 horas, máximo $10.00
    }
    if (horas >= 24.0) {
        cargo = 10.0; // Establecer el cargo máximo en $10.00 después de 24 horas
    }

    return cargo;
}

int main() {
    cout << "Ingrese los siguientes Datos" << endl;
    cout << " " << endl;
    cout << "Cliente     Horas Estacionadas" << endl;

    double total_recibos = 0.0;

    vector<double> horas_estacionadas;
    vector<double> cargos;

    for (int cliente = 1; cliente <= 3; ++cliente) {
        double horas;
        cout << cliente << "                 ";
        cin >> horas;

        horas_estacionadas.push_back(horas);

        double cargo = calcularCargos(horas);
        cargos.push_back(cargo);// funciona para imprimir un datos al final del vector

        total_recibos += cargo;
    }
    cout << " " << endl;
    cout << "A continuación se le imprimirá un reporte" << endl;
    cout << " " << endl;
    cout << "Cliente     Horas Estacionadas   Cargo" << endl;
   for (int cliente = 0; cliente < 3; ++cliente) {
        cout << cliente + 1 << "               ";
        cout.precision(3); // Establecer la precisión en un decimal
        cout << horas_estacionadas[cliente] << "               $";
        cout.precision(2); // Establecer la precisión en dos decimales
        cout << cargos[cliente] << endl;
    }

    cout << "                 TOTAL              $";
    cout.precision(2); // Establecer la precisión en dos decimales
    cout << total_recibos << endl;

    return 0;
}
```
# Python
```
def calcular_cargos(horas):
    cargo = 2.0  # Tarifa base

    if horas > 3.0:
        cargo += min(10.0, (horas - 3.0) * 0.5)  # Cargo adicional por hora después de 3 horas, máximo $10.00
    if horas >= 24.0:
        cargo = 10.0  # Establecer el cargo máximo en $10.00 después de 24 horas

    return cargo

print("Ingrese los siguientes Datos")
print(" ")
print("Cliente     Horas Estacionadas")

total_recibos = 0.0

horas_estacionadas = []
cargos = []

for cliente in range(1, 4):
    horas = float(input(f"{cliente}                 "))
    horas_estacionadas.append(horas)

    cargo = calcular_cargos(horas)
    cargos.append(cargo)  # funciona para imprimir un datos al final de la lista

    total_recibos += cargo

print(" ")
print("A continuación se le imprimirá un reporte")
print(" ")
print("Cliente     Horas Estacionadas   Cargo")

for cliente in range(3):
    print(f"{cliente + 1}               {horas_estacionadas[cliente]:.3f}               ${cargos[cliente]:.2f}")

print("                 TOTAL              $%.2f" % total_recibos)
```
# Imagenes
![Estacionamiento](https://mail.google.com/mail/u/1?ui=2&ik=d6f780a736&attid=0.1&permmsgid=msg-a:r-4948701384418308422&th=18b087e443b19d12&view=fimg&fur=ip&sz=s0-l75-ft&attbid=ANGjdJ_eqOjJlu3KR6Sa-GXd3Df9waabopN7UwYPUN08Oo0Kwbh3XC6k0sZ2s2YKqcinQgRe-Bi83MYJQ2Es4qaFo-39FJjEHHgMdUyL9PHrSGiSHbzRbxxM1aN9K2M&disp=emb&realattid=ii_lnfkbpf30)

# Ejercicio 2 
Escriba una aplicación que le pregunte al usuario cuántas filas y cuántas columnas de una
matriz quiere ingresar, luego que reciba todos los valores, seguido debe imprimir el número mayor de
la matriz y los datos de la matriz ingresada y el promedio de la matriz
# C++
```
#include <iostream>
#include <vector>

using namespace std;

int main() {
    int filas, columnas;
    
    // Solicitar al usuario el número de filas y columnas
    cout << "Ingrese el número de filas de la matriz: ";
    cin >> filas;
    cout << "Ingrese el número de columnas de la matriz: ";
    cin >> columnas;

    // Declarar una matriz de enteros con las dimensiones especificadas
    vector<vector<int>> matriz(filas, vector<int>(columnas));

    // Solicitar al usuario ingresar los valores de la matriz
    cout << "Ingrese los valores de la matriz:" << endl;
    for (int i = 0; i < filas; ++i) {
        for (int j = 0; j < columnas; ++j) {
            cout << "Matriz[" << i << "][" << j << "]: ";
            cin >> matriz[i][j];
        }
    }

    // Encontrar el número mayor en la matriz
    int mayor = matriz[0][0];
    for (int i = 0; i < filas; ++i) {
        for (int j = 0; j < columnas; ++j) {
            if (matriz[i][j] > mayor) {
                mayor = matriz[i][j];
            }
        }
    }

    // Calcular el promedio de la matriz
    double suma = 0.0;
    for (int i = 0; i < filas; ++i) {
        for (int j = 0; j < columnas; ++j) {
            suma += matriz[i][j];
        }
    }
    double promedio = suma / (filas * columnas);

    // Mostrar el número mayor, la matriz y el promedio
    cout << "Número mayor en la matriz: " << mayor << endl;

    cout << "Matriz ingresada:" << endl;
    for (int i = 0; i < filas; ++i) {
        for (int j = 0; j < columnas; ++j) {
            cout << matriz[i][j] << "\t";
        }
        cout << endl;
    }

    cout << "Promedio de la matriz: " << promedio << endl;

    return 0;
}
```
# Python
```
def ingresar_matriz(filas, columnas):
    matriz = []
    print("Ingrese los valores de la matriz:")
    for i in range(filas):
        fila = [int(input(f"Matriz[{i}][{j}]: ")) for j in range(columnas)]
        matriz.append(fila)
    return matriz

def encontrar_mayor(matriz):
    return max(max(fila) for fila in matriz)

def calcular_promedio(matriz):
    suma = sum(sum(fila) for fila in matriz)
    return suma / (len(matriz) * len(matriz[0]))

def main():
    filas = int(input("Ingrese el número de filas de la matriz: "))
    columnas = int(input("Ingrese el número de columnas de la matriz: "))

    matriz = ingresar_matriz(filas, columnas)
    mayor = encontrar_mayor(matriz)
    promedio = calcular_promedio(matriz)

    print(f"Número mayor en la matriz: {mayor}")
    print("Matriz ingresada:")
    for fila in matriz:
        print("\t".join(map(str, fila)))
    print(f"Promedio de la matriz: {promedio}")
```
# Imagenes
![Estacionamiento](https://mail.google.com/mail/u/1?ui=2&ik=d6f780a736&attid=0.2&permmsgid=msg-a:r461331365379152675&th=18b08982d946053f&view=fimg&fur=ip&sz=s0-l75-ft&attbid=ANGjdJ8XLLPpgrOLxtG9YYpFmhcwnEMtlpm_0AEia_W3zam_wjd77goiGC4b34huPGtNkm7c0K6ePT-qYWG95BrtJGRokLsX4wfq3E9sPALgd83TRpFiYLgiC2sGl4M&disp=emb&realattid=ii_lnflc44o1)

# Ejercicio 3
Se dice que un número entero es un número perfecto si la suma de sus divisores,
incluyendo 1 (pero no el número en sí), es igual al número. Por ejemplo, 6 es un número perfecto ya
que 6 = 1 + 2 + 3.
Escriba una función llamada esPerfecto que determine si el parámetro numero es un número perfecto.
Use esta función en un programa que determine e imprima todos los números perfectos entre 1 y 1000.
Imprima los divi- sores de cada número perfecto para confirmar que el número sea realmente perfecto.
Ponga a prueba el poder de su computadora, evaluando números mucho más grandes que 1000.
# C++
# Python
# Imagenes
# Ejercicio 4
Escriba una aplicación que determine la mediana y el promedio de una lista (arreglo) de
números, donde el usuario indique la cantidad de e ingrese dichos números. Es decir el debe decir cuáto
será la longitud del arreglo e ingresará cada número.
# C++
# Python
# Imagenes
