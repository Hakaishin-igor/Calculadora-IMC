#Calculadora IMC
#By HakaishinIgor

def calcular_imc(peso, altura):
    return peso / (altura ** 2)

def avaliar_peso(imc):
    if imc < 18.5:
        return "Abaixo do peso"
    elif 18.5 <= imc < 24.9:
        return "Peso normal"
    elif 25 <= imc < 29.9:
        return "Acima do peso"
    else:
        return "Obesidade"

def grau_obesidade(imc):
    if imc >= 30:
        return "Obesidade Grau I"
    elif imc >= 35:
        return "Obesidade Grau II"
    elif imc >= 40:
        return "Obesidade Grau III"
    else:
        return ""

def calcular_gasto_calorico_diario(idade, peso, altura, pratica_esporte):
    # Fator de atividade física
    fator_atividade = 1.375 if pratica_esporte else 1.2

    # Fórmula de Harris-Benedict para calcular o gasto calórico diário
    gasto_calorico_diario = (10 * peso) + (6.25 * altura * 100) - (5 * idade) + 5
    gasto_calorico_diario *= fator_atividade

    return gasto_calorico_diario

def main():
    nome = input("Digite seu nome: ")
    idade = int(input("Digite sua idade: "))
    peso = float(input("Digite seu peso em kg: "))
    altura = float(input("Digite sua altura em metros: "))
    esporte = input("Você pratica algum esporte? (Sim/Não): ")

    pratica_esporte = esporte.lower() == 'sim'

    imc = calcular_imc(peso, altura)
    resultado_peso = avaliar_peso(imc)

    print(f"\nNome: {nome}")
    print(f"Idade: {idade} anos")
    print(f"Peso: {peso} kg")
    print(f"Altura: {altura} metros")
    print(f"Pratica esporte: {esporte}")

    print(f"\nResultado do IMC: {imc:.2f} - {resultado_peso}")

    if resultado_peso == "Obesidade":
        print(f"Grau de obesidade: {grau_obesidade(imc)}")

    gasto_calorico_diario = calcular_gasto_calorico_diario(idade, peso, altura, pratica_esporte)
    print(f"Gasto calórico diário estimado: {gasto_calorico_diario:.2f} calorias")

if __name__ == "__main__":
    main()
