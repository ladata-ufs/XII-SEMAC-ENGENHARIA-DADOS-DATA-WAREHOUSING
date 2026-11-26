# Guia: Como Transformar o Projeto do Workshop em um Portfólio no GitHub

Um erro comum ao concluir cursos e workshops é subir um único notebook bagunçado chamado `Projeto_Final_v2.ipynb` sem explicação. Recrutadores e lideranças técnicas avaliam **clareza, organização, reprodutibilidade e capacidade de explicar decisões arquiteturais** — muitas vezes passando menos de 2 minutos no seu repositório.

Este guia mostra o passo a passo para transformar o projeto desenvolvido no Dia 3 em um **repositório de portfólio profissional**.

---

## 1. Crie um Repositório Próprio e com Nome Claro

Evite nomes genéricos como `workshop-semac` ou `trabalho-dados`. Prefira nomes que comuniquem o **domínio** e a **arquitetura**:
- Bom: `cajutech-data-pipeline-dw`
- Bom: `ecommerce-medallion-lakehouse-duckdb`
- Evite: `exercicio_aula3`, `teste_etl`

---

## 2. Estruture as Pastas de Forma Profissional

Organize seu repositório para que qualquer pessoa entenda o fluxo só de olhar a raiz do projeto:

```text
cajutech-data-pipeline-dw/
├── assets/                     # Prints dos gráficos e diagrama de arquitetura
├── data/
│   └── raw/                    # Fontes pequenas de exemplo para reprodutibilidade
├── notebooks/                  # Notebooks limpos e numerados (ex: 01_ingestao.ipynb)
│   └── pipeline_completa.ipynb
├── src/                        # (Diferencial!) Scripts Python modularizados
├── docs/                       # Dicionário de dados ou notas de modelagem
├── .gitignore                  # Impede subir lixo, .venv e arquivos pesados
├── requirements.txt            # Lista exata de bibliotecas usadas
└── README.md                   # A "vitrine" do seu projeto (use o readme-template.md!)
```

> **Dica de ouro:** se você separar a pipeline em scripts na pasta `src/` (`extract.py`, `transform.py`, `load_dw.py`, `train_ml.py`) além do notebook exploratório, seu projeto já se destaca da maioria dos portfólios juniores.

---

## 3. Limpe o Código e Configure o `.gitignore`

Antes do primeiro commit, faça uma revisão rápida:
1. **Reinicie o kernel e rode tudo de cima para baixo (*Restart & Run All*)**: garanta que o notebook executa sem erros do início ao fim.
2. **Remova células de teste e comentários soltos** (ex.: `# testando`, `df.head()` repetidos sem propósito).
3. **Use caminhos relativos** (ex.: `data/raw/vendas_brutas.csv`), nunca caminhos absolutos da sua máquina (`C:\Users\Joao\Downloads\...`).
4. **Configure o `.gitignore`** para não versionar arquivos desnecessários ou sensíveis:
   ```gitignore
   .venv/
   venv/
   __pycache__/
   .ipynb_checkpoints/
   .env
   *.duckdb.wal
   ```
   *(Atenção: nunca suba senhas, chaves de API ou bancos gigantes no GitHub. Para bases pequenas didáticas como a do workshop, manter `data/raw/` ajuda quem quiser clonar e rodar o projeto.)*

---

## 4. Construa um `README.md` que Vende o Seu Trabalho

Copie o modelo em [`docs/apendice/readme-template.md`](readme-template.md) para a raiz do seu repositório como `README.md` e personalize:

- **Comece pelo problema de negócio, não pela ferramenta:** explique *por que* o projeto existe antes de listar Pandas e DuckDB.
- **Mostre visualmente:** inclua o diagrama de arquitetura (Mermaid ou imagem) e **1 ou 2 gráficos gerados na Etapa 4** salvos em `assets/`. Repositórios visuais retêm muito mais atenção.
- **Documente números reais:** cite quantas duplicatas foram removidas, quanto o Parquet economizou em relação ao CSV e qual foi a acurácia do modelo de ML.
- **Explique os trade-offs:** escreva 3 ou 4 linhas justificando *por que* usou Medallion, Parquet, Star Schema e Feature Store.

---

## 5. Publique no GitHub com Boas Práticas de Git

No terminal, dentro da pasta do seu projeto:

```bash
# Inicializar o repositório
git init
git branch -M main

# Adicionar arquivos e criar commits claros e objetivos
git add .gitignore requirements.txt data/raw/
git commit -m "chore: adiciona estrutura inicial e fontes de dados brutas"

git add notebooks/
git commit -m "feat: implementa pipeline Bronze, Silver, Star Schema (DuckDB) e Feature Store"

git add README.md assets/
git commit -m "docs: adiciona arquitetura, resultados e guia de execução no README"

# Conectar ao repositório criado no GitHub e enviar
git remote add origin https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
git push -u origin main
```

### Capriche na página do repositório no GitHub:
- Preencha a seção **About** (canto superior direito) com uma frase curta de impacto.
- Adicione **Topics** (tags) relevantes: `data-engineering`, `data-warehouse`, `duckdb`, `parquet`, `etl`, `star-schema`, `feature-store`, `python`.
- Fixe (*Pin*) o repositório no topo do seu perfil do GitHub.

---

## 6. Como Apresentar o Projeto no LinkedIn e no Currículo

Não diga apenas *"Fiz um projeto de engenharia de dados no workshop"*. Use a estrutura **Contexto → Ação Técnica → Resultado**:

> **Exemplo para Currículo:**
> *Desenvolvi uma pipeline ponta a ponta em Python, DuckDB e Parquet integrando 4 fontes heterogêneas (SQLite, CSV, JSON e logs textuais) em arquitetura Medallion (Bronze/Silver/Gold), modelando um Data Warehouse em Star Schema para KPIs analíticos e uma Feature Store offline consumida por modelo de classificação em Scikit-Learn.*

> **Exemplo de Post no LinkedIn:**
> - **Gancho:** "Como transformar dados espalhados em SQLite, CSV, JSON e logs em um Data Warehouse + Feature Store para ML?"
> - **Corpo:** 3 tópicos curtos sobre os desafios de heterogeneidade que você resolveu + imagem do diagrama de arquitetura ou de um gráfico gerado.
> - **Chamada final:** link direto para o repositório no GitHub convidando para feedback.

---

## Checklist Final Antes de Compartilhar

- [ ] O repositório tem nome profissional, descrição (*About*) e *Topics* preenchidos.
- [ ] O `README.md` contém problema de negócio, diagrama de arquitetura, resultados e instruções de execução.
- [ ] O notebook/código roda de ponta a ponta usando apenas caminhos relativos e `requirements.txt`.
- [ ] Não há arquivos temporários (`.venv`, `.ipynb_checkpoints`, senhas) versionados.
- [ ] Você consegue explicar em 2 minutos, em uma entrevista, cada decisão tomada nas 4 etapas.
