# """

Programa que cria um arquivo texto e insere 'n' registros de informação de usuários

"""

# Criando um arquivo texto com o nome baseado no input do usuário
nome_arquivo = str(input('Digite o nome do arquivo (a extensão será .txt): '))

# abrindo o arquivo
arquivo = open(nome_arquivo + '.txt', 'w')

# lendo a quantidade de usuários que deverão ser criados (utilizado no loop como variável de parada)
quantidade_cadastros = int(input('Digite quantos usuários você quer cadastrar: ').strip())

# Criando lista vazia para armazenar os cadastros
lista_cadastros = []


for cadastro in range(quantidade_cadastros):
    # Colhendo inputs do usuário
    codigo = input('Digite o código do usuario: ').strip()
    nome = input('Digite o nome do usuario: ').strip()
    email = input('Digite o e-mail: ').strip()
    idade = input('Digite a idade: ').strip()
    telefone = input('Digite o telefone: ').strip()

    # Adicionando valores a lista de cadastros (lista de dicionários)
    lista_cadastros.append({
        'codigo': codigo,
        'nome': nome,
        'email': email,
        'idade': idade,
        'telefone': telefone
    })
# Ordenação de dados pelo Código
def bubleorder(lista_cadastros):
    for num, i in enumerate(lista_cadastros):
        for num2, j in enumerate(lista_cadastros):
            print(str(num) + " " + str(num2))
            if int(i['codigo']) < int(j['codigo']):
                aux = lista_cadastros[num2]
                lista_cadastros[num2] = lista_cadastros[num]
                lista_cadastros[num] = aux
    return lista_cadastros

# Ordenando a lista pela chave "codigo" em cada dicionário.
lista_cadastros_ordenada = bubleorder(lista_cadastros)

for cadastro in lista_cadastros_ordenada:
    print(cadastro)
    arquivo.write(str(cadastro))
    arquivo.write('\n')

arquivo.close()

