# 🧠 Engenharia de Soluções Lógicas
 
## 📝 Descrição do Projeto
Este projeto consiste no desenvolvimento de soluções algorítmicas voltadas à resolução de problemas complexos do mundo real, utilizando conceitos de abstração e modelagem lógica.

A abordagem parte da análise do problema até a construção de uma solução estruturada, garantindo clareza, organização e eficiência na resolução.
 
*Figura 1: Representação da lógica aplicada na solução de problemas.*
![Diagrama](Diagrama.pdf)
 
## 🚀 Tecnologias Utilizadas
* **Linguagem:** Python  
* **Conceitos Aplicados:** Decomposição de problemas, raciocínio lógico estruturado, abstração e modelagem  
* **Ferramentas:** VS Code / Terminal
 
## 📊 Funcionalidades
* Estruturação de problemas complexos  
* Divisão em partes menores (decomposição)  
* Aplicação de lógica sequencial e condicional  
* Modelagem de soluções algorítmicas  


## 💻 Resposta do Projeto 
<details> <summary>📂 Clique para ver as respotas</summary>

inicio



  enquanto (verdadeiro) faca



    // Entrada de dados (sensores)

    leia fluxo_veiculos

    leia tempo_espera



    escreva("Coletando dados dos sensores...")



    // DECISÃO 1: Trânsito livre?

    se (fluxo_veiculos < 30) entao



      escreva("Caminho livre")



    senao



      // NÃO vai para o fim → continua



      // DECISÃO 2: Trânsito intenso?

      se (fluxo_veiculos >= 30) entao



        escreva("Tráfego intenso detectado")

        escreva("Escolhendo nova rota")



        // DECISÃO 3: Tempo maior que 100?

        se (tempo_espera > 100) entao



          escreva("Recalculando rota")



          // DECISÃO 4: Rota alterada?

          // (simulação de confirmação)

          rota_alterada <- verdadeiro



          se (rota_alterada == verdadeiro) entao

            escreva("Nova rota definida")

          senao

            escreva("Buscando alternativa")

          fimse



        senao



          escreva("Tempo aceitável, mantendo rota atual")



        fimse



      senao



        // Caso não seja intenso nem livre (intermediário)

        escreva("Tráfego moderado")



        // Ainda continua lógica

        se (tempo_espera > 100) entao

          escreva("Recalculando rota")

        senao

          escreva("Mantendo fluxo normal")

        fimse



      fimse



    fimse



    escreva("Atualizando sistema...\n")



  fimenquanto



fim



Cenário A (Ideal)
Entrada:

fluxo_veiculos = 80

tempo_espera = 60

emergencia = falso

Execução:

fluxo_veiculos > 50?

Sim (80 > 50)

Sistema entra no bloco de tráfego intenso

“Tráfego intenso detectado”

“Aumentando tempo do sinal verde”

tempo_espera > 100?

Não (60 < 100)

Resultado:

“Mantendo ajuste atual”

Conclusão:

O sistema ajusta o semáforo normalmente, apresentando o comportamento esperado.

Cenário B (Limite/Borda)
Entrada:

fluxo_veiculos = 50

tempo_espera = 100

emergencia = falso

Execução:

fluxo_veiculos > 50?

Não (50 não é maior que 50)

Vai para o próximo bloco (não finaliza)

emergencia == verdadeiro?

Não

tempo_espera > 100?

Não (100 não é maior que 100)

Resultado:

“Mantendo ciclo padrão dos semáforos”

Conclusão:

Valores no limite não ativam as ações.

Se necessário, pode-se utilizar >= em vez de > para incluir esses casos.

Cenário C (Erro/Exceção)
Entrada:

fluxo_veiculos = -10

tempo_espera = "abc"

emergencia = "talvez"

Execução:

fluxo_veiculos > 50?

Pode gerar comportamento incorreto

tempo_espera > 100?

Erro (não é possível comparar texto com número)

emergencia == verdadeiro?

Valor inválido

Conclusão:

O sistema pode falhar ou tomar decisões incorretas devido à ausência de validação dos dados de entrada.





1. Qual foi o maior desafio logístico?
O maior desafio foi simplificar um problema real, com muitas variáveis, em decisões binárias (se/senão) sem perder a lógica do sistema.



2. Qual modificação tornaria o algoritmo mais resiliente?
Adicionar validações de entrada para garantir que os dados sejam válidos (números corretos e valores coerentes), evitando erros e decisões incorretas.
