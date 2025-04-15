#etl Ibovespa
#Importando as bibliotecas

import pandas as pd
def read_files(path, name_file, year_date, type_file): #parametros da funcao
  
    _file = f'{path}{name_file}{year_date}.{type_file}'

    colspecs = [(2,10), #data do pregão lista do python somamos +1 pois inicia no 0
              (10,12), #codigo do BDI - obs.: dados layout, sempre diminuindo 1
              (12,24), #codigo de negociacao do papel - sigla acao
              (27,39), #nome resumido da empresa - nome acao
              (56,69), #preco abertura papel
              (69,82), #preco maximo
              (82,95), #preco minimo
              (108,121), #preco fechamento
              (152,170), #quantidade de titulos negociados
              (170,188) #volume de negocios   
  ]
                  
              
    names = ['data_pregao', 'codbdi', 'sigla_acao', 'nome_acao', 'preco_abertura', 'preco_maximo', 'preco_minimo', 'preco_fechamento', 'qtd_negocios', 'volume_negocios']

    df = pd.read_fwf(_file, colspecs = colspecs, names = names, skiprows = 1) #listas que já criamos, pulando o header
    return df

def filter_stocks(df):
    df = df[df['codbdi'] == 2] #filtrando apenas ações 02 LOTE PADRAO
    df = df.drop(columns=['codbdi']) #excluindo coluna codigo bdi
    return df

#ajustar data
def parse_date(df):
    df['data_pregao'] = pd.to_datetime(df['data_pregao'], format = '%Y%m%d')
    return df

#ajustes campos numericos
#todos divididos por 100 porque queremos duas casas decimais e depois convertemos em float
def parse_values(df):
    df['preco_abertura'] = (df['preco_abertura'] / 100).astype(float)
    df['preco_maximo'] = (df['preco_maximo'] / 100).astype(float)
    df['preco_minimo'] = (df['preco_minimo'] / 100).astype(float)
    df['preco_fechamento'] = (df['preco_fechamento'] / 100).astype(float)
    return df

def parse_int(df):
    df['qtd_negocios'] = df['qtd_negocios'].astype(int)
    df['volume_negocios'] = df['volume_negocios'].astype(int)
    return df

#juntando os arquivos lendo todos os csv disponiveis por ano

def concat_files(path, name_file, year_date, type_file, final_file):

  for i, y in enumerate(year_date):  #i torna indice e o y parametro
      df = read_files(path, name_file, y, type_file)
      df = filter_stocks(df)
      df = parse_date(df)
      df = parse_values(df)
      df = parse_int(df)

      if i == 0: #se o indice for 0, o primeiro sempre é
        df_final = df
      else: #das proximas vezes concatena
        df_final = pd.concat([df_final, df])
  
  df_final.to_csv(f'{path}/{final_file}', index = False) #para nao incluir campo de index
  
  #EXECUCAO DO SCRIPT

year_date = ['2018','2019','2020']
path = f'{CAMINHO}'
name_file = 'COTAHIST_A'
type_file = 'TXT'
final_file = 'all_bovespa.csv'

concat_files(path, name_file, year_date, type_file, final_file)
