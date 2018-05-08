# API de integração

## Visão Geral

Este documento tem por objetivo fornecer uma documentação detalhada da funcionalidade de integração da plataforma de
gestão do Milk's Rota, para comunicação com outros serviços e sistemas externos.

A comunicação com a __API__ se dá através de requisições __POST__ do protocolo __HTTP__. Esses métodos precisam ser chamados
passando os devidos parâmetros e a API irá retornar os resultados no formado __JSON__

## Introdução 

  O Milk's Rota é uma plataforma exclusiva e dedicada, criada para aumentar a produtividade
	e reduzir custos no processo de coleta e captação de leite de laticínios e cooperativas. 
	Utilizando as tecnologias web e mobile mais modernas, ela automatiza o processo de coleta 
	de ponta-a-ponta, simplificando a operação para carreteiros, técnicos e administração. 
	São fornecidas informações valiosas que facilitam a gestão, tomada de decisões estratégicas e operacionais.
	
  Para viabilizar a troca de informações entres os mais variados sistemas de gestão do mercado, 
	foi criada uma A.P.I. de integração que disponibiliza métodos de acesso á base de dados de nosso servidor, 
	de forma segura e controlada, por meio dos quais a equipe técnica das empresas pode acessar e registrar as 
	informações no ambiente.


## Autenticação

Toda chamada aos métodos da API exige que sejam enviados como parâmetro, além dos parâmetros específicos do método, os
seguintes parâmetros:

| Parâmetro | Descrição |
|-----------|-----------|
| conta_id  | Identificador único da conta |
| token     | Token da API gerado para a conta |

Para obter essas informações, entre em contato com a equipe de suporte através do email [suporte@milksrota.com.br](mailto:suporte@milksrota.com.br)

## Exemplo

#### Requisição

```http
POST /api/retaguardasync/writeTag HTTP/1.1
Host: app.sclrota.com.br
Content-Type: application/json
Accept: application/json

{
    "conta_id":40001,
    "data":[
        {
            "codigo":"00306",
            "tipo":"C",
            "tagid":"323CDE91",
            "veiculo":"",
            "tanque":"",
            "coletor":"00016",
            "tecnico":""
        }
    ]
}
```

#### Resposta

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: xxxx

{"success":true,"message":"OK","data":[],"monitor.time":7.0328681469}
```

##  FORMAS DE INTEGRAÇÃO 


### Modelos de Integração

  Estão disponíveis dois modelos de integração entre a plataforma Milk's Rota e os sistemas ERP das empresas contratantes.
  
-------
(1) - Troca de Informações por arquivos
-------  
  Previmos a utilização de arquivos tipados no formato texto simples, por meio dos quais as informações podem ser enviadas e recebidas
  da plataforma. Estes arquivos tem como requisitos básicos a utilização de um caracter separador padrão ("|","-", "/",etc.) entre os atributos e a necessidade de que a "**primeira linha do arquivo contenha o nome do atributo como coluna da tabela**".
  
  Neste modelo, utilizaremos um utilitário integrador que opera no módo "Stand-alone" para fazer o mapeamento das informações, inserir em tabelas temporárias e enviá-las ao servidor Milk's Rota.
  
  obs: Escolha um caracter separador que NÃO faça parte da construção dos nomes das colunas
  
  Ex: Uma forma válida de enviar as informações de cadastro das linhas de coleta para o integrador pode ser criada desta forma
  
| codigo/|nome/|distancia_Km/|codigo_rota/
|-------|----|-------------|:-----------:|
| 001/|Linha Norte/|100,00/|0001/  	     |
| 002/|Linha Sul/|132,00/  |0001/		 |
| 003/|Linha Rural/|245,00/|0001/		 |

  
Importante: Os nomes das colunas que identificam os atributos não podem contem espaços em branco, desta forma uma rejeição seria criada se o nome de uma das colunas fosse descrito assim: (**codido da linha**). 

São permitidos nomes do tipo (codigo-da-linha ou codigo_da_linha), onde não ha inserção de espaços entre as palavras. Acentuação gráfica também deve ser evitada. 

### Cadastros básicos para operação

  O coletor Milk's Rota é uma App Mobile que opera nos modos **on line** e **off-line**, com seleção automática, dependendo da disponibilidade de conexão ás redes móveis ou Wi-Fi.
  
  Ao iniciar ou finalizar uma viagem, o equipamento coletor deve estar conectado a uma rede de transferência de dados para receber um pacote de carga com as informações dos produtores, pontos de coleta, dados dos veículos transportadores, forma de descarga, etc., e também para fazer a sincronização dos dados coletados com o servidor Web ao final do percurso nas linhas.
  
  Se não houver sinal de dados ao iniciar uma viagem, o coletor não fará o processo de auto-atualização da base de dados, e os registros poderão ser feitos com base na última carga recebida. Será imprescindível que ao finalizar uma linha de coleta, o sistema detecte uma conexão de dados disponível, caso contrário, o servidor web não será atualizado e o conjunto coletor (Celular + impressora) ficará indisponível para abertura de novas viagens, até se faça a conexão e a descarga das informações para o servidor. 
  
  ----
### Carga na base de dados
  ---
  
  Este é o conjunto de informações que devem ser extraídas do sistema ERP da empresa contratante e enviados á plataforma Milk's Rota para alimentar os dispositivos coletores móveis:
  
  
  **Grupos de Rotas**:  Definimos com grupos de rotas, um container que represente o primeiro nível hierárquico de rotas de coleta dentro da organização ou empresa que utiliza a plataforma Milk's Rota.
>
  Ex.: 0001 -  GR_02976205000132 
>
Grupo de rotas da empresa "LATICÍNIOS EXEMPLO"  

  **Rotas**: As rotas de coleta são representações de uma região, identificação de uma filial ou posto de coleta da empresa, e que por sua vez, estão ligadas a um determinado Grupo de Rotas. As rotas de coleta agregam um conjunto de linhas de coleta, que são finalmente os destinos dos veículos coletores.
  
> Ex.: 
>  Grupo_Rota/Rota/Descricao
  
>  0001/R001/Regiao Sul/  
>  0001/R002/Regiao Norte/  
>  0001/R003/Posto Coleta III/
>

  **Linhas de Coleta**: Entendemos como linhas de coleta o conjunto de propriedades a serem visitas por um mesmo veículo transportador, dentro de uma ordem e horários pré-definidos.
  
  Um determinado veículo pode se deslocar por mais de uma linha de coleta desde que esta faça parte da mesma Rota de Coleta que foi definida no momento da abertura da viagem, caso contrário, estaria configurado ai um "desvio de rota", que é permitido de acordo com a política da empresa contratante.
  
> Ex.:
> Codigo/Nome_da_Linha/Codigo_da_Rota

>  0001/Linha Bananal/R001/   
>  0002/Linha Fundão/R001/  
>  0003/Linha Areais/R002/  
>  0004/Linha Cristais/R003/  


  **Veículos e Reboques**: Esta tabela deve expor as informações básicas sobre os veículos de transporte utilizados para realizar as coleta nas linhas, sendo que os atritubtos obrigatórios são apenas o código de identificação do veículo e sua placa. Caso a empresa utilize conjuntos de veículo + reboque, conhecidos como "Romeu e Julieta", o registro deve ser feito para cada parte do conjunto, ou seja, os reboques (Julietas) também precisam ser cadastrados, bem como seus tanques de transporte.
  
> Ex.:   
> Codigo_Veiculo/Placa/Tipo  

>  V001/XYZ-9999/V/  
>  V002/JUL-8989/R/  
>  V003/HRR-0001/V/    
>  V004/TTT-0002/V/  

* V - Veículos Simples
* R - Reboque  

  **Motoristas/Coletores**: Este conjunto de dados deve trazer as informações sobre os motorista e ou pessoas que atuam nas rotas para realizarem os registros de coletas e que irão operar a aplicação mobile.
  
>Ex.: 
>Codigo/Nome/  

>C001/Jose Antonio/   
>C002/Marcos Vinicius/   
>C003/Elias Transportes/   
>C004/Transportes XYZ  

**Tecnicos Plataforma/Seguidores de Rota**: Este arquivo deve conter as informações sobre os operadores de plataforma que atuam no momento da descarga dos veículos e também dos seguidores de rota. os Seguidores de rotá são pessoas responsáveis por controlar administrativamente o funcionamento do processo de coleta e que serão notificados por meio de SMS ou E-Mail quando uma ocorrência relevante for registrada pelos motoristas/coletores durante o percurso nas linhas.
  
>Ex.: 
>Codigo/Nome/celular/email/  

>L001/Jose Antonio/31 99999-4949/jose.antonio@Milk's Rota.com.br/       
>L002/Marcos Vinicius/32 99999-8888/marcos.vinicius@Milk's Rota.com.br/       


**Motivos de Cancelamento**: Conjunto de justificativas aceitáveis quando uma coleta programada não for realizada. Estes motivos serão utilizados tanto para as coletas simples, quando para as coletas especiais que geralmente são enviadas para análise de qualidade do produto em laboratórios externos à empresa.
  
>Ex.: 
>Codigo/Descricao/aplicacao  

>001/Lama na Estrada/C/   
>002/Porteira Trancada/C/   
>003/Capacidade veículo atingida/C/   
>004/problemas mecanicos no veículo/C/   
>005/Falta de energia ou Tanque Desligado/A/  
>006/Abrigo Tanque sem acesso/C/     
>007/Temperatura produto acima do permitido/A   
  
**Produtores**: Dados cadastrais do produtores/fornecedores que mantem relação comercial com a empresa.
  
>Ex.: 
>Codigo_Produtor/Nome/Fone_Conta/Celular/Email/doc/ie/tipo  

>P001/Jose Antonio/31 3332-1010/31 99999-4949/jose.antonio@Milk's Rota.com.br/59613654600//F       
>P002/Marcos Vinicius/32 3411-2210/32 99999-8888/marcos.vinicius@Milk's Rota.com.br/23467892344//F      
 
**obs: O código de identificação do produtor precisar ser reconhecível pelo sistema ERP da empresa contratante,pois os registros das coletas vem marcados com este código no arquivo de integração de retorno.**

|Tipo|Descricao|
|:------------:|--------|
|F|Pessoa Fíisica|
|J|Pessoa Jurídica|
  

**Fazendas**: Informações básicas das fazendas produtoras.
  
>Ex.: 
>Codigo_Fazenda/Nome/Codigo_Produtor/  

>F001/Fazenda Raio de Sol/001/       
>F002/Fazenda Miramar/002/  
>F003/Sitio Araras/001/  

**Tanques**: São os registros dos pontos de coleta que precisam ser visitados dentro de uma linha. Consideramos várias situações onde a fazenda produtora possua um ou mais tanques. Devem ser registrados também neste conjunto de dados, as informações dos tanques de transporte dos veículos e reboques, bem como os silos e baloes de armazenamento que são destino do produto no momento da descarga. 
  
  Aconselhameos que o primeiro atributo da linha de dados seja o "Tipo_de_Tanque", que poderá ser carregado com as seguintes informações:

|Tipo de Tanque|Descricao|
|:------------:|--------|
|V|Tanque de Veículo|
|F|Ponto de Coleta na Fazenda|
|P|Silo ou Balão de Plataforma|


 
>Ex.: 
>Tipo_de_Tanque/codigo_tanque/codigo_da_fazenda/codigo_do_veiculo/capacidade/altura/perimetro/volume/
comunitario/distribuicao/diferenca/impressao/divisao/  

>F/T001/F002/ /1000/ / /1000/**1**/DP/P/S/M/       
>V/T002/  /V001-01/3500/ / /3500/0/DP/P/S/M/  
>V/T003/  /V001-02/4000/ / /4500/0/DP/P/S/M/  
>V/T004/  /V001-02/3500/ / /3500/0/DP/P/S/M/  
>V/T002/  /V001-01/3500/ / /3500/0/DP/P/S/M/  
>P/BALAO 01/ / /50000/ / /50000/0/DP/P/S/M/  
>P/SILO 01 / / /80000/ / /80000/0/DP/P/S/M/  
>P/SILO 02 / / /100000/ / /100000/0/DP/P/S/M/  
 
  Obs.: os tanque do tipo "V" Veículo devem ser informados para cada compartimento do tanque do veículo, se o veículo transportador tiver um tanque com 3 compartimentos, cada um compartimento deve ter um registro com sua capacidade de transporte. O mesmo ocorre para o caso dos reboques, se o veículo for do tipo "R" reboque, ele terá registrados os tanques do veículo simples e também os tanques do reboque que compoe o conjunto de transporte "Romeu e Julieta".    

  **TABELA DE DOMÍNIOS PARA OS ATRIBUTOS DOS TANQUES**

|Atributo|Domínio|
|--------|-------|
|Comunitario| 0 - Tanque individual  /  1 - Tanque Comunitário ou Coletivo|
|Distribuicao| DP - Distribuicao pela Plataforma WEB  / DC - Distribuicao pelo motorista ou coletor|
|Diferenca| P - Diferenças de anotação vão para o proprietário  / D - Distribuição proporcional da diferença por participação|
|Impressao| D - Detalhada - Imprime ticket de coleta para cada participante / S - Simplificada, apenas um ticket geral | 
|Divisao| M - Manual, Coletor digita os valores  / A - Automática, Sistema calcula participação por percentual |

  Esta tabela de domínios se aplica ao caso de tanques do tipo "F" (Pontos de coleta na fazenda), onde existe a participação de mais de um produtor utilizando o mesmo tanque resfriador no regime comunitário ou coletivo.

 **Tanques Coletivos**: Relação de produtores participantes dos tanques comunitários ou coletivos. Os registros desta tabela levam em conta o código do tanque que necessariamente precisar estar registrado na tabela de tanques com o atributo "**comunitario=1**".
  
>Ex.: 
>Codigo_Registro/Codigo_do_Tanque/Codigo_do_Produtor/percentual/responsavel/  

>0001/T001/P002/00/**1**/   
>0002/T001/P005/00/0/  
>0003/T001/P006/00/0/    
  
Nota: Cada tanque coletivo deve conter apenas uma linha com o atributo "**responsável**" marcada com o conteúdo "1";   
São aceitos "N" registros de participantes para os tanques e o vincúlo acontece pelo código do produtor;  
Caso seja informado o percentual de participação do produtor no tanque para cálculo de distribuição de volumes, O atributo **divisao** do tanque deve ter o conteúdo "**A**" (Automática) e o atributo distribuição deve ter o conteúdo "**DC**" (distribuição pelo coletor), na tabela de registro do tanque.

  **Tags NFC**: A paltaforma Milk's Rota faz a identificação de vários atores do processo através da tecnologia NFC (Near Field Comunication). São identificados os motoristas/coletores, veículos, pontos de coleta, reboques e técnicos de plataforma.
  
  As etiquetas NFC tem um identificador único que precisa ser vinculado ao ator que será identificado. Como não existe gravação ou regravação direta, usaremos o modelo de tabela abaixo para gerar as associações.  
  Reutilização dos identificadores NFC são permitidos naturalmente, basta que o ID da tag NFC seja desvinculado de um ator e vinculado a outro.
  
>Ex.:
>Codigo_Registro/Codigo_Coletor/codigo_tanque/codigo_veiculo/codigo_tecnico/tagid/tipo/  

>0001/C001/ / / /A7890288/C/   
>0002/  /T001/ / /17090188/T/   
>0003/ / /V001/ /234ER288/V/   
>0004/ / /V002//AS1223E1/R/    
>0005/ / //L001/XS1453E1/L/      

**Tabela de valores para o atributo "tipo"**

|Valor|Descrição|
|:---:|---------|
|V|Tag de Veículo|
|T|Tag de Tanque (Ponto de coleta) |
|C|Tag de Coletor |
|R|Tag de Reboque|
|A|Tag de amostra|  
|L|Tag de Tecnico plataforma e laboratório|


  **Itinerários**: As Informações constantes deste arquivo definem a lista de propriedades produtoras a serem visitadas em uma viagem, bem como a ordem e horário programados de coletas. Devem ser informados os registros para todas as rotas e linhas que os coletores percorrem durante uma viagem.

>Ex.:
>Codigo/Rota/Linha/fazenda/produtor/ordem/horario/    

>0001/R001/001/F0005/P0001/1/07:00    
>0002/R001/001/F0002/P0003/2/07:40    
>0003/R001/001/F0003/P0007/3/08:10    
>0004/R001/001/F0001/P0022/4/09:00    



--------
 (2) - Consumo dos métodos do WebService  
--------

  A plataforma Milk's Rota disponibiliza, por meio de um serviço Web, vários métodos de leitura e gravação na base de dados. A forma de comunicação entre as partes e feita por meio de trocas de mensagens no formato JSON (JavaScript Object Notation) em operações POST.
  
  A seguir listaremos a URI Base de comunicação e as assinaturas dos métodos de leitura e gravação.


  **Endereço Base do Servidor**  

*  **http://app.sclrota.com.br/api/retaguardasync (AMBIENTE DE PRODUÇÃO)**

*  **http://teste.sclrota.com.br/api/retaguardasync (AMBIENTE DE HOMOLOGAÇÃO E TESTES)**

  As credenciais de acesso são fornecidas na instalação da plataforma. Nas operações com o servidor será necessário incluir no arquivo JSON a chave de identificação da conta além dos parâmetros requeridos para cada método.
  
  
  
### Métodos Inclusão/Alteração disponíveis
  

|Assinatura|parametros|função|
|----------|---------|------|
|[writeGrupoRota](anexos/#tbgruporotas)|conta_id|CRUD tabela de Grupo de Rotas|
|[writeRota](anexos/#tbrotas)|conta_id|CRUD tabela de Rotas|
|[writeLinha](anexos/#tblinhas)|conta_id|CRUD tabela de Linhas |  
|[writeColetor](anexos/#tbcoletores)|conta_id|CRUD tabela coletores/motoristas|
|[writeProdutor](anexos/#tbprodutores)|conta_id|CRUD tabela produtores|
|[writeFazenda](anexos/#tbfazendas)|conta_id|CRUD tabela Fazendas|
|[writeVeiculo](anexos/#tbveiculos)|conta_id|CRUD tabela veículos transportadores|
|[writeTanque](anexos/#tbtanques)|conta_id|CRUD tabela Tanques de armazenamento|
|[writeExtrato](anexos/#tbextratos)|conta_id|CRUD tabela extratos de coletas dos produtores|
|[writeItinerario](anexos/#tbitinerarios)|conta_id|CRUD tabela Itinerarios e ordem de coleta|
|[writeTecnico](anexos/#tbtecnicos)|conta_id|CRUD tabela Tecnicos de plataforma e seguidores de rota|
|[writeTag](anexos/#tbtags)|conta_id|CRUD tabela Tags NFC|
|[writeAnalise](anexos/#tbanalises)|conta_id|CRUD tabela analise de qualidade dos produtos|
|[writeMotivo](anexos/#tbmotivos)|conta_id|CRUD tabela Motivos de Cancelamentos de coletas|
|[writeVinculado](anexos/#tbvinculados)|conta_id|CRUD tabela Tanques Comunitário ou Coletivo|
|[writeSeguidor](anexos/#tbseguidores)|conta_id|CRUD tabela Seguidores de Rota|
