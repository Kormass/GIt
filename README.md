import json

# Lista de animales con precios
catalogo_animales = {
    "Perro": 100,
    "Gato": 50,
    "Elefante": 1000,
    "León": 800,
    "Tigre": 900
}

# Crear un menú
def mostrar_menu():
    print("Catálogo de Animales:")
    for i, (animal, precio) in enumerate(catalogo_animales.items()):
        print(f"{i+1}. {animal} - ${precio}")
    print("0. Salir")

# Obtener la selección y realizar la compra
def obtener_seleccion():
    while True:
        try:
            seleccion = int(input("Seleccione un animal para comprar (0 para salir): "))
            if 0 <= seleccion <= len(catalogo_animales):
                return seleccion
            else:
                print("Selección inválida. Intente nuevamente.")
        except ValueError:
            print("Entrada inválida. Intente nuevamente.")

# Realizar la compra y guardar en archivo JSON
def realizar_compra(animal_seleccionado):
    precio = catalogo_animales[animal_seleccionado]
    print(f"Compraste un {animal_seleccionado} por ${precio}. ¡Disfrútalo!")

    # Crear un archivo JSON con la compra
    with open("compra_animal.json", "w") as archivo_json:
        json.dump({"animal_comprado": animal_seleccionado, "precio": precio}, archivo_json)
    print("Compra guardada en 'compra_animal.json'.")

# Programa principal
def main():
    mostrar_menu()
    seleccion = obtener_seleccion()
    
    if seleccion == 0:
        print("Saliendo...")
    else:
        animal_seleccionado = list(catalogo_animales.keys())[seleccion - 1]
        realizar_compra(animal_seleccionado)

if __name__ == "__main__":
    main()
    # GIt
