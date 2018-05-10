-----
## Modelos Arquivos JSON 
-----

<a name="tbgruporotas" > 
### **Grupo de Rotas** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeGrupoRota  
  
  Modelo Arquivo JSON Mensagem
```  
{"conta_id":70387,
 "data":[{"codigo":"001",
          "nome":"FM_PARA_MINAS",
		  "deleted":"0"
		 }
		]
}  
```
<a name="tbrotas" > 
### **Rotas**
</a>

 URI: http://app.sclrota.com.br/api/retaguardasync/writeRota  
  
  Modelo Arquivo JSON Mensagem
```  
{"conta_id":70387,
  "data":[{"codigo":"001",
           "nome":"Rota_001",
		   "Tipo_Descarga":"DP",
		   "grupo_rota":"001";
		   "deleted":"0"
		   }
		 ]
 }  
```
<a name="tblinhas" > 
### **Linhas de Coleta** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeLinha  
  
  Modelo Arquivo JSON Mensagem
```  
{"conta_id":70387,
 "data":[{"codigo":"001",
          "nome":"Linha_001",
		  "distancia":"100.00",
		  "rota":"001",
		  "deleted":"0"
		  }
		]
}  
```
<a name="tbcoletores" > 
### **Motoristas / Coletores** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeColetor  
  
  Modelo Arquivo JSON Mensagem
```  
{"conta_id":70387,
 "data":[{"codigo":"001",
          "nome":"Jose Antonio",
		  "rg":"MG 3201011",
		  "cpf":"59613653618",
		  "cnh":"78522552244",		  
		  "deleted":"0"
		  }
		]
}  
```

<a name="tbprodutores" > 
### **Produtores** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeProdutor  
  
  Modelo Arquivo JSON Mensagem
```  
{"conta_id":70387,
 "data":[{"codigo":"P001",
          "ipo":"F"
          "nome":"Jose Maria Melo",
		  "logradouro":"Rua X",
		  "numero":"99",
		  "bairro":"centro",		  
		  "cidade":"Sao Paulo",		  
		  "uf":"SP",		  
		  "cep":"11850000",
		  "doc":"SP 96801125",
		  "ie":"", 		  		  
		  "deleted":"0"
		  }
		]
}  
```

<a name="tbfazendas" > 
### **Fazendas** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeFazenda  
  
  Modelo Arquivo JSON Mensagem
```  
{"conta_id":70387,
 "data":[{"codigo":"F001",
          "nome":"Fazenda Sol Nascente",
		  "logradouro":"Regiao Furquilha",
		  "numero":"00",
		  "bairro":"Zona Rural",		  
		  "cidade":"Sao Paulo",		  
		  "uf":"SP",		  
		  "cep":"11850000",
		  "latitude":"11853345",
		  "longitude":"1195000",
		  "produtor":"P001",		  		  
		  "deleted":"0"
		  },
		  {"codigo":"F002",
          "nome":"Fazenda Miramar",
		  "logradouro":"Rodovia BR 101",
		  "numero":"KM 234",
		  "bairro":"Zona Rural",		  
		  "cidade":"Rio de Janeiro",		  
		  "uf":"RJ",		  
		  "cep":"22530000",
		  "latitude":"11743345",
		  "longitude":"1176000",
		  "produtor":"P002",		  		  
		  "deleted":"0"
		  }
		]
}  
```

<a name="tbveiculos" > 
### **Veículos** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeVeiculo  
  
  Modelo Arquivo JSON Mensagem
```  
{"conta_id":70387,
 "data":[{"codigo":"V001",
          "placa":"XXX-9999",
		  "tipo":"V",
		  "pesobruto":"99999",
		  "pesoliquido":"99999",		  
		  "capacidade":"99999",		  		  		  		  
		  "deleted":"0"
		  }
		]
}  
```
<a name="tbtanques" > 
### **Tanques** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeTanque 

  A Entidade Tanque recebe os registros de todos os repositórios de armazenamento. Resfriadores das fazendas, compartimentos dos veiculos transportadores, balões e silos de armazenamento na plataforma.

  O Atributo "**tipo**" define a função do compartimento e dependendo deste atributo, somente um código de veículo, produtor, fazenda ou coletor será informado, os demais deverão ficar sem valor ("").
  
  Modelo Arquivo JSON Mensagem
```  
{"conta_id":70387,
 "data":[{"codigo":"T001",
          "tipo":"V",
		  "veiculo":"V001",
		  "fazenda":"",
		  "comunitario":"0",		  
		  "comunitario_lancamento":"",		  		  		  		  
		  "comunitario_divisao":"",
		  "comunitario_diferenca":"",		  		  		  		  		  
		  "comunitario_impressao":"",
		  "porcentagem":"",		  		  		  		  	
		  "deleted":"0"
		  }
		]
}  
```
<a name="tbextratos" > 
### **Extratos de Coleta** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeExtrato 

  
  Modelo Arquivo JSON Mensagem
```  
{"conta_id":70387,
 "data":[{"produtor":"P001",
          "dt_coleta":"2016-09-09",
		  "quantidade":"958",
		  "temperatura":"2.5"		  
		  },
		  {"produtor":"P001",
          "dt_coleta":"2016-09-07",
		  "quantidade":"1032",
		  "temperatura":"2.8"		  
		  }
		]
}  
```
<a name="tbitinerarios" > 
### **Itinerarios** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeItinerario 

  
  Modelo Arquivo JSON Mensagem
```  
{"conta_id":70387,
 "data":[{"fazenda":"F001",
          "rota":"R001",
		  "linha":"L001",
		  "ordem":"1"	
		  "horario":"07:00" 	
		  },
		 {"fazenda":"F003",
          "rota":"R001",
		  "linha":"L001",
		  "ordem":"2"	
		  "horario":"07:45" 	
		  }
		]
}  
```
<a name="tbtecnicos" > 
### **Tecnicos de Plataforma e Seguidores de Rota** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeTecnico  
  
  Modelo Arquivo JSON Mensagem
```  
{"conta_id":70387,
 "data":[{"codigo":"L001",
          "nome":"Joao Carlos Cardoso",
		  "rg":"MG 7022015",
		  "cpf":"59613653688",
		  "email":"j.carloscardoso@gmail.com",		  
		  "telefone":"37999811133",		  
		  "imei":"7522999855554445",		  		  
		  "deleted":"0"
		  }
		]
}  
```
<a name="tbtags" > 
### **Tags NFC ** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeTag  
  
  Modelo Arquivo JSON Mensagem
  
  O Atributo "**tipo**" define que ator será identificado e dependendo deste atributo, somente um código de veículo, tanque, tecnico ou coletor será informado, os demais deverão ficar sem valor ("").
```  
{"conta_id":70387,
 "data":[{"tipo":"V",
          "tagid":"AAA174E45",
		  "coletor":"",
		  "tecnico":"",
		  "tanque":"",		  
		  "veiculo":"V001",		  		  
		  "deleted":"0"
		  }
		]
}  
```
<a name="tbanalises" > 
### **Resultados das Analises de qualidade ** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeAnalise  
  
  Modelo Arquivo JSON Mensagem  
  
```  
{"conta_id":70387,
 "data":[{"produtor":"P001",
          "teor_gordura":"305",
		  "ccs":"400",
		  "ufc":"100",
		  "proteinas":"2000",		  
		  "esd":"450",
          "lactose":"",		  
		  "deleted":"0"
		  }
		]
}  
```
<a name="tbmotivos" > 
### **Motivos de cancelamento de coletas aceitáveis ** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeMotivo  
  
  Modelo Arquivo JSON Mensagem  
  
```  
{"conta_id":70387,
 "data":[{"codigo":"MC001",
          "motivo":"Lama na Estrada",
		  "exige_foto":"1",
		  "envia_notificação":"0",
		  "gravidade":"B"		  		  		  		  
		  }
		]
}  
```
    
<a name="tbvinculados" > 
### **Produtores Participantes dos Tanques Coletivos ou Comunitários** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeVinculado  
  
  Modelo Arquivo JSON Mensagem  
  
  O atributo "**proprietario**" devine o participante responsável pelo registros de volume armazenados no tanque, e dependendo da configuração da plataforma, as diferenças podem ser creditadas ou debitadas na conta deste produtor. Somente um registro deve ser envidado com esta propriedade assinalada com "1" para cada conjunto de participantes de um mesmo tanque.
  
```  
{"conta_id":70387,
 "data":[{"codigo":"001",
          "tanque":"T001",
		  "produtor":"P001",
		  "proprietario":"1",
		  "procentagem":"60"		  		  		  		  
		  },
		  {"codigo":"002",
          "tanque":"T001",
		  "produtor":"P005",
		  "proprietario":"0",
		  "procentagem":"40"		  		  		  		  
		  }
		]
}  
```
<a name="tbseguidores" > 
### **Notificações para seguidores de rota ** 
</a>
  URI: http://app.sclrota.com.br/api/retaguardasync/writeSeguidor  
  
  Modelo Arquivo JSON Mensagem  
  
```  
{"conta_id":70387,
 "data":[{"codigo":"001",
          "gruporota":"0001",
		  "tecnico":"L001",
		  "baixa":"0",
		  "media":"1",
		  "alta":"1",
		  "deleted":"0"	
		  }
		]
}  
```