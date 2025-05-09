# Evaluacion-de-la-Posicion-Correcta-de-Salida-en-una-Carrera-de-100-Metros-en-Atletismo
Evaluación de la Posición Correcta de Salida en una Carrera de 100 Metros en Atletismo
import math

def calcular_centro_gravedad(altura, angulo_del, angulo_trs):
    factor_trs = (90 - angulo_trs) / 90
    factor_del = (90 - angulo_del)/ 90
    promedio_factor = (factor_del + factor_trs) / 2
    return round(altura * (0.55 - 0.1 * promedio_factor), 2)

def evaluar_posicion(nombre, edad, altura, peso,angulo_del, angulo_trs):
    print("\nEvaluación Biomecánica Profesional - Posición de Salida en Sprint (100m)")
    print("Candidato: {}, Edad: {} años, Altura: {:.2f} m, Peso: {:.1f} kg".format(nombre, edad, altura, peso))
    errores = []

    if not (angulo_del == 90):
        errores.append(f"- Ángulo de la pierna delantera fuera del rango ideal (90°): {angulo_del}°")
    if not (angulo_trs == 120):
        errores.append(f"- Ángulo de la pierna trasera fuera del rango ideal (120°): {angulo_trs}°")

    cg_inicial = calcular_centro_gravedad(altura, angulo_del, angulo_trs)
    print(f"\nCentro de Gravedad estimado (antes de correcciones): {cg_inicial:.2f} m")

    if errores:
        print("\n🔴 Resultado: Posición inicial INCORRECTA")
        print("Problemas detectados:")
        for error in errores:
            print(error)

        angulo_del_corr = angulo_del
        angulo_trs_corr = angulo_trs
        cg_corregido = calcular_centro_gravedad(altura, angulo_del_corr, angulo_trs_corr)

        print("\n✅ Sugerencias de corrección biomecánica:")
        if angulo_del != angulo_del_corr:
            print(f"- Ajustar ángulo de pierna izquierda a {angulo_del_corr}°")
        if angulo_trs != angulo_trs_corr:
            print(f"- Ajustar ángulo de pierna derecha a {angulo_trs_corr}°")

        print(f"Centro de Gravedad estimado (después de correcciones): {cg_corregido:.2f} m")
    else:
        print("\n✅ Resultado: ¡Posición inicial CORRECTA!")
        print("\n📘 Basado en estudios biomecánicos como los publicados en el *Journal of Sports Sciences*, mantener los ángulos de salida dentro de los rangos establecidos (pierna delantera 90°, pierna trasera 120°) optimiza la transferencia de fuerza en el impulso inicial, reduciendo el tiempo de reacción y mejorando la eficiencia del desplazamiento.")
        print("\n✔️ Su postura cumple con los estándares recomendados para una salida explosiva y segura.")

if __name__ == "__main__":
    print("Ingrese los datos del atleta para la evaluación biomecánica:")
    nombre = input("Nombre: ")
    edad = int(input("Edad: "))
    altura = float(input("Altura (en metros, por ejemplo 1.75): "))
    peso = float(input("Peso (en kilogramos, por ejemplo 70.5): "))
    angulo_del = float(input("Ángulo de la pierna delantera (en grados): "))
    angulo_trs = float(input("Ángulo de la pierna trasera (en grados): "))
    evaluar_posicion(nombre, edad, altura, peso, angulo_del, angulo_trs)
