# 🏢 Auditoria de Orçamentos Corporativos (Python)
 
[![Python Version](https://img.shields.io/badge/python-3.x-blue.svg)](https://www.python.org/)
[![Status](https://img.shields.io/badge/status-concluído-brightgreen.svg)]()
  
## 📖 Sobre o Projeto
Este projeto foi desenvolvido como parte da disciplina de Programação de Computadores do curso de Engenharia de Software. O objetivo do script é processar e calcular o orçamento de uma estrutura organizacional complexa (dicionários aninhados) de uma multinacional, aplicando regras de negócio dinâmicas e auditoria de execução.
 
A solução foi arquitetada utilizando conceitos avançados de Python para garantir flexibilidade, performance e rastreabilidade.
 
## 🚀 Funcionalidades
- **Cálculo Hierárquico:** Varredura completa da estrutura corporativa, independentemente do nível de profundidade.
- **Filtros Dinâmicos:** Capacidade de ignorar setores específicos e todos os seus subsetores na hora do cálculo financeiro.
- **Conversão de Câmbio:** Suporte a parâmetros opcionais para conversão de moedas em tempo de execução.
- **Sistema de Auditoria:** Monitoramento automatizado de tempo de execução e registro (logging) dos parâmetros utilizados na transação financeira.
 
## 🛠️ Tecnologias e Conceitos Aplicados
Este projeto foi construído utilizando Python puro (Standard Library), com foco nos seguintes paradigmas e recursos:
* **Funções Recursivas (Recursion):** Utilizadas para a navegação na árvore de dados (dicionários aninhados).
* **Decorators:** Implementação do `@auditor` para injetar comportamentos de log e cronometragem sem modificar a lógica de negócios.
* **Empacotamento de Argumentos (`*args` e `**kwargs`):** Utilizados tanto no decorator quanto na função principal para permitir a passagem dinâmica de departamentos a serem ignorados e taxas de câmbio.
 
## ⚙️ Como Executar
 
### Pré-requisitos
* Python 3.8 ou superior instalado.
 
### Passo a Passo
1. Clone este repositório:
   ```bash
   git clone [https://github.com/SeuUsuario/seu-repositorio.git](https://github.com/SeuUsuario/seu-repositorio.git)
   ```
2. Acesse a pasta do projeto:
   ```bash
   cd seu-repositorio
   ```
3. Execute o script principal:
   ```bash
   python main.py
   ```
 
## 🧠 Lógica e Estrutura do Código
Breve explicação de como o código foi organizado:
* `[Explique aqui em 1 ou 2 parágrafos como você pensou para construir a sua recursão e como o decorator foi acoplado no projeto]`.
* **Dados:** Os dados simulados da empresa foram estruturados em... `[explique a estrutura do seu dicionário]`.
 
## 👤 Autor
 
* **Vinicius Pina Ferreira** * LinkedIn: https://www.linkedin.com/in/vin%C3%ADcius-pina-ferreira-a58b46380/
* E-mail: vinicius.pina64@gmail.com
 
---

## 💻 Código do Projeto

<details>
<summary>📂 Clique para ver todo o código</summary>

import time

empresa = {
    "Matriz": {
        "TI": {
            "Infraestrutura": 120000,
            "Desenvolvimento": 95000,
        },
        "RH": {
            "Recrutamento": 60000,
            "Treinamento": 35000,
        },
        "Marketing": {
            "Digital": 55000,
            "Eventos": 40000,
        },
    },
    "Filial SP": {
        "Vendas": 75000,
        "Logística": 90000,
    },
}

def auditor(funcao):
    def wrapper(*args, **kwargs):
        print("=" * 50)
        print("  AUDITORIA — INÍCIO DO CÁLCULO")
        print("=" * 50)
        print(f"  Departamentos ignorados : {args[1:]}")
        print(f"  Parâmetros de câmbio    : {kwargs}")
        inicio = time.perf_counter()
        resultado = funcao(*args, **kwargs)
        fim = time.perf_counter()
        print(f"  Tempo de execução       : {fim - inicio:.6f}s")
        print("=" * 50)
        return resultado
    return wrapper

@auditor
def calcular_orcamento(estrutura, *args, **kwargs):
    taxa = kwargs.get("taxa_cambio", 1.0)
    moeda = kwargs.get("moeda_destino", "USD")

    def somar(no):
        if isinstance(no, (int, float)):
            return no
        total = 0
        for nome, conteudo in no.items():
            if nome in args:
                print(f"  >> Ignorando: {nome}")
                continue
            total += somar(conteudo)
        return total

    total_usd = somar(estrutura)
    total_convertido = total_usd * taxa
    print(f"\n  Total (USD)  : US$ {total_usd:,.2f}")
    print(f"  Total ({moeda}) : {total_convertido:,.2f}\n")
    return total_convertido

calcular_orcamento(empresa)

calcular_orcamento(
    empresa,
    "TI", "Marketing",
    moeda_destino="BRL",
    taxa_cambio=5.20
)
