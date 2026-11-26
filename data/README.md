# Dados do Workshop (`data/`)

Todos os arquivos de entrada e saída utilizados nos notebooks do **Dia 2** ficam centralizados nesta pasta, separados por módulo:

- **`modulo_01/`**:
  - `aula/`: pasta criada automaticamente durante a execução de `modulo_01_ingestion.ipynb` para arquivos gerados em demonstração.
  - `exercicios/`: `log_sistema.txt`, `produtos.csv` e `loja_oltp.db`.
- **`modulo_02/`**:
  - `comparativo/`: `vendas_armazenamento.csv` e `vendas_armazenamento.parquet` (comparação de formato e tamanho).
  - `datalake/`: arquitetura Medallion simulada (`bronze/`, `silver/`, `gold/`).
  - `exercicios/`: `clientes_cadastro.csv` e `pedidos_bronze.csv` (além da subpasta `datalake/` gerada ao resolver os exercícios).
- **`modulo_03/`**:
  - `vendas_brutas.csv`, `vendas_etl.csv`, `vendas_tratadas.parquet` e `data_warehouse.duckdb` (usado nos Módulos 3 e 4).
  - `exercicios/`: `vendas_brutas_ex.csv` (e `vendas_limpas_ex.parquet` gerado nos exercícios).
- **`modulo_04/`**:
  - `feature_store/`: `fs_comportamento_cliente.parquet` e `fs_comportamento_cliente.csv` (Feature Store offline exportada para ML).
