# Métodos Leitura e Exclusão  - Manutenção das informações no Servidor

Os métodos abaixo estão disponíveis para chamada externa da API.

## Apagar Analises

Reseta todos os dados de análise de uma conta.

|Método | URL
|-------|----
|clearAlise |**http://app.sclrota.com.br/api/retaguardasync/clearAnalise**


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível excluir os dados<br>__true__: exclusão bem sucedida
| data    | Mensagem de confirmação do resultado

___


## Apagar dados da conta

Reseta todos os dados de uma conta, mas não exclui o registro da conta.

|Método | URL
|-------|----
|clearConta |**http://app.sclrota.com.br/api/retaguardasync/clearConta**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| doc       | Documento CNPJ vinculado ao registro da conta


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível excluir os dados<br>__true__: exclusão bem sucedida
| data    | Mensagem de confirmação do resultado

___

## Apagar Extrato

Reseta todos os dados de extrato de uma conta.

|Método | URL
|-------|----
|clearExtrato |**http://app.sclrota.com.br/api/retaguardasync/clearExtrato**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível excluir os dados<br>__true__: exclusão bem sucedida
| data    | Mensagem de confirmação do resultado

___

## Apagar Grupos de Rotas

Reseta todos os dados os grupos de rota vinculados a uma conta.

|Método | URL
|-------|----
|clearGrupoRota|**http://app.sclrota.com.br/api/retaguardasync/clearGrupoRota**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível excluir os dados<br>__true__: exclusão bem sucedida
| data    | Mensagem de confirmação do resultado

___

## Apagar Itinerário

Reseta todos os dados de itinerários vinculados a uma conta.

|Método | URL
|-------|----
|clearItinerario |**http://app.sclrota.com.br/api/retaguardasync/clearItinerario**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível excluir os dados<br>__true__: exclusão bem sucedida
| data    | Mensagem de confirmação do resultado

___

## Fechar Vigência do Itinerário de uma linha de coleta

Seta uma data de vigência final para o itinerário de coleta de uma determinada linha da conta.

|Método | URL
|-------|----
|closeItinerario |**http://app.sclrota.com.br/api/retaguardasync/closeItinerario**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| doc       | CNPJ cadastrado para a conta (com máscara : 99.99.999/9999-99
| linha     | código da linha onde será executado o fechamento


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível fechar a vigência<br>__true__: fechamento executado
| data    | Mensagem de confirmação do resultado

___


## Apagar Tags NFC

Reseta todos os dados de tags NFC vinculadas a uma conta.

|Método | URL
|-------|----
|clearTag |**http://app.sclrota.com.br/api/retaguardasync/clearTag**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível excluir os dados<br>__true__: exclusão bem sucedida
| data    | Mensagem de confirmação do resultado

___

## Apagar Produtores Vinculados

Reseta todos os dados de tanques vinculados de uma conta.

|Método | URL
|-------|----
|clearVinculado |**http://app.sclrota.com.br/api/retaguardasync/clearVinculado**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível excluir os dados<br>__true__: exclusão bem sucedida
| data    | Mensagem de confirmação do resultado

___

## Ler Coletas

Recupera todos os registros de coletas realizadas em um período, vinculadas a uma conta.

|Método | URL
|-------|----
|readColeta |**http://app.sclrota.com.br/api/retaguardasync/readColeta**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado
| comunitario | 1 => Se deverão ser listadas apenas os registros principais da coleta em tanque comunitários<br> 0 => Se irá listar apenas coletas comuns


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros da coleta

### Estrutura do Registro da coleta

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro da coleta na API |
| parada_id | Identificação única do registro de visita na API |
| coletor_id | Identificação Única do agente de coleta na API|
| produtor_id | Identificação Única do produtor na API |
| conta_id | Identificação Única da conta na API |
| quantidade | Volume da coleta  |
| dt_coleta | Data de realização da coleta no formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__
| coletada  | 1 => Coleta realizada<br> 0 => Coleta não realizada
| alizarol  | 1 => Passou no exame de alizarol<br> 0 => Não passou no exame de alizarol
| tipo_alizarol | Tipo do alizarol utilizado no exame
| temperatura | Temperatura do tanque resfriador no momento da coleta
| dt_edicao | Se o registro foi editado pelo agente de coleta, é data da edição no formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__
| regua | Medida da régua aferida pelo agente de coleta
| amostra | Número da amostra utilizada
| contraprova | Número do lacre da contra-prova da amostra
| comunitaria | 1 => Se o registro representa a coleta principal de um tanque comunitário<br> 0 => Coleta comum
| vinculada   | 0 => A coleta não é vinculada a um tanque comunitário <br> 1 => A coleta não é vinculada a um tanque comunitário
| diferenca   | Valor da diferença entre o volume informado pelo tanque comunitário e o valor aferido
| distribuida | Se o registro da coleta comunitária já foi distribuído
| informado | Volume informado no tanque comunitário
| latitude | Coordenada geográfica do local de realização da coleta
| longitude | Cooredenada geográfica do local de realização da coleta
| exame_visual | 1 => Característico para exame visual<br> 0 => Não característico para exame visual
| tanque | Código de identificação do tanque no ERP
| fazenda  | Código de identificação da fazenda no ERP
| viagem_id | Identificação Única da viagem na API
| coletor | Código de identificação do agente de coleta no ERP
| produtor | Código de identificação do produtor no ERP
| boca | Compartimentos de armazenamento do leite no veículo

## Ler Coletor (Agentes de Coleta / Motoristas)

recupera os registros dos agentes de coleta

|Método | URL
|-------|----
|readColetor |**http://app.sclrota.com.br/api/retaguardasync/readColetor**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros dos agentes de coleta

### Estrutura do Registro de Agente de Coleta

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro do agente na API |
| conta_id | Identificação única do conta na API |
| dt_push | Data de criação do registro na base de dados da API|
| nome | Nome do agente de coleta / Motorista |
| rg | Número da Identidade / Documento de Identificação do agente de coleta |
| cpf | Número do C.P.F. do agente de coleta  |
| cnh  | Número da Carteira Nacional de Habilitação do agente de coleta |
| dt_create | Data da última atualização do registro na base da API, no formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__
| dt_deleted  | Data da exclusão lógica do registro na base da API, no formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__
| deleted | 1 => Registro Excluído<br> 0 => Registro ativo
| codigo | Código de Identificação do agente de coleta no ERP
| avatar | Imagem no formato BASE64 (Foto do agente de coleta)


## Ler Distribuição (Tanques Coletivos)

recupera os registros de distribuição de volumes para cada participante de tanques coletivos/comunitários em um período

|Método | URL
|-------|----
|readColetaComunitaria |**http://app.sclrota.com.br/api/retaguardasync/readColetaComunitaria**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado
| comunitario | 1 => Se deverão ser listadas apenas os registros principais da coleta em tanque comunitários<br> 0 => Se irá listar apenas coletas comuns


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros da distribuição

### Estrutura do Registro de distribuição das coletas

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro da coleta na API |
| parada_id | Identificação única do registro de visita na API |
| coletor_id | Identificação Única do agente de coleta na API|
| produtor_id | Identificação Única do produtor na API |
| conta_id | Identificação Única da conta na API |
| quantidade | Volume da coleta  |
| dt_coleta | Data de realização da coleta no formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__
| coletada  | 1 => Coleta realizada<br> 0 => Coleta não realizada
| alizarol  | 1 => Passou no exame de alizarol<br> 0 => Não passou no exame de alizarol
| tipo_alizarol | Tipo do alizarol utilizado no exame
| temperatura | Temperatura do tanque resfriador no momento da coleta
| dt_edicao | Se o registro foi editado pelo agente de coleta, é data da edição no formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__
| regua | Medida da régua aferida pelo agente de coleta
| amostra | Número da amostra utilizada
| contraprova | Número do lacre da contra-prova da amostra
| comunitaria | 1 => Se o registro representa a coleta principal de um tanque comunitário<br> 0 => Coleta comum
| vinculada   | 0 => A coleta não é vinculada a um tanque comunitário <br> 1 => A coleta não é vinculada a um tanque comunitário
| diferenca   | Valor da diferença entre o volume informado pelo tanque comunitário e o valor aferido
| distribuida | Se o registro da coleta comunitária já foi distribuído
| informado | Volume informado no tanque comunitário
| latitude | Coordenada geográfica do local de realização da coleta
| longitude | Cooredenada geográfica do local de realização da coleta
| exame_visual | 1 => Característico para exame visual<br> 0 => Não característico para exame visual
| tanque | Código de identificação do tanque no ERP
| fazenda  | Código de identificação da fazenda no ERP
| viagem_id | Identificação Única da viagem na API
| coletor | Código de identificação do agente de coleta no ERP
| produtor | Código de identificação do produtor no ERP
| boca | Compartimentos de armazenamento do leite no veículo


## Ler Descargas

recupera os registros das descargas e volumes armazenados nos balões e silos da plataforma, ao final das viagens

|Método | URL
|-------|----
|readDescarga |**http://app.sclrota.com.br/api/retaguardasync/readDescarga**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros da descarga

### Estrutura do Registro de descargas e armazenamento

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| viagem_id | Identificação única da viagem na API |
| tanque_id | Identificação Única do tanque, balão ou Silo na base de dados da API|
| coletor_id | Identificação Única do agente de coleta / Motorista na base de dados da API |
| produtor_id | Identificação Única do produtor na base de dados da API (Responsável por um cancelamento de armazenamento) |
| balao_id | Identificação Única do balão - Compartimento de Plataforma na API  |
| pesagem_inicial_id  | Identificação Única do registro de pesagem inicial do veículo, quando tipo de descarga for por pesagem |
| pesagem_final_id | Identificação Única do registro de pesagem final do veículo, quando tipo de descarga for por pesagem |
| conta_id | Identificação Única do registro da conta na API |
| qtd_coletado | Volume em litros anotado nos registros de coleta pelo agente de coleta
| qtd_armazenado | Volume real aferido e armazenado na plataforma de descarga
| peso_coletado | Peso referente á quantidade informada pelo agente de coleta
| peso_armazenado | Peso referente á quantidade real armazenada na platafora de descarga
| dt_descarga | Data da descarga, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__
| origem_cancelamento | Ator que deu origem ao cancelamento do armazenamento, quando ocorrer (Produtor ou Agente de Coleta)
| motivo_cancelamento | Motivo do cancelamento do armazenamento (Antibiótico detectado, acidez elevada, etc )
| cancelada | 1 => Armazenamento não realizado pelo motivo informado<br> 0 => Armazenamento realizado normalmente |
| foto_ticket | Imagem BASE64 do ticket de descarga ou medidor de vazão com volume aferido e atesto |
| tecnico_id | Identificação Única técnico de plataforma que executou a descarga do volume |
| tanque_veiculo | Identificação Única do compartimento de armazenamento origem do volume no veículo |
| balao | Código do balão, silo ou tanque no ERP |
| produtor | Código do produtor que deu origem a um possível cancelamento de armazenamento de volume |
| coletor | Código do agente de coleta que deu origem a um possível cancelamento |

## Ler Fazendas

recupera os registros das fazendas

|Método | URL
|-------|----
|readFazenda |**http://app.sclrota.com.br/api/retaguardasync/readFazenda**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros das fazendas

### Estrutura do Registro de Fazendas

| Campo | Descrição |
|-------|-----------|
| id | identificação Única do registro na API |
| produtor_id | Identificação Única do produtor na API |
| conta_id | Identificação Única da conta na API |
| codigo | Identificação da fazenda no ERP |
| producao | Estimativa de produção |
| numero | Número do endereço da fazenda |
| logradouro | Endereço da fazenda |
| bairro | Bairro onde se localiza a fazenda |
| municipio | Cidade onde se localiza a fazenda |
| uf | Unidade da federação - endereço da fazenda |
| cep | Código de identificação postal da fazenda |
| latitiude |coordenada geofrafica de localização da fazenda |
| longitude | coordenada geofrafica de localização da fazenda |
| nome | Nome do produtor |
| dt_created |Data de gravação do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__
| dt_deleted |Data da exclusão lógica do registro, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__
| deleted | 1 => Registro Inativo<br> 0 => Registro Ativo
| produtor | Código do produtor no ERP, proprietário da fazenda |

## Ler Grupos de Rotas

recupera os registros de grupos de rotas

|Método | URL
|-------|----
|readGrupoRota |**http://app.sclrota.com.br/api/retaguardasync/readGrupoRota**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros do grupo de rotas

### Estrutura do Registro de Grupo de Rotas

| Campo | Descrição |
|-------|-----------|
| id | identificação Única do registro na API |
| nome | Nome do grupo de rotas no ERP |
| conta_id | Identificação Única da conta na API |
| codigo | Identificação do grupo de rotas no ERP |
| deleted | 1 => Registro Inativo<br> 0 => Registro Ativo |

## Ler Itinerários

recupera os registros dos itinerário

|Método | URL
|-------|----
|readItinerario |**http://app.sclrota.com.br/api/retaguardasync/readItinerario**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros dos itinerários

### Estrutura do Registro de itinerario

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro do agente na API |
| conta_id | Identificação única do conta na API |
| fazenda_id | Identificação Única da fazenda na API |
| linha_id | Identificação Única da linha na API|
| tanque_id | Identificação Única do tanque na API|
| ordem | Ordem de coleta no itinerário |
| codigo | código de itenficação do registro no ERP |
| horario  | Horário previsto de realização da coleta |
| dt_push | Data da última atualização do registro na base da API, no formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| coleta_seletiva  | 1 => Indica que a coleta é seletiva e o volume será armazenado em um compartimento especial do veículo<br> 0 => Coleta normal |
| fazenda | Código de Identificação da fazenda no ERP |
| tanque | Código do Ponto de Coleta (Tanque/Resfriador)  no ERP |
| linha | Código de Identificação da linha de coleta no ERP |
| deleted | 1 => Registro Inativo<br> 0 => Registro Ativo |

## Ler Linhas

recupera os registros das linhas de coleta

|Método | URL
|-------|----
|readLinha |**http://app.sclrota.com.br/api/retaguardasync/readLinha**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros das linhas de coleta

### Estrutura do Registro de Linha

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro da linha na API |
| conta_id | Identificação única do conta na API |
| rota_id | Identificação Única da rota na API |
| dt_push | Data da última atualização do registro na base da API, no formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__
| codigo | código de itenficação da linha no ERP |
| nome | Nome da linha  |
| distancia | Distância prevista para deslocamento em km |
| deleted | 1 => Registro Inativo<br> 0 => Registro Ativo |

## Ler Motivos Cancelamento (Justificativas)

recupera os registros de Justificativas de cancelamento de coleta

|Método | URL
|-------|----
|readMotivo |**http://app.sclrota.com.br/api/retaguardasync/readMotivo**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros das justificativas de cancelamento

### Estrutura do Registro de Motivos de Cancelamento

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| conta_id | Identificação única do conta na API |
| codigo | código de itenficação do motivo de cancelamento no ERP |
| motivo | Descrição do motivo de cancelamento   |
| exige_foto | 1 => Exige que seja feita uma foto para confirmação da justificativa<br> 0 => Foto não obrigatória |
| envia_notificacao | 0 => Não notifica os seguidores de rota sobre ocorrência<br> 1 => Notifica seguidores de rota da ocorrência |
| gravidade | A => Alta<br> M =>Média <br> B => Baixa |
| deleted | 1 => Registro Inativo<br> 0 => Registro Ativo |


## Ler Ocorrências

recupera os registros de ocorrências registradas na viagens

|Método | URL
|-------|----
|readOcorrencia |**http://app.sclrota.com.br/api/retaguardasync/readOcorrencia**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros das ocorrêncas

### Estrutura do Registro de Ocorrências

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| visita_id | Identificação única do registro de visita na viagem na API |
| dt_ocorrencia | Data da ocorrência, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| ocorrencia | Descrição da ocorr6encia  |
| foto | Imagem no formato BASE64 da ocorrência |
| latitude | Coordenada geográfica do local da ocorrência |
| longitude | Coordenada geográfica do local da ocorrência |
| fazenda_id | Identificação Única da Fazenda na API |
| viagem_id | Identificação única da Viagem na API |

## Ler Produtores

recupera os registros dos produtores

|Método | URL
|-------|----
|readProdutor |**http://app.sclrota.com.br/api/retaguardasync/readProdutor**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros dos Produtores

### Estrutura do Registro de Produtor

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| Tipo  | Tipo de Pessoa **(F) Física (J) Jurídica** |
| conta_id | Identificação única do conta na API |
| dt_push | Data da última atualização do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| codigo | Código de identificação do produtor no ERP  |
| nome | Nome do Produtor |
| numero | Número do endereço do produtor |
| logradouro | Endereço do Produtor |
| cidade | Cidade do endereço do Produtor |
| doc | Documento de Identificação do Produtor |
| ie    | Inscrição Estadual para pessoas jurídicas |
| uf | Estado no endereço do Produtor |
| cep | Código de endereçamento postal do produtor |
| dt_create | Data de criação do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| dt_delete | Data da exclusão lógica do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| deleted | 1 => Registro Inativo<br> 0 => Registro Ativo |

## Ler Resumo das coletas

recupera os registros resumidos das coletas de uma viagem específica

|Método | URL
|-------|----
|readResumoColeta |**http://app.sclrota.com.br/api/retaguardasync/readResumoColeta**|


### Parâmetros da requisição

| Parâmetro   | Descrição
|-------------|----------
| conta_id    | Código de identificação da conta
| token       | Token de autorização da conta na API
| doc         | CNPJ da empresa,registrado no cadastro da conta
| viagem_id   | Identificador único da viagem 
| comunitario | __(0) Retorna apenas coletas individuais (1) retorna apenas distribuiçao tanques comunitários__

__Obs: Uma chamada deve ser feita para receber as coletas individuais e outra para receber a distribuição dos tanques coletivos/comunitários
afim de se obter todos os registros com o volume total da viagem.__

### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros das coletas da viagem indicada



### Estrutura do Registro de Resumo de Coletas

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| dt_push | Data e Hora de gravação do registro , formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| parada_id | Identificador único do registro da visita |
| coletor_id | Identificador único do motorista/agente de coletas |
| tanque_id | Identificador único do tanque (ponto de coleta) |
| viagem | Identificador único da viagem (viagem_id) solicitado |
| dt_coleta | Data e Hora da coleta , formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__  |
| CodigoFazenda | Código da Fazenda onde ocorreu a coleta |
| NomeFazenda | Nome da Fazenda onde ocorreu a coleta |
| CodigoProdutor | Código do Produtor |
| NomeProdutor | Nome do Produtor |
| Tanque | Código do Tanques (Ponto de coleta) na Fazenda onde ocorreu a coleta |
| Quantidade | quantidade de leite coletado |
| Regua | Medida da régua obtida do volume coletado |
| Alizarol | Resultado do exame de alizarol (acidez) __"(1) Aprovado, (2) Reprovado"__ |
| Amostra | Número da amostra de rastreabilidade  |
| Contraprova | Número de Amostra para contraprova de exames laboratoriais |
| Temperatura | Temperatura registrada no momento da coleta |
| Coletada | Indica se o volume foi coletado ou não __"(1) Coletado (0) Não Coletado"__|
| Codigolinha | Código da principal linha de coleta percorrida na viagem  |
| Nomelinha | Nome da linha de coleta da viagem|
| CodigoRota |Código da Rota (agrupamento de linhas) selecionado na viagem |
| Rota |Nome da rota selecionada na viagem |
| Veiculo |Placa do veículo utilizado para realizar a viagem |
| CodigoMotorista |Código do agente de coleta que executou a vaigem (Motorista) |
| NomeMotorista |Nome do agente de coleta que executou a viagem  |
| dt_edicao | Data e Hora da ultimaalteração no registro , formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__  |



## Ler Resumo das viagens

recupera os registros de resumo das viagens finalizadas em um período

|Método | URL
|-------|----
|readResumoViagem |**http://app.sclrota.com.br/api/retaguardasync/readResumoViagem**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros das Rotas



### Estrutura do Registro de Resumo de Viagens

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| dt_abertura | Data e Hora de Início da viagem , formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| dt_fechamento | Data e Hora do Encerramento da viagem na plataforma , formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| km_inicial | Quilometragem na abertura da viagem |
| km_final | Quilometragem no fechamento da viagem |
| km_distancia | Distância percorrida na viagem |
| veiculo_placa | Placa do veículo utilizado na viagem |
| veiculo_codigo | Código do veículo na Plataforma  |
| linha_codigo | Código da principal linha de coleta percorrida na vaigem  |
| linha_nome | Nome da linha de coleta da viagem|
| rota_codigo |Código da Rota (agrupamento de linhas) selecionado na viagem |
| rota_nome |Nome da rota selecionada na viagem |
| tipo_descarga |Indicador da forma de controle de descarga na plataforma <br> TP => Por Taque através do painel de controle<br> TC => Por Tanque feita pelo próprio agente de coleta <br> PP => Plataforma Pesagem <br> PC=> Pesagem pelo agente de coleta |
| coletor_codigo |Código do agente de coleta que executou a vaigem (Motorista) |
| coletor_codigo |Nome do agente de coleta que executou a viagem  |
| tecnico_codigo |Código do técnico de paltaforma que registrou a descarga da viagem |
| tecnico_nome |Nome do técnico de paltaforma que atuou na descarga da viagem |
| coletas_realizadas |Número de coletas efetivadas na viagem |
| coletas_canceladas |Número de coletas canceladas na viagem |
| coletas_pendentes |Número de coletas planejadas mas não efetivadas ou canceladas na viagem |
| volume_coletado |Volume total informado pelo agente de coleta |
| volume_aferido |Volume total aferido pelo técnico na descarga (volume efetivo armazenado) |
| volume_descartado |Volume total descartado (Motivos diversos - produto não aproveitado - antibiotico, improprio) |
| atesto |Volume total referente a diferença entre o volume informado , volume descartado e volume realmente aferido  |
| descarregada | 1 => Dados da descarga forma inseridos para esta viagem<br> 0 => Dados da descarga ainda não foram inseridos para esta viagem |


## Ler Rotas

recupera os registros de rotas

|Método | URL
|-------|----
|readRota |**http://app.sclrota.com.br/api/retaguardasync/readRota**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros das Rotas

### Estrutura do Registro de Rota

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| conta_id | Identificação única do conta na API |
| grupo_rota_id | Identificação única do grupo de rotas na API |
| dt_push | Data da última atualização do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| codigo | Código de identificação do produtor no ERP  |
| nome | Nome da rota |
| tipo_descarga |TT => Tanque por Técnio<br>TC => Tanque pelo Coletor<br>TP =>Tanque pela Plataforma<br>PT =>Pesagem pelo Técnico<br>PC =>Pesagem pelo Coletor<br>PP =>Pesagem pela Plataforma |
| deleted | 1 => Registro Inativo<br> 0 => Registro Ativo |

## Ler Seguidores de Rota

recupera os registros de Seguidores de rota

|Método | URL
|-------|----
|readSeguidor |**http://app.sclrota.com.br/api/retaguardasync/readSeguidor**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros dos Seguidores de  Rotas

### Estrutura do Registro de Seguidor de  Rota

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| alta | Recebe notificação de graviade Alta <br> 1 => Sim // 0 => Não |
| media | Recebe notificação de graviade Média <br> 1 => Sim // 0 => Não |
| baixa | Recebe notificação de graviade Baixa <br> 1 => Sim // 0 => Não |
| grupo_rota_id | Identificação única do grupo de rotas na API |
| tecnico_id | Identificação Única do técncio seguidor na API |
| conta_id | Ientificação Única da conta na API |
| codigo | Código de identificação do Seguidor de Rota no ERP  |
| gruporota | Código de identificação do Grupo de Rota no ERP |
| tecnico | Código de identificação do Técnico no ERP |

## Ler Tags NFC

recupera os registros de Tag NFC e seus respectivos vinculos de utilização

|Método | URL
|-------|----
|readTag |**http://app.sclrota.com.br/api/retaguardasync/readTag**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros das Tags NFC

### Estrutura do Registro de Tag NFC

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| conta_id | Ientificação Única da conta na API |
| tipo | F => Tanque de Fazenda<br>C =>Coletor (Agente Coleta)<br>V => Veículo<br>L =>Técnico de Plataforma/Laboratório |
| tecnico_id | Identificação Única do técncio seguidor na API |
| tag_id | Identificação Única da Tag vinculada ao ERP e na API |
| tanque_id | Identificação Única do tanque de coleta na API |
| coletor_id | Identificação Única do agente de coleta na API |
| veiculo_id | Identificação Única do veículo na API |
| tanque | Código de identifcação do tanque no ERP |
| veiculo| Código de identificação do veículo no ERP |
| coletor | Código de identificaáco do agente de coleta no ERP |
| tecnico | Código de identificação do técnico de plataforma no ERP  |
| dt_create | Data de criação do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| dt_push | Data da última atualização do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| deleted | 1 => Registro Inativo<br> 0 => Registro Ativo |

## Ler Tanques

recupera os registros de Tanques de armazenamento nos pontos de coleta, veículo e plataforma de descarga

|Método | URL
|-------|----
|readTanque |**http://app.sclrota.com.br/api/retaguardasync/readTanque**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros dos Tanques

### Estrutura do Registro de Tanques

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| tipo | F => Tanque de Fazenda<br>V => Veículo<br>P =>Plataforma (Balões e Silos de Armazenamento) |
| conta_id | Ientificação Única da conta na API |
| veiculo_id | Identificação Única do veículo na API |
| fazenda_id | Identificação Única da fazenda onde se localiza o tanque na API |
| dt_create | Data de criação do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| dt_push | Data da última atualização do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| dt_delete | Data da exclusão lógica do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| deleted | 1 => Registro Inativo<br> 0 => Registro Ativo |
| capacidade | Capacidade total de armazenamento do tanque |
| altura | Medida da altura do tanque em Centímetros |
| perimetro | Medida da circunferéncia do tanque |
| volume | Volume máximo comportado no tanque |
| codigo | Código de identificação do Tanque no ERP |
| comunitario | 1 => Tanque Coletivo ou comunitário<br> 0 => Tanque individual |
| comunitario_lancamento | DC => Distribuição feita pelo agente de coleta<br> DP => Distribuição feita no painel de administração (Plataforma)<br> DA=>Distribuição pelo App Tanque Coletivo |
| comunitario_diferenca | P => Proprietário assume toda diferança<br> D => Distribui diferença proporcionalmente ao fornecimento para cada participante  |
| porcentagem |Percentual de distribição - sem efeito |
| comunitario_divisao |M => Manual (Agente de Coleta Informa)<br> A => Automática por percentual |
| comunitario_impressao |D => Detalhada(Imprime a distribuiçao no ticket de coleta)<br> S =>Simplificada (Não imprime distribuição no ticket de coleta) |
| coleta_seletiva | 1 => indica que a coleta neste tanque deve ser armazenada em compartimento especial no veículo<br> 0 => Armazenamento normal |
| veiculo | Código de Identificação do veículo no ERP |
| fazenda | Código de Identificação da Fazenda no ERP |
| email | Credencial de aceso ao tanque comunitário pelo App tanque coletivo |
| senha | senha de registro no App Tanque Coletivo |

## Ler Tecnicos

recupera os registros dos técnicos de plataforma, administradores e seguidores de rota

|Método | URL
|-------|----
|readTecnico |**http://app.sclrota.com.br/api/retaguardasync/readTecnio**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros dos Tecnicos

### Estrutura do Registro de Tecnico

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| conta_id | Identificação única do conta na API |
| dt_push | Data da última atualização do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| codigo | Código de identificação do técnico no ERP  |
| nome | Nome do Técnico |
| rg | Número do documento de identificação do técnico |
| cpf | Número do C.P.F. do técnico |
| email | endereço eletrônico para recepção da notificações enviadas pela plataforma |
| telefone | Numero completo do telefone celular do técnico para recebimento de notificações SMS |
| imei | Número de IMEI, identificador único do celular do técnico para recebimento de notificações SMS |
| senha | Senha de acesso á plataforma |
| dt_create | Data de criação do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| dt_delete | Data da exclusão lógica do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| deleted | 1 => Registro Inativo<br> 0 => Registro Ativo |

## Ler Veiculo

recupera os registros dos veículos cadastrados na plataforma.

|Método | URL
|-------|----
|readVeiculo |**http://app.sclrota.com.br/api/retaguardasync/readVeiculo**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros dos Veículos

### Estrutura do Registro de Veículo

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| conta_id | Identificação única do conta na API |
| dt_push | Data da última atualização do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| codigo | Código de identificação do veículo no ERP  |
| placa | placa do veículo |
| tipo | V => Veículo<br> R => Reboque (Julieta) |
| pesobruto | peso bruto do veículo |
| pesoliquido | Peso líquido do veículo |
| capacidade | Capacidade total de transporte do tanque de leite |
| deleted | 1 => Registro Inativo<br> 0 => Registro Ativo |

## Ler Viagem

recupera os registros das viagens finalizadas em um período.

|Método | URL
|-------|----
|readViagem |**http://app.sclrota.com.br/api/retaguardasync/readViagem**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros de Viagens

### Estrutura do Registro de Viagens

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| conta_id | Identificação única do conta na API |
| veiculo_id | Identificação Única do Veículo na API |
| Coletor_id |Identificação Única do Agente de Coleta na API |
| linha_id |Identificação Única da Linha na API |
| rota_id |Identificação Única da Rota  na API |
| tecnico_id |Identificação Única do Técnico na API |
| dt_push | Data da última atualização do registro na API, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| dt_abertura | Data da abertura da viagem, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| dt_fechamento | Data do encerramento da viagem , formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| dt_descarga | Data da descarga na plataforma, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| dt_liberacao | Data de liberação para descarga, caso viagem travada por algum motivo, formato __"ANO-MES-DIA HORA:MINUTO:SEGUNDO"__ |
| km_inicial |Quilomentragem inicial do veículo ao iniciar a viagem |
| km_final | Quilometragem final do veículo ao chegar na plataforma de descarga |
| distancia | distância percorrida na viagem (diferença entre km_final e km_inicial) |
| km_justificativa | Justificativa de deslocamento maior ou menor que o previsto para a linha de coleta |
| liberada | 0 => Viagem liberada sem intercorrência<br> 1 => viagem não liberada, requer intervenção do administrador |
| coletado | - sem efeito |
| removida | 0 => viagem Ativa <br> 1 => viagem removida logicamente - Não listada no painel |
| token | token de identificação da viagem entre a aplicação e o painel - deteção de falha de sincronização |
| app_version | Versão do aplicativo coletor que gerou a viagem |
| rota | Código de identificação da rota no ERP  |
| veiculo | Código de Identificação do Veículo no ERP |
| linha | Código de Identificação da Linha no ERP |
| coletor | Código de identificação do agente de coleta (Motorista) no ERP|
| comunitario_pendente | 0 => Distribuição dos tanques coletivos da viagem já resolvidos<br> 1 => Pendência de distribuição de volume em tanques coletivos |
| bocas | Quantidade de compartimentos no veículo utilizados no trasnporte do produto |

## Ler Vinculados

recupera os registros dos produtores vinculados em tanques coletivos.

|Método | URL
|-------|----
|readVinculado |**http://app.sclrota.com.br/api/retaguardasync/readVinculado**|


### Parâmetros da requisição

| Parâmetro | Descrição
|-----------|----------
| conta_id  | Código de identificação da conta
| token     | Token de autorização da conta na API
| dt_inicio | Data de início do período desejado
| dt_fim    | Data de término do período desejado


### Retorno

| Retorno | Descrição | Valores
|---------|-----------|-------
| success | Se a operação foi bem sucedida ou não | __false__: não foi possível recuperar os dados<br>__true__: operação bem sucedida
| message | Mensagem de confirmação do resultado
| data    | Array de objetos JSON representando os registros do produtores vinculados

### Estrutura do Registro de produtores vinculados

| Campo | Descrição |
|-------|-----------|
| id    | Identificação única do registro na API |
| tanque_id | Identificação única do tanque coletivo na API |
| produtor_id | Identificação única do produtor na API|
| porcentagem | Porcentagem do volume coletado a ser distribuído automaticamente para o produtor em caso de distribuição automática no tanque  |
| proprietario | 1 => Administrador ou propríetário do tanque<br> 0 => Participante comum |
| tanque | Código de Identificação do Tanque no ERP |
| produtor | Código de Identificação do Produtor no ERP |


