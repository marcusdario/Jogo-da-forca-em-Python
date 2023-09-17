# Jogo-da-forca-em-Python
Jogo da forca em pyton codificação:

import random

# Lista de palavras para o jogo
palavras = ["python", "java", "ruby", "javascript", "html", "css"]

# Escolha uma palavra aleatória da lista
palavra_escolhida = random.choice(palavras)

# Inicialização de variáveis
tentativas = 6
letras_certas = []
letras_erradas = []

# Função para exibir a palavra oculta com traços
def exibir_palavra_oculta(palavra, letras_certas):
    resultado = ""
    for letra in palavra:
        if letra in letras_certas:
            resultado += letra
        else:
            resultado += "_"
    return resultado

# Loop principal do jogo
while True:
    # Exibir a palavra oculta
    palavra_oculta = exibir_palavra_oculta(palavra_escolhida, letras_certas)
    print("\nPalavra: " + palavra_oculta)

    # Exibir letras erradas
    print("Letras erradas: " + ", ".join(letras_erradas))

    # Verificar se o jogador ganhou
    if palavra_oculta == palavra_escolhida:
        print("\nVocê ganhou! A palavra era: " + palavra_escolhida)
        break

    # Verificar se o jogador perdeu
    if tentativas == 0:
        print("\nVocê perdeu! A palavra era: " + palavra_escolhida)
        break

    # Solicitar uma letra ao jogador
    letra = input("\nDigite uma letra: ").lower()

    # Verificar se a letra é válida
    if len(letra) != 1 or not letra.isalpha():
        print("Por favor, digite uma letra válida.")
        continue

    # Verificar se a letra já foi tentada
    if letra in letras_certas or letra in letras_erradas:
        print("Você já tentou esta letra antes.")
        continue

    # Verificar se a letra está na palavra
    if letra in palavra_escolhida:
        letras_certas.append(letra)
    else:
        letras_erradas.append(letra)
        tentativas -= 1
