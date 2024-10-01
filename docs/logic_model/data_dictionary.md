| Entidade: Usuário |
| --- |

| Nome | Tipo | Descrição | Restrições |
| --- | --- | --- | --- |
| user_id | Númerico | Código de identificação do usuário | PK |
| nome | Texto | Nome do usuário | Not Null |
| email | Texto | E-mail do usuário | Not Null / Unique |
| senha | Texto | Senha do usuário | Not Null |
| role | Caractere | 1 para passageiro (básico), 2 para motorista e 3 para ambos | Not Null |
| foto | BLOB | Foto do usuário | |

___

| Entidade: Review |
| --- |

| Nome | Tipo | Descrição | Restrições |
| --- | --- | --- | --- |
| review_id | Numérico | Código de identificação da review | PK |
| avaliacao | Numérico | Entre 1 e 5 estrelas | Not Null |
| comentario | Texto | Comentário adicional sobre a experiência | |

___

| Entidade: Veículo |
| --- |

| Nome | Tipo | Descrição | Restrições |
| --- | --- | --- | --- |
| id_carro | Numérico | Código de identificação do carro | PK |
| modelo | Texto | Modelo do carro | Not Null |
| ano | Numérico | Ano de fabricação do carro | Not Null |
| placa | Texto | Placa de Identificação do carro | Not Null / Unique |
| cor | Texto | Cor do carro | Not Null |

___

| Entidade: Reserva |
| --- |

| Nome | Tipo | Descrição | Restrições |
| --- | --- | --- | --- |
| reserva_id | Numérico | Código de identificação da reserva | PK |
| data_reserva | Data | Data em qual a reserva foi feita | Not Null |
| status | Booleano | Indica o estado de conclusão da reserva (completo ou cancelado) | Not Null |

___

| Entidade: Pagamento |
| --- |

| Nome | Tipo | Descrição | Restrições |
| --- | --- | --- | --- |
| pagamento_id | Numérico | Código de identificação do pagamento | PK |
| valor | Decimal | Valor da reserva | Not Null |
| data_pagamento | Data | Data de pagamento | Not Null |

___

| Entidade: Carona |
| --- |

| Nome | Tipo | Descrição | Restrições |
| --- | --- | --- | --- |
| carona_id | Numérico | Código de identificação da carona | PK |
| origem | Texto | O ponto de partida da carona | Not Null |
| destination | Texto | O destino da carona | Not Null |
| horario | Data | Horário de partida da carona | Not Null |
| vagas | Numérico | Número de vagas disponíveis na carona | Not Null |
| user_id | Numérico | Chave estrangeira referenciando a tabela Usuário | FK |
| reserva_id | Numérico | Chave estrangeira referenciando a tabela Reserva | FK |

___

| Entidade: Chat |
| --- |

| Nome | Tipo | Descrição | Restrições |
| --- | --- | --- | --- |
| chat_id | Numérico | Código de identificação da carona | PK |
| message | Texto | Conteúdo da mensagem enviada | Not Null |
| timestamp | Data | Data de envio da mensagem | Not Null |

organizar FK
