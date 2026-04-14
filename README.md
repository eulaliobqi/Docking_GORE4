# 🧬 GORE4 Docking Pipeline

> **🟡 Status atual:** `Fase 1 – Preparação & Validação Estrutural`  
> 📅 Última atualização: Abril 2026

Repositório contendo o pipeline reprodutível para modelagem por homologia, validação estrutural, geração de ensemble peptídico, *docking* molecular e refinamento termodinâmico do peptídeo inibidor **LALAK (Leu-Ala-Leu-Ala-Lys)** no sítio ativo da **tripsina de *Spodoptera frugiperda***.

---

## 🎯 Objetivo
Prever a pose de ligação, afinidade termodinâmica e interações chave do peptídeo LALAK no pocket S1 da tripsina, utilizando um fluxo de trabalho validado na literatura para peptídeos curtos (4–8 resíduos). O pipeline prioriza reprodutibilidade, controle de estados de protonação e *rescoring* termodinâmico para superar limitações de funções de *scoring* clássicas.

---

## 🧪 Sistema em Estudo
| Componente | Descrição | Fonte / Método |
|------------|-----------|----------------|
| **Receptor** | Tripsina de *S. frugiperda* (~245 aa) | Modelagem por homologia (SWISS-MODEL) |
| **Ligante** | Peptídeo LALAK (Leu-Ala-Leu-Ala-Lys) | Geração *ab initio* (PEP-FOLD4) |
| **Sítio-alvo** | Pocket S1 (Asp189) + Trio Catalítico (His57, Asp102, Ser195) | PDBs de referência: `1TRN`, `3PTB`, `1TGN` |
| **pH de trabalho** | 7.8 (atividade fisiológica da tripsina) | PROPKA / PDBFixer |

---

## 📁 Estrutura do Repositório
```text
├── 01_preparo/          # Modelos limpos, com H⁺ e protonação pH 7.8
├── 02_peptideo/         # Ensemble LALAK (PEP-FOLD4) + conformações representativas
├── 03_haddock/          # Restrições CNS, config.yaml, resultados de docking
├── 04_md_mmgb/          # Topologias GROMACS, trajetórias MD, scores MM-GBSA
├── 05_validacao/        # Relatórios MolProbity/ProSA/QMEAN, PLIP, visualizações
├── scripts/             # Automação (setup, MM-GBSA, validação)
├── docs/                # Protocolos detalhados, parâmetros, notas de execução
└── README.md
