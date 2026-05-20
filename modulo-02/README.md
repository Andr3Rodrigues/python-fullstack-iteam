"""
=============================================================
GABARITO – Módulo 2: Estruturas de Controle
Curso de Capacitação Full Stack – ITEAM
Professor: Msc. Hygo Sousa De Oliveira
=============================================================
⚠️  ATENÇÃO: Este arquivo é exclusivo para o professor.
    Suba-o na branch 'gabarito', não na 'main'.
=============================================================
"""


# ==============================================================
# EXERCÍCIO 01 – Classificador de Temperatura
# ==============================================================
def ex01_classificador_temperatura():
    try:
        temp = float(input("Digite a temperatura em °C: "))
    except ValueError:
        print("Entrada inválida. Digite um número.")
        return

    if temp < 0:
        classificacao = "❄️ Congelante"
    elif temp <= 14:
        classificacao = "🥶 Frio"
    elif temp <= 24:
        classificacao = "😊 Agradável"
    elif temp <= 34:
        classificacao = "☀️ Quente"
    else:
        classificacao = "🔥 Muito quente"

    print(f"Temperatura: {temp}°C")
    print(f"Classificação: {classificacao}")


# ==============================================================
# EXERCÍCIO 02 – Validador de Acesso
# ==============================================================
def ex02_validador_acesso():
    usuario = input("Usuário: ")
    senha   = input("Senha: ")

    # Verifica o usuário primeiro para não revelar qual campo está errado
    if usuario != "admin":
        print("❌ Usuário não encontrado.")
    elif senha != "iteam2025":
        print("❌ Senha incorreta.")
    else:
        print("✅ Acesso liberado. Bem-vindo!")


# ==============================================================
# EXERCÍCIO 03 – Tabuada Interativa
# ==============================================================
def ex03_tabuada():
    try:
        numero = int(input("Digite um número inteiro: "))
    except ValueError:
        print("Entrada inválida.")
        return

    print(f"\n=== Tabuada do {numero} ===")
    for i in range(1, 11):
        resultado = numero * i
        # {:>2} alinha o multiplicador à direita em 2 chars
        # {:>3} alinha o resultado à direita em 3 chars
        print(f"{numero} x {i:>2} = {resultado:>3}")


# ==============================================================
# EXERCÍCIO 04 – Contador Regressivo
# ==============================================================
def ex04_contador_regressivo():
    try:
        n = int(input("Digite um número inteiro positivo: "))
        if n < 0:
            print("O número deve ser positivo.")
            return
    except ValueError:
        print("Entrada inválida.")
        return

    while n >= 0:
        print(f"{n}...", end=" ")
        n -= 1

    print("\n🚀 Lançamento!")


# ==============================================================
# EXERCÍCIO 05 – Buscador com break
# ==============================================================
def ex05_buscador_break():
    estoque  = ["Teclado", "Mouse", "Webcam", "Monitor", "Headset", "Notebook"]
    alvo     = "Monitor"
    encontrado = False

    for indice, produto in enumerate(estoque):
        if produto == alvo:
            encontrado = True
            break  # Para assim que achar — não percorre o restante

    if encontrado:
        print(f"'{alvo}' encontrado na posição {indice} do estoque.")
    else:
        print("Produto não encontrado no estoque.")


# ==============================================================
# EXERCÍCIO 06 – Filtro de Dados com continue
# ==============================================================
def ex06_filtro_continue():
    leituras = [12.5, None, 8.3, None, 15.0, 9.7, None, 11.2, 6.8, None]

    soma     = 0.0
    validos  = 0
    ignorados = 0

    for leitura in leituras:
        if leitura is None:
            ignorados += 1
            continue  # Pula o restante da iteração para valores None

        soma    += leitura
        validos += 1

    media = soma / validos if validos > 0 else 0

    print(f"Soma dos válidos  : {soma:.2f}")
    print(f"Média dos válidos : {media:.2f}")
    print(f"Registros ignorados: {ignorados}")


# ==============================================================
# EXERCÍCIO 07 – Validação de Entrada com while
# ==============================================================
def ex07_validacao_nota():
    nota = None

    while True:
        try:
            nota = float(input("Digite a nota do aluno (0.0 a 10.0): "))
        except ValueError:
            print("⚠️ Entrada inválida. Digite um número.")
            continue  # Volta ao início do while sem executar o resto

        if 0.0 <= nota <= 10.0:
            break  # Entrada válida — sai do loop
        else:
            print("⚠️ Nota fora do intervalo permitido. Tente novamente.")

    if nota >= 9.0:
        conceito = "A – Excelente"
    elif nota >= 7.0:
        conceito = "B – Bom"
    elif nota >= 5.0:
        conceito = "C – Regular"
    else:
        conceito = "D – Insuficiente"

    print(f"Nota: {nota:.1f} | Conceito: {conceito}")


# ==============================================================
# EXERCÍCIO 08 – Calculadora com try/except
# ==============================================================
def ex08_calculadora_segura():
    try:
        a  = float(input("Primeiro número : "))
        b  = float(input("Segundo número  : "))
        op = input("Operação (+, -, *, /): ").strip()

        if op == "+":
            resultado = a + b
        elif op == "-":
            resultado = a - b
        elif op == "*":
            resultado = a * b
        elif op == "/":
            resultado = a / b   # Pode lançar ZeroDivisionError
        else:
            raise ValueError(f"Operação '{op}' não é válida.")

    except ValueError as e:
        print(f"❌ Erro de valor: {e}")
    except ZeroDivisionError:
        print("❌ Erro: divisão por zero não é permitida.")
    else:
        # Executado APENAS quando nenhuma exceção ocorre
        print(f"✅ Resultado: {a} {op} {b} = {resultado:.4f}")
    finally:
        # Executado SEMPRE, independentemente de erro ou não
        print("Calculadora encerrada.")


# ==============================================================
# EXERCÍCIO 09 – Padrão Numérico com for aninhado
# ==============================================================
def ex09_padrao_numerico():
    n = 5

    # Triângulo crescente
    for i in range(1, n + 1):
        for j in range(1, i + 1):
            print(j, end=" ")
        print()  # Quebra de linha após cada linha do padrão

    # Desafio extra — triângulo decrescente
    for i in range(n, 0, -1):
        for j in range(1, i + 1):
            print(j, end=" ")
        print()


# ==============================================================
# EXERCÍCIO 10 – Jogo de Adivinhação
# ==============================================================
def ex10_jogo_adivinhacao():
    import random

    numero_secreto = random.randint(1, 100)
    tentativas_max = 7
    tentativa      = 0
    acertou        = False

    print("🎮 Adivinhe o número entre 1 e 100! Você tem 7 tentativas.")

    while tentativa < tentativas_max:
        tentativa += 1

        try:
            chute = int(input(f"\nTentativa {tentativa}/{tentativas_max}: "))
        except ValueError:
            print("⚠️ Digite apenas números inteiros.")
            tentativa -= 1  # Não conta tentativa inválida
            continue

        if chute == numero_secreto:
            acertou = True
            break
        elif chute < numero_secreto:
            print("📈 O número secreto é MAIOR.")
        else:
            print("📉 O número secreto é MENOR.")

    if acertou:
        print(f"\n🎉 Parabéns! Você acertou em {tentativa} tentativa(s).")
    else:
        print(f"\n💀 Game over! O número era {numero_secreto}.")


# ==============================================================
# EXERCÍCIO 11 – Verificador de Número Primo
# ==============================================================
def ex11_numero_primo():
    try:
        n = int(input("Digite um número inteiro positivo: "))
        if n <= 0:
            print("❌ O número deve ser positivo e maior que zero.")
            return
    except ValueError:
        print("❌ Entrada inválida. Digite um número inteiro.")
        return

    if n == 1:
        print(f"{n} não é primo (1 é caso especial).")
        return

    primo     = True
    divisor   = None

    # Otimização: verifica até √n — qualquer fator > √n tem um par < √n
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            primo   = False
            divisor = i
            break  # Para no primeiro divisor encontrado

    if primo:
        print(f"{n} é um número primo. ✅")
    else:
        print(f"{n} não é primo. Divisível por {divisor}. ❌")


# ==============================================================
# EXERCÍCIO 12 – Analisador de Senha Forte
# ==============================================================
def ex12_analisador_senha():
    senha = input("Digite a senha para análise: ")

    especiais      = "!@#$%^&*"
    tem_maiuscula  = False
    tem_minuscula  = False
    tem_digito     = False
    tem_especial   = False

    # Percorre caractere por caractere registrando os critérios
    for char in senha:
        if char.isupper():
            tem_maiuscula = True
        if char.islower():
            tem_minuscula = True
        if char.isdigit():
            tem_digito = True
        if char in especiais:
            tem_especial = True

    comprimento_ok = len(senha) >= 8

    print(f"\nAnalisando: {senha}")
    print(f"{'✅' if comprimento_ok else '❌'} Comprimento adequado ({len(senha)} caracteres)")
    print(f"{'✅' if tem_maiuscula  else '❌'} Contém maiúscula")
    print(f"{'✅' if tem_minuscula  else '❌'} Contém minúscula")
    print(f"{'✅' if tem_digito     else '❌'} Contém número")
    print(f"{'✅' if tem_especial   else '❌'} Contém caractere especial")

    todos = all([comprimento_ok, tem_maiuscula, tem_minuscula, tem_digito, tem_especial])
    print(f"\n{'🔒 Senha FORTE!' if todos else '⚠️  Senha FRACA — melhore os critérios acima.'}")


# ==============================================================
# EXERCÍCIO 13 – Simulador de Caixa Eletrônico
# ==============================================================
def ex13_caixa_eletronico():
    cedulas = [200, 100, 50, 20, 10]

    try:
        valor = int(input("Digite o valor do saque (R$): "))
    except ValueError:
        print("❌ Valor inválido. Digite um número inteiro.")
        return

    if valor % 10 != 0:
        print("❌ O valor deve ser múltiplo de R$10.")
        return
    if valor <= 0 or valor > 3000:
        print("❌ Valor fora do limite permitido (R$10 a R$3.000).")
        return

    print(f"\n💵 Saque: R$ {valor}")
    print("Cédulas utilizadas:")

    total_cedulas = 0
    restante      = valor

    for cedula in cedulas:
        quantidade = restante // cedula   # Quantas cédulas desta denominação
        if quantidade > 0:
            print(f"  R${cedula:<3} → {quantidade} cédula(s)")
            total_cedulas += quantidade
            restante -= quantidade * cedula   # Atualiza o restante

        if restante == 0:
            break  # Para se já não há mais valor a distribuir

    print(f"Total de cédulas: {total_cedulas}")


# ==============================================================
# EXERCÍCIO 14 – Leitura de Múltiplos Dados com Tratamento
# ==============================================================
def ex14_leitura_notas_turma():
    notas = []

    print("Digite as notas dos alunos (0 a 10). Digite 'fim' para encerrar.")

    while True:
        entrada = input("Nota: ").strip()

        if entrada.lower() == "fim":
            break  # Encerra a coleta de notas

        try:
            nota = float(entrada)
        except ValueError:
            print("⚠️ Entrada não numérica. Ignorada.")
            continue  # Pula para a próxima iteração

        if not (0.0 <= nota <= 10.0):
            print("⚠️ Nota fora do intervalo (0 a 10). Ignorada.")
            continue

        notas.append(nota)

    if not notas:
        print("Nenhuma nota válida registrada.")
        return

    print(f"\n📊 Relatório da Turma")
    print(f"  Total de notas válidas : {len(notas)}")
    print(f"  Média                  : {sum(notas) / len(notas):.2f}")
    print(f"  Maior nota             : {max(notas):.1f}")
    print(f"  Menor nota             : {min(notas):.1f}")


# ==============================================================
# EXERCÍCIO 15 – Desafio Final: Menu de Sistema
# ==============================================================
def ex15_menu_sistema():

    def _conversor_temperatura():
        """Versão simplificada do Ex01."""
        try:
            c = float(input("Temperatura em °C: "))
            f = (c * 9 / 5) + 32
            print(f"{c}°C = {f:.2f}°F")
        except ValueError:
            print("⚠️ Entrada inválida.")

    def _verificador_primo():
        """Versão simplificada do Ex11."""
        try:
            n = int(input("Número inteiro positivo: "))
            if n < 2:
                print("Não é primo.")
                return
            for i in range(2, int(n ** 0.5) + 1):
                if n % i == 0:
                    print(f"{n} não é primo.")
                    return
            print(f"{n} é primo. ✅")
        except ValueError:
            print("⚠️ Entrada inválida.")

    def _analisador_senha():
        """Versão simplificada: comprimento e dígito."""
        senha = input("Senha: ")
        ok = len(senha) >= 8 and any(c.isdigit() for c in senha)
        print("✅ Senha aceitável." if ok else "❌ Senha muito curta ou sem dígito.")

    def _calculadora():
        """Versão simplificada do Ex08."""
        try:
            a  = float(input("Número A: "))
            b  = float(input("Número B: "))
            op = input("Operação (+,-,*,/): ").strip()
            ops = {"+": a + b, "-": a - b, "*": a * b}
            if op == "/":
                if b == 0:
                    print("❌ Divisão por zero.")
                    return
                print(f"Resultado: {a / b:.4f}")
            elif op in ops:
                print(f"Resultado: {ops[op]:.4f}")
            else:
                print("❌ Operação inválida.")
        except ValueError:
            print("⚠️ Entrada inválida.")

    # ── Loop principal do menu ──────────────────────────────
    while True:
        print("\n" + "=" * 29)
        print("   SISTEMA ITEAM - MENU    ")
        print("=" * 29)
        print("[1] Conversor de temperatura")
        print("[2] Verificador de número primo")
        print("[3] Analisador de senha")
        print("[4] Calculadora segura")
        print("[0] Sair")
        print("=" * 29)

        try:
            opcao = int(input("Escolha uma opção: "))
        except ValueError:
            print("⚠️ Digite apenas números.")
            continue  # Opção inválida — volta ao menu

        if opcao == 0:
            print("👋 Encerrando o sistema. Até logo!")
            break
        elif opcao == 1:
            _conversor_temperatura()
        elif opcao == 2:
            _verificador_primo()
        elif opcao == 3:
            _analisador_senha()
        elif opcao == 4:
            _calculadora()
        else:
            print("⚠️ Opção não existe. Tente novamente.")
            continue  # Opção fora do range — volta ao menu


# ==============================================================
# EXECUÇÃO DO GABARITO
# ==============================================================
if __name__ == "__main__":
    funcoes = [
        ex01_classificador_temperatura,
        ex02_validador_acesso,
        ex03_tabuada,
        ex04_contador_regressivo,
        ex05_buscador_break,
        ex06_filtro_continue,
        ex07_validacao_nota,
        ex08_calculadora_segura,
        ex09_padrao_numerico,
        ex10_jogo_adivinhacao,
        ex11_numero_primo,
        ex12_analisador_senha,
        ex13_caixa_eletronico,
        ex14_leitura_notas_turma,
        ex15_menu_sistema,
    ]

    for i, fn in enumerate(funcoes, 1):
        print(f"\n{'=' * 50}")
        print(f"EXERCÍCIO {i:02d} – {fn.__name__}")
        print("=" * 50)
        fn()
