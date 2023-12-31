# entregas_chpython

----- SEÇÃO CRIAÇÃO DO ALERTA -----

É criada uma função ('extracao') para realizar uma requisição e um alerta por meio do notification.notify. A requisição é feita pela função requests e é atribuída uma variável ao código do status da requisição. O alerta exibe uma mensagem informando se a requisição foi realizada com sucesso ou não. Em caso negativo, retorna qual o tipo de erro (erro na requisição ou outros tipos).

----- SEÇÃO EXTRAÇÃO DAS BASES -----

As seguintes bases são extraídas pela função 'extracao' criada anteriormente:

base_municipios: 
https://brasilapi.com.br/api/ibge/municipios/v1/sp?providers=dados-abertos-br,gov,wikipedia

base_uf:
https://brasilapi.com.br/api/ibge/uf/v1

base_estado_sp:
https://brasilapi.com.br/api/ibge/uf/v1/sp

base_pix:
https://brasilapi.com.br/api/pix/v1/participants

----- SEÇÃO TRATAMENTO DAS BASES -----

São feitos os seguintes ajustes às bases:

- base_uf: o dicionário da coluna 'regiao' é desmembrado em duas colunas (sigla da região e nome da região)

- base_estado_sp: a base traz 3 informações sobre a região (id, nome e sigla). A coluna região foi resumida para mostrar apenas o nome da região.

- base_pix: a data mostrada na coluna 'inicio_operacao' é formatada para mostrar apenas a data, em vez de data e horário, no formato DD/MM/YYYY

----- SEÇÃO SALVAR EM BANCO DE DADOS -----
 É utilizada uma função para salvar as bases tratadas em formato .db, criando e fechando uma conexão pelo sqlite.
 Uma segunda função é utilizada para mostrar as tabelas salvas no banco de dados.

----- PRODUTOS FINAIS -----

Arquivos:
banco_projeto.db    contendo:
                    base_uf
                    base_estado_sp
	                base_municipios
	                base_pix
requirements.txt    mostra as versões dos pacotes utilizados, extraídos do 'meu_ambiente_virtual'