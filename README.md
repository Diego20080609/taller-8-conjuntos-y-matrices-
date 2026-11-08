"""
Ejercicio 1: análisis de una matriz de ventas.
Filas = vendedores, columnas = semanas (valores en millones de pesos).
Sin librerías externas: listas anidadas, ciclos for y acumuladores.
"""

ventas = [
    [12, 15, 10, 18],
    [8, 14, 16, 12],
    [20, 18, 15, 22],
]


def mostrar_matriz(matriz):
    """1. Muestra la matriz indicando vendedor y semana."""
    print("\n=== MATRIZ DE VENTAS (millones de pesos) ===")
    encabezado = f"{'':<12}"
    for j in range(len(matriz[0])):
        encabezado += f"{'Semana ' + str(j + 1):>10}"
    print(encabezado)
    for i in range(len(matriz)):
        linea = f"{'Vendedor ' + str(i + 1):<12}"
        for j in range(len(matriz[i])):
            linea += f"{matriz[i][j]:>10}"
        print(linea)


def totales_por_vendedor(matriz):
    """2. Total de cada vendedor (recorre cada fila)."""
    totales = []
    for fila in matriz:
        acumulador = 0
        for valor in fila:
            acumulador += valor
        totales.append(acumulador)
    return totales


def totales_por_semana(matriz):
    """3. Total de cada semana (recorre cada columna)."""
    totales = []
    for j in range(len(matriz[0])):
        acumulador = 0
        for i in range(len(matriz)):
            acumulador += matriz[i][j]
        totales.append(acumulador)
    return totales


def posicion_del_mayor(lista):
    """Devuelve el índice del mayor valor de una lista (sin usar max)."""
    indice_mayor = 0
    for i in range(1, len(lista)):
        if lista[i] > lista[indice_mayor]:
            indice_mayor = i
    return indice_mayor


def promedio_general(matriz):
    """6. Promedio de todas las ventas de la matriz."""
    suma = 0
    cantidad = 0
    for fila in matriz:
        for valor in fila:
            suma += valor
            cantidad += 1
    return suma / cantidad


def mostrar_analisis(matriz):
    mostrar_matriz(matriz)

    tot_vend = totales_por_vendedor(matriz)
    print("\n--- Total de ventas por vendedor ---")
    for i in range(len(tot_vend)):
        print(f"Vendedor {i + 1}: {tot_vend[i]} millones")

    tot_sem = totales_por_semana(matriz)
    print("\n--- Total de ventas por semana ---")
    for j in range(len(tot_sem)):
        print(f"Semana {j + 1}: {tot_sem[j]} millones")

    mejor_v = posicion_del_mayor(tot_vend)
    print(f"\nVendedor con mayores ventas: Vendedor {mejor_v + 1} "
          f"({tot_vend[mejor_v]} millones)")

    mejor_s = posicion_del_mayor(tot_sem)
    print(f"Semana con mayor volumen de ventas: Semana {mejor_s + 1} "
          f"({tot_sem[mejor_s]} millones)")

    print(f"Promedio general de ventas: {promedio_general(matriz):.2f} millones")


def pedir_entero(mensaje, minimo, maximo):
    """Pide un entero dentro de un rango y repite hasta que sea válido."""
    while True:
        try:
            valor = int(input(mensaje))
            if minimo <= valor <= maximo:
                return valor
            print(f"  Debe estar entre {minimo} y {maximo}.")
        except ValueError:
            print("  Ingrese un número entero válido.")


def modificar_venta(matriz):
    """7. Modifica la venta de un vendedor en una semana."""
    print("\n=== MODIFICAR UNA VENTA ===")
    vendedor = pedir_entero(f"Vendedor (1-{len(matriz)}): ", 1, len(matriz))
    semana = pedir_entero(f"Semana (1-{len(matriz[0])}): ", 1, len(matriz[0]))
    nuevo = pedir_entero("Nuevo valor de ventas (millones): ", 0, 10**6)

    anterior = matriz[vendedor - 1][semana - 1]
    matriz[vendedor - 1][semana - 1] = nuevo
    print(f"Vendedor {vendedor}, Semana {semana}: {anterior} -> {nuevo}")


def main():
    print("########## RESULTADOS INICIALES ##########")
    mostrar_analisis(ventas)

    modificar_venta(ventas)

    print("\n########## RESULTADOS ACTUALIZADOS ##########")
if name == "diego"
    main()
    mostrar_analisis(ventas)


if _name_ == "_main_":
