# nelson
prueba
import random
import time

# Definir los caracteres para representar las cartas y la arena
CARACTER_CARTA = "C"
CARACTER_ARENA = "="

# Definir los mazos
mazo1 = ["Carta 1", "Carta 2", "Carta 3", "Carta 4", "Carta 5", "Carta 6", "Carta 7", "Carta 8"]
mazo2 = ["Carta 9", "Carta 10", "Carta 11", "Carta 12", "Carta 13", "Carta 14", "Carta 15", "Carta 16"]

# Definir la arena
arena = [[CARACTER_ARENA] * 10 for _ in range(5)]


def mostrar_arena():
    print("------ ARENA ------")
    for fila in arena:
        print(" ".join(fila))
    print("-------------------")


def mostrar_mazo(mazo):
    print("------ MAZO ------")
    for i, carta in enumerate(mazo, start=1):
        print(f"{i}. {carta}")
    print("-------------------")


def seleccionar_carta(mazo):
    mostrar_mazo(mazo)

    while True:
        seleccion = input("Selecciona una carta: ")
        if seleccion.isdigit() and 1 <= int(seleccion) <= len(mazo):
            return mazo[int(seleccion)-1]
        else:
            print("Selección inválida. Inténtalo nuevamente.")


def colocar_carta(carta):
    fila = random.randint(0, 4)
    columna = random.randint(0, 9)

    if arena[fila][columna] == CARACTER_ARENA:
        arena[fila][columna] = CARACTER_CARTA
        print(f"¡{carta} ha sido colocada en la arena!")
    else:
        print("No se pudo colocar la carta. Espacio ocupado.")


# Juego principal
print("¡Bienvenido a Clash Royale!")
time.sleep(1)

# Jugador 1 selecciona una carta
print("Jugador 1:")
carta_jugador1 = seleccionar_carta(mazo1)
colocar_carta(carta_jugador1)

time.sleep(1)

# Jugador 2 selecciona una carta
print("Jugador 2:")
carta_jugador2 = seleccionar_carta(mazo2)
colocar_carta(carta_jugador2)

time.sleep(1)

# Mostrar la arena actualizada
mostrar_arena()

time.sleep(1)

# Simular el combate
print(f"¡{carta_jugador1} vs {carta_jugador2}!")
time.sleep(1)

# Determinar el ganador
ganador = random.choice([1, 2])

if ganador == 1:
    print("¡Jugador 1 gana el combate!")
else:
    print("¡Jugador 2 gana el combate!")

time.sleep(1)

print("¡Gracias por jugar a Clash Royale!")
