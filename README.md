
import math

# Obtener los datos del usuario
H = float(input("Altura de la sección transversal (H): "))
B = float(input("Anchura de la brida (B): "))
t = float(input("Anchura del alma (t): "))
tf = float(input("Espesor de la brida (tf): "))
tw = float(input("Espesor del alma (tw): "))
L = float(input("Longitud del perfil (L): "))
E = float(input("Módulo de elasticidad del acero (E): "))
fy = float(input("Límite elástico del acero (fy): "))

# Calcular el área de la sección transversal del perfil
A = 2 * tf * B + (H - 2 * tf) * t

# Calcular el momento de inercia respecto al eje X
Ix = (2 * tf * B * ((H / 2) - tf) ** 2) + (t * (H - 2 * tf) ** 3 / 12)

# Calcular el momento flector máximo (asumiendo una carga uniformemente distribuida)
M = (L ** 2) * (fy * A) / 8

# Calcular la carga axial máxima (asumiendo una carga uniformemente distribuida)
N = (L ** 2) * (fy * A) / (2 * math.pi ** 2 * E * ((t / H) ** 3 / 3 + (tf / H) * (1 - tf / H) ** 2))

# Calcular el esfuerzo máximo
sigma_max = ((M * H) / (2 * Ix)) + ((N * tf) / A) + ((N * tw) / A)

# Imprimir el resultado
print("El esfuerzo máximo del perfil de acero tipo H es:", sigma_max, "MPa")
