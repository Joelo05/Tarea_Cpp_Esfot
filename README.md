# Tarea_Cpp_Esfot
Indicaciones de la Tarea – Programación en C++
Ejercicios SIN funciones
1) Vector de 5 ciudades (datos quemados). Mostrar la ciudad del tercer registro.
   #include <iostream>
using namespace std;

int main() {
    string ciudades[5] = {"Quito", "Guayaquil", "Cuenca", "Ambato", "Manta"};

    cout << "La ciudad del tercer registro es: " << ciudades[2];

    return 0;
}


2) Vector de materias con tamaño ingresado por el usuario.
   #include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Ingrese el tamano del vector: ";
    cin >> n;

    string materias[n];

    cout << "Ingrese las materias del tercer semestre:" << endl;
    for (int i = 0; i < n; i++) {
        cout << "Materia " << i << ": ";
        cin >> materias[i];
    }

    cout << "Materias ingresadas:" << endl;
    for (int i = 0; i < n; i++) {
        cout << materias[i] << endl;
    }

    return 0;
}



3) Vector de 4 equipos de fútbol y sus puntajes.
   #include <iostream>
using namespace std;

int main() {
    string equipos[4];
    int puntajes[4];

    cout << "Ingrese equipos y puntajes:" << endl;
    for (int i = 0; i < 4; i++) {
        cout << "Equipo " << i << ": ";
        cin >> equipos[i];
        cout << "Puntaje: ";
        cin >> puntajes[i];
    }

    int mayor = puntajes[0];
    int pos = 0;

    for (int i = 1; i < 4; i++) {
        if (puntajes[i] > mayor) {
            mayor = puntajes[i];
            pos = i;
        }
    }

    cout << "El equipo con mayor puntaje es: " << equipos[pos] << " con " << mayor;

    return 0;
}


Ejercicios CON funciones – Ejercicio 1
#include <iostream>
using namespace std;

void llenarPaises(string paises[]) {
    cout << "Ingrese 5 paises:" << endl;
    for (int i = 0; i < 5; i++) {
        cout << "Pais " << i << ": ";
        cin >> paises[i];
    }
}

void registrarPrecios(int precios[]) {
    cout << "Ingrese precios de vuelos:" << endl;
    for (int i = 0; i < 5; i++) {
        cout << "Precio " << i << ": ";
        cin >> precios[i];
    }
}

void autorPrograma() {
    cout << "Autor: Joel Del Pozo" << endl;
}

int main() {
    string paises[5];
    int precios[5];

    llenarPaises(paises);
    registrarPrecios(precios);
    autorPrograma();

    return 0;
}


Ejercicios CON funciones – Ejercicio 2
#include <iostream>
using namespace std;

void pedirDimensiones(int &filas, int &columnas) {
    cout << "Ingrese filas: ";
    cin >> filas;
    cout << "Ingrese columnas: ";
    cin >> columnas;
}

void llenarMatriz(int matriz[][10], int filas, int columnas) {
    cout << "Ingrese los valores:" << endl;
    for (int i = 0; i < filas; i++) {
        for (int j = 0; j < columnas; j++) {
            cout << "[" << i << "][" << j << "]: ";
            cin >> matriz[i][j];
        }
    }
}

void mostrarMatriz(int matriz[][10], int filas, int columnas) {
    cout << "Contenido:" << endl;
    for (int i = 0; i < filas; i++) {
        for (int j = 0; j < columnas; j++) {
            cout << matriz[i][j] << " ";
        }
        cout << endl;
    }
}

int main() {
    int filas, columnas;
    int matriz[10][10];

    pedirDimensiones(filas, columnas);
    llenarMatriz(matriz, filas, columnas);
    mostrarMatriz(matriz, filas, columnas);

    return 0;
}


Ejercicio 3 – Notas de estudiantes
#include <iostream>
using namespace std;

int main() {
    string estudiantes[2] = {"Ana", "Juan"};
    int notas[2][4] = {
        {3, 4, 5, 10},
        {10, 9, 6, 10}
    };

    for (int i = 0; i < 2; i++) {
        int suma = 0;
        for (int j = 0; j < 4; j++) {
            suma += notas[i][j];
        }
        float promedio = suma / 4.0;

        cout << "Estudiante: " << estudiantes[i] << " Promedio: " << promedio << endl;
    }

    return 0;
}


Ejercicio 4 – Inventario
#include <iostream>
using namespace std;

int main() {
    string productos[3];
    int inicial[3];
    int vendido[3];
    int finalStock[3];

    cout << "Ingreso de productos:" << endl;
    for (int i = 0; i < 3; i++) {
        cout << "Producto " << i << ": ";
        cin >> productos[i];
        cout << "Stock inicial: ";
        cin >> inicial[i];
        cout << "Stock vendido: ";
        cin >> vendido[i];

        if (vendido[i] > inicial[i]) {
            cout << "Error: no puede vender mas de lo que hay" << endl;
            finalStock[i] = -1;
        } else {
            finalStock[i] = inicial[i] - vendido[i];
        }
    }

    cout << "Resultados:" << endl;
    for (int i = 0; i < 3; i++) {
        cout << productos[i] << " Stock final: " << finalStock[i] << endl;
    }

    return 0;
}


Ejercicio de Recursividad
#include <iostream>
using namespace std;

int ventasDias(int ventas[], int n) {
    if (n == 0) {
        return 0;
    }
    return ventas[n - 1] + ventasDias(ventas, n - 1);
}

int main() {
    int n;
    cout << "Ingrese numero de dias: ";
    cin >> n;

    int ventas[n];
    for (int i = 0; i < n; i++) {
        cout << "Ventas dia " << i << ": ";
        cin >> ventas[i];
    }

    int total = ventasDias(ventas, n);
    cout << "Total ventas: " << total;

    return 0;
}

Ejercicio especial – YouTubers con estructura y matriz
#include <iostream>
#include <cstdlib>
using namespace std;

struct Youtuber {
    string nombre;
    string categoria;
    int suscriptores;
};

int main() {
    Youtuber matriz[2][2] = {
        {{"Auron", "Gaming", 30}, {"Luzu", "Vlogs", 5}},
        {{"Gonza", "Tecnologia", 2}, {"Rubi", "Gaming", 8}}
    };

    int ganancias[2][2];

    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            int aleatorio = 3000 + rand() % 5001;
            ganancias[i][j] = matriz[i][j].suscriptores * aleatorio;
        }
    }

    string buscar;
    cout << "Ingrese categoria a buscar: ";
    cin >> buscar;

    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            if (matriz[i][j].categoria == buscar) {
                cout << "Encontrado en posicion [" << i << "][" << j << "]" << endl;
            }
        }
    }

    int totalSus = 0, totalGan = 0;
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            totalSus += matriz[i][j].suscriptores;
            totalGan += ganancias[i][j];
        }
    }

    cout << "Total suscriptores: " << totalSus << endl;
    cout << "Total ganancias: " << totalGan;

    return 0;
}


ACTIVIDAD PRACTICA:
EJERCICIO 1 (sin funciones)
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Ingrese el tamano del arreglo: ";
    cin >> n;

    int arreglo[n];

    cout << "Llenar arreglo:" << endl;
    for (int i = 0; i < n; i++) {
        cout << "Elemento " << i << ": ";
        cin >> arreglo[i];
    }

    int pos;
    cout << "Ingrese la posicion a buscar: ";
    cin >> pos;

    if (pos >= 0 && pos < n) {
        cout << "Dato en la posicion " << pos << ": " << arreglo[pos];
    } else {
        cout << "Posicion fuera del rango";
    }

    return 0;
}

EJERCICIO 2 (sin funciones)
#include <iostream>
using namespace std;

int main() {
    string nombres[3];
    int edades[3];

    cout << "Ingreso de nombres y edades:" << endl;
    for (int i = 0; i < 3; i++) {
        cout << "Nombre " << i << ": ";
        cin >> nombres[i];
        cout << "Edad " << i << ": ";
        cin >> edades[i];
    }

    cout << "Datos ingresados:" << endl;
    for (int i = 0; i < 3; i++) {
        cout << "Persona: " << nombres[i] << " - Edad: " << edades[i] << endl;
    }

    return 0;
}

EJERCICIO 2 (sin funciones)
#include <iostream>
using namespace std;

int main() {
    string nombres[3];
    int edades[3];

    cout << "Ingreso de nombres y edades:" << endl;
    for (int i = 0; i < 3; i++) {
        cout << "Nombre " << i << ": ";
        cin >> nombres[i];
        cout << "Edad " << i << ": ";
        cin >> edades[i];
    }

    cout << "Datos ingresados:" << endl;
    for (int i = 0; i < 3; i++) {
        cout << "Persona: " << nombres[i] << " - Edad: " << edades[i] << endl;
    }

    return 0;
}

EJERCICIO 4 (con funciones, arreglos paralelos)
#include <iostream>
using namespace std;

void llenarDatos(string nombres[], int edades[]) {
    for (int i = 0; i < 3; i++) {
        cout << "Nombre " << i << ": ";
        cin >> nombres[i];
        cout << "Edad " << i << ": ";
        cin >> edades[i];
    }
}

void mostrarDatos(string nombres[], int edades[]) {
    cout << "Datos ingresados:" << endl;
    for (int i = 0; i < 3; i++) {
        cout << "Persona: " << nombres[i] << " - Edad: " << edades[i] << endl;
    }
}

int main() {
    string nombres[3];
    int edades[3];

    llenarDatos(nombres, edades);
    mostrarDatos(nombres, edades);

    return 0;
}

