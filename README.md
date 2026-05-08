# Projeto: Modelagem de Incerteza com Redes Bayesianas

Este projeto apresenta a implementação e análise de uma **Rede Bayesiana** baseada no problema clássico de justiça e probabilidade criminal do livro *Artificial Intelligence: A Modern Approach (Russell & Norvig)*. O sistema foi desenvolvido em **ProbLog**, uma linguagem de programação lógica probabilística.

## Descrição do Cenário

A rede modela as interdependências entre as seguintes variáveis:

- **B (Broke Law):** O indivíduo quebrou a lei.
- **M (Politically Motivated):** O promotor possui motivações políticas.
- **I (Indicted):** O indivíduo foi indiciado (depende de B e M).
- **G (Guilty):** O veredito de culpabilidade (depende de B, I e M).
- **J (Jail):** O desfecho de prisão (depende de G e, na versão expandida, de P).
- **P (Presidential Pardon):** A concessão de um indulto presidencial (fator inibidor de J).

---

## Implementação Técnica (ProbLog)

O código mapeia as **Tabelas de Probabilidade Condicional (CPT)** em regras lógicas. Um diferencial deste modelo é o tratamento de **Independência Específica ao Contexto (CSI)**:

- **Lógica de Inocência:** Se o indivíduo não quebrou a lei ($\neg b$), a probabilidade de ser culpado ($g$) torna-se independente da motivação política ($m$) ou indiciamento ($i$), sendo fixada em **0.0** em contextos de integridade fática.
 
- **Expansão da Rede:** Foi adicionado o nó **P (Indulto)**, que atua como uma porta lógica de controle sobre o nó **J**, reduzindo drasticamente a chance de prisão mesmo em casos de condenação.

---

### 📊 Análise de Resultados

Os cálculos realizados pelo motor de inferência demonstram a aplicação da **Regra de Bayes** para probabilidades condicionais:

| Cenário | Descrição | Probabilidade |
| --- | --- | --- |
| **P(j / b, i, m)** | Chance de prisão dado que quebrou a lei, foi indiciado e o promotor é motivado. | **~81%** |
| **Cenário B** | Probabilidade de ir preso sendo inocente ($\neg g$). | **0%**  |
| **Perdão (P)** | Probabilidade de ser culpado mas ser "salvo" pelo indulto. | **~1%** |

---

### 📂 Como Executar

1. Acesse o [ProbLog Editor Online](https://dtai.cs.kuleuven.be/problog/editor.html).
2. Cole o código presente neste repositório.
3. Clique em **Evaluate** para observar as inferências marginais e conjuntas.

---

**Curso:** Inteligência Artificial - IComp/UFAM **Professor:** Edjard Mota 
**Acadêmico:** Kevyn do Nascimento Paz Gondim
