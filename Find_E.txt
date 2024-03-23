from decimal import Decimal, getcontext

def calcular_e(n_casas):
    getcontext().prec = n_casas + 1
    e = Decimal(0)
    k = 0
    while True:
        termo = Decimal(1) / Decimal(factorial(k))
        if abs(termo) < 10**(-n_casas):
            break
        e += termo
        k += 1
    return e

def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n-1)

while True:
    try:
        n = int(input("Insira o número de casas decimais desejado para 'e' (ou -1 para sair): "))
        if n == -1:
            print("Encerrando o programa.")
            break
        elif n < 0:
            print("Por favor, digite um número positivo ou -1 para sair.")
        else:
            print("O valor de 'e' com", n, "casas decimais é:")
            print(calcular_e(n))
    except ValueError:
        print("Entrada inválida. Por favor, digite um número inteiro.")
