class EdR {
    handleEstudiante[] arregloHandlesEstudiantes;              // tamaño E, acceso por id
    booleanos[] listaCopiados  // el índice es el id
    MinHeap<Estudiantes> heapEstudiantes;   // ordenado por puntaje
    int[] solucionCanonica;                    // arreglo de tamaño R
    int dimensionAula;
}


class Estudiante {
    int id;
    boolean entregado;
    int respuestasCompletadas;          // contador
    int puntajeActual;                  // parte entera del % de respuestas correctas resueltas
    int[] respuestas;                   // tamaño R, valores -1 si no respondió
}


nuevoEdR:


Todas las demás es simplemente asignación por lo tanto es O(1)

TOTAL: O(E * R)

copiarse:
Buscar estudiante por id en arregloEstudiantes O(1)
Identificar “el vecino con más respuestas completadas”.
O(R) porque cada estudiante tiene respondido[] y necesitamos ver cuáles faltan.
Encontrar la primera respuesta faltante O(R)
Asignar la respuesta (respuestas = valor y respondido = true) O(1)
Actualizar puntaje O(R)
Reinsertar en heap O(log E)

TOTAL: O(R + log E)

resolver:
Buscar por arregloEstudiantes O(1)
Actualizar respuesta (respuestas = valor y respondido = true) O(1)
Actualizar puntaje O(1) porque sabemos exactamente qué ejercicio se resolvió
Actualizar en heap O(log E)


TOTAL: O(log E)

consultarDarkWeb:
Por cada estudiante k: O(k)
	obtener el Estudiante O(1)
copiar examen DW completo O(R)
borrar el mínimo O(log E)
recalcular puntaje O(R)
reinsertar O(log E)

TOTAL: O(k (R + log(E)))

notas:
Creamos una lista y le insertamos cada estudiante de arregloEstudiantes O(E)

TOTAL: O(E)

entregar:
Preguntar a Daniela


chequearCopias:

Por cada estudiante: O(E)
	Por cada respuesta: O(R)
		Comparo respuesta con cantidad de personas con la misma respuesta en el                          mismo punto. 
		Sumo 1 a un contador 
		Comparo contador con cantidad de respuestas
		Lo agrego a la lista res si es sospechoso

TOTAL: O(E * R)




corregir:
Por cada Estudiante: O(E)
Si no es sospechoso: O(1)
	Lo agregamos a un maxheap O(log E)
