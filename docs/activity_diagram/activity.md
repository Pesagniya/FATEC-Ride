| UC03: Publicar Carona |
| --- |

@startuml  
|Motorista|  
start  
:O sistema verifica se tem carro registrado;  

if () then (Sim)  
 :O motorista acessa a tela para oferecer carona;  
 repeat  
 :O motorista insere informações pertinentes;  
 :O sistema valida os dados inseridos;  
 if (Dados válidos?) then (Sim)  
  :A carona é salva no banco de dados e exibida na lista de viagens;  
  break  
 else (Não)  
  :Erro: Dados inválidos;  
 endif  
 repeat while (Cancelar Operação?) is (Não) not (Sim)  
else (Não)  
 :Cadastrar veículo;  
 stop  
endif  
stop  
@enduml  

| UC04: Procurar Carona |
| --- |

@startuml  
|Passageiro|  
start  
:O passageiro entra na tela inicial do sistema de buscar caronas;  
:O passageiro informa ponto de partida e destino;  
:O sistema exibe a lista de caronas correspondentes;
  
if (Selecionar filtros de pesquisa?) then (Não)  
else (Sim)  
if (Carona encontrada?) then (Sim)
else (Não)  
:Não existe caronas que atendam a necessidade do passageiro;  
stop  
endif  
endif  
:O passageiro seleciona a carona;  
:O passageiro visualiza os detalhes da carona;  
stop  
@enduml  

| UC05: Fazer Reserva |
| --- |

@startuml  
|Passageiro|  
start  
:O usuário acessa a viagem que atende as suas preferências;  
:O usuário clica no botão para fazer a reserva; 

if (Operação realizada com sucesso?) then (Sim)  
 :O sistema notifica o motorista sobre a reserva;  
 if (O motorista aceita a reserva do passageiro) then (Sim)  
  :O sistema atualiza o banco de dados e insere a nova reserva;  
 else (Não)  
 stop  
 endif  
else (O usuário tem uma viagem pendente no mesmo horário)  
 :Erro: Indisponibilidade de horário;  
 stop  
endif  
stop  
@enduml  

| UC06: Consultar Chat |
| --- |

@startuml  
|Usuário|  
start  
:O usuário seleciona uma carona na tela de busca ou na tela de viagens;  
:O usuário acessa o perfil entre os participantes da carona;  
:O usuário escreve uma mensagem para outra pessoa;  

if (O usuário envia a mensagem) then (Sim)  
 :A mensagem é salva pelo sistema;  
else (Operação Cancelada)  
 stop  
endif  
stop  
@enduml  

| UC07: Consultar Caronas |
| --- |

@startuml  
|Usuário|  
start  
:O usuário acessa a tela de viagens a partir da barra de menu;  
:O sistema exibe todas as caronas associadas, ordenadas por mês;  
:O usuário seleciona uma viagem para visualizar todos os detalhes;  
stop  
@enduml  

| UC08: Cancelar Viagem |
| --- |

@startuml  
|Usuário|  
start  
:O usuário tem reservas ou publicações de caronas;  
if () then (Sim)  
 :O usuário acessa a tela de viagens a partir da barra de menu;  
 :O usuário seleciona a carona e cancela a viagem;  
 :O sistema notifica as partes interessadas sobre o cancelamento da carona;  
 if (Carona dentro de 2 horas?) then (Sim)  
  :O sistema não reembolsa o passageiro;  
 else (Não)  
 endif  
 :O sistema atualiza as informações da carona;  
else (Não)  
 :Não há viagens para seleção;  
 stop  
endif  
stop  
@enduml  

| UC09: Avaliar Experiência |
| --- |

@startuml  
|Usuário|  
start  
:O usuário avalia o passageiro/motorista por meio do pop-up após a finalização da carona;  
if () then (Não)  
 :O usuário acessa a tela de caronas finalizadas;  
 :O usuário seleciona a carona para avaliação;  
 :O usuário insere a nota (1-5) e feedback sobre a viagem;  
endif  
:O sistema registra a avaliação e atualiza a média do usuário;  
stop  
@enduml  
