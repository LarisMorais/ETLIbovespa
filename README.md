
# 📈 ETL de Séries Históricas da B3 (Ibovespa)

Este projeto em Python realiza um processo ETL (Extração, Transformação e Carga) de dados históricos da B3, utilizando arquivos TXT disponibilizados pela bolsa. O objetivo é consolidar informações relevantes sobre ações negociadas no mercado à vista em um único arquivo CSV para análises posteriores.

## 🔍 Sobre o Projeto

O script executa as seguintes etapas:

1. **Extração**: Leitura de arquivos TXT anuais contendo dados históricos de negociações da B3.
2. **Transformação**:
   - Despreza o cabeçalho e lê os registros de cotação.
   - Filtra os dados para incluir apenas ações do tipo "02 - Lote Padrão".
   - Ajusta os campos numéricos, datas e inteiros conforme o layout fornecido pela B3.
3. **Carga**: Consolida os dados de todos os anos informados em um único arquivo CSV (`all_bovespa.csv`).

## 🛠️ Tecnologias Utilizadas

- Python 3
- Bibliotecas:
  - `pandas`

## 📁 Estrutura do Projeto

- `main.py`: Script principal que executa o processo ETL.
- `COTAHIST_A2018.ZIP`: Exemplo de arquivo TXT anual da B3.
- `all_bovespa.csv`: Arquivo CSV gerado com os dados consolidados.

## 🔗 Recursos Adicionais

- [Download dos arquivos TXT da B3](https://www.b3.com.br/pt_br/market-data-e-indices/servicos-de-dados/market-data/historico/mercado-a-vista/series-historicas/)
- [Layout dos arquivos TXT](https://www.b3.com.br/data/files/33/67/B9/50/D84057102C784E47AC094EA8/SeriesHistoricas_Layout.pdf)

## 🚀 Como Executar

### Pré-requisitos

- Python 3 instalado na máquina.
- Bibliotecas necessárias instaladas (`pandas`).

### Passos

1. Clone o repositório:

   ```bash
   git clone https://github.com/LarisMorais/ETL-Ibovespa.git
   cd ETL-Ibovespa
   ```

2. Instale as dependências:

   ```bash
   pip install pandas
   ```

3. Adicione os arquivos TXT anuais da B3 ao diretório do projeto.

4. Execute o script:

   ```bash
   python main.py
   ```

   O script processará os arquivos e gerará o arquivo `all_bovespa.csv` com os dados consolidados.

## 📬 Contato

Se desejar entrar em contato, você pode me encontrar em:


- [LinkedIn](https://www.linkedin.com/in/larissamorais26/)
- [GitHub](https://github.com/LarisMorais)
- Email: larismorais26@gmail.com
