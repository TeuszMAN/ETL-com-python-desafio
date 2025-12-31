# 🔄 ETL com Python - Desafio DIO

## 📋 Descrição

Este projeto implementa um pipeline ETL (Extract, Transform, Load) em Python para processamento de dados de contatos. O objetivo é demonstrar como extrair dados de um arquivo CSV, transformá-los aplicando formatações padronizadas e exportá-los em formato JSON.

### O que faz este projeto?

1. **Extração (Extract)**: Lê dados de um arquivo CSV contendo informações de contatos (nome, endereço, telefone)
2. **Transformação (Transform)**: 
   - Separa o endereço em componentes: rua, número e bairro usando expressões regulares
   - Formata números de telefone para o padrão brasileiro: `(DDD) XXXXX-XXXX`
3. **Carregamento (Load)**: Exporta os dados transformados em formato JSON estruturado

## 🚀 Tecnologias Utilizadas

- **Python 3.x**
- **Pandas** - Manipulação e análise de dados
- **Regex (re)** - Expressões regulares para transformação de strings
- **JSON** - Serialização de dados
- **Jupyter Notebook** - Ambiente interativo de desenvolvimento

## 📁 Estrutura do Projeto

```
ETL-com-python-desafio/
│
├── README.md                           # Documentação do projeto
├── requirements.txt                    # Dependências do projeto
├── sample.ipynb                        # Notebook com o código ETL
└── data/
    └── Dio - desafio - Página1.csv    # Arquivo CSV de entrada
```

## 📊 Dados de Entrada

O arquivo CSV de entrada contém as seguintes colunas:

| Coluna   | Descrição                                    | Exemplo                                   |
|----------|----------------------------------------------|-------------------------------------------|
| nome     | Nome do contato                              | Lucas                                     |
| endereco | Endereço completo (rua, número e bairro)     | Rua das flores, 123 - Jd Primavera        |
| telefone | Número de telefone (formatos variados)       | 19999999999, (19) 98743-1212              |

## 📤 Dados de Saída

Após o processamento, os dados são transformados em JSON com a seguinte estrutura:

```json
[
    {
        "nome": "Lucas",
        "rua": "Rua das flores",
        "numero": "123",
        "bairro": "Jd Primavera",
        "telefone": "(19) 99999-9999"
    }
]
```

## ⚙️ Instalação

1. Clone o repositório:
```bash
git clone https://github.com/TeuszMAN/ETL-com-python-desafio.git
cd ETL-com-python-desafio
```

2. Crie um ambiente virtual (opcional, mas recomendado):
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
# ou
venv\Scripts\activate     # Windows
```

3. Instale as dependências:
```bash
pip install -r requirements.txt
```

## 🎯 Como Usar

1. Abra o Jupyter Notebook:
```bash
jupyter notebook sample.ipynb
```

2. Execute todas as células do notebook sequencialmente

3. O resultado será exibido no formato JSON ao final da execução

## 🔧 Funções Principais

### `separar_endereco(endereco)`
Utiliza regex para separar o endereço em três componentes:
- **Rua**: Nome da via
- **Número**: Número do imóvel
- **Bairro**: Nome do bairro

### `formatar_telefone(telefone)`
Formata números de telefone para o padrão brasileiro:
- Telefones com 11 dígitos (DDD + número): Formata para `(DDD) XXXXX-XXXX`
- Telefones com 9 dígitos (apenas número, sem DDD): Assume DDD 19 e formata para `(19) XXXXX-XXXX`

## 📝 Exemplo de Transformação

**Antes:**
| nome    | endereco                           | telefone        |
|---------|------------------------------------|-----------------|
| Lucas   | Rua das flores, 123 - Jd Primavera | 19999999999     |
| Vanessa | Rua do Bem te vi, 33 - Jd Bosque   | 955555555       |
| Tiago   | Av do Falcão, 99 - Jd Bosque       | (19) 98743-1212 |

**Depois:**
| nome    | rua              | numero | bairro       | telefone        |
|---------|------------------|--------|--------------|-----------------|
| Lucas   | Rua das flores   | 123    | Jd Primavera | (19) 99999-9999 |
| Vanessa | Rua do Bem te vi | 33     | Jd Bosque    | (19) 95555-5555 |
| Tiago   | Av do Falcão     | 99     | Jd Bosque    | (19) 98743-1212 |

## 📄 Licença

Este projeto foi desenvolvido como parte do desafio da [Digital Innovation One (DIO)](https://www.dio.me/).

---

Desenvolvido com ❤️ por [TeuszMAN](https://github.com/TeuszMAN)
