### Descrição dos Casos de Uso

**Registrar Perfil (UC01)**

- Ator: Novo usuário.
- Pré-condição: O usuário acessa o aplicativo sem ter um perfil registrado.
- Pós-condição: O usuário tem um perfil ativo no sistema.
- Fluxo principal:
1.  O usuário acessa a tela de cadastro.
2.  O usuário preenche o e-mail institucional da FATEC para o processo inicial de verificação.
3.  O sistema envia um código de verificação para o e-mail informado.
4.  O sistema valida o código e procede para a tela de dados pessoais.
5.  O usuário fornece informações relevantes para o seu cadastro, incluindo nome, senha, data de nascimento. placa e modelo de carro (opcional), foto de perfil (opcional), curso (opcional) e minibiografia (opcional).
6.  O sistema valida as informações e cria um perfil para o usuário.
- Fluxo alternativo:
2. O usuário passa o processo de verificação por dados fornecidos pela API do Facebook, e retorna ao passo 3 para as informações restantes.
- Fluxo de exceção:
3. O sistema não permite o cadastro de um usuário que já tenha cadastro no banco de dados.

**Login Aplicação (UC02)**

- Ator: Usuário.
- Pré-condição: O usuário já possui um perfil registrado.
- Pós-condição: O usuário está logado no sistema e pode acessar suas funcionalidades.
- Fluxo principal:
1.  O usuário insere suas credenciais (e-mail e senha).
2.  O sistema autentica o usuário.
3.  O usuário acessa o menu principal do aplicativo.
- Fluxo alternativo:  
1a. O usuário faz o login utilizando suas credencias do Facebook, e retorna ao passo 2.  
1b. O usuário não lembra a senha do perfil e requisita a troca de senha.  
2b. O usuário insere o e-mail da conta.  
3b. O sistema envia um e-mail, redirecionando-o para um link contendo instruções para o procedimento.  
4b. A senha do usuário é redefinida com sucesso, e retorna ao passo 1.

**Publicar Carona (UC03)**

- Ator: Motorista.
- Pré-condição: O usuário deve estar logado no aplicativo e ter um carro registrado no sistema.
- Pós-condição: A carona está disponível para ser reservada por passageiros.
- Fluxo principal:
1.  O motorista acessa a tela direcionada para oferecer caronas a partir da barra de menu.
2.  O motorista insere as informações sobre a carona, incluindo data, horário, local de partida, destino, trajeto e filtros (opcional).
3.  O motorista define o número de vagas disponíveis e o valor estimado por pessoa.
4.  O sistema valida os dados inseridos.
5.  A carona é publicada no sistema.

**Procurar Carona (UC04)**

- Ator: Passageiro.
- Pré-condição: O passageiro está logado no aplicativo.
- Pós-condição: A carona é exibida de acordo com o requisitos especificados.
- Fluxo principal:
1.  O passageiro acessa a tela de buscar caronas a partir da barra de menu.
2.  O passageiro informa o ponto de partida e o destino desejado.
3.  O sistema exibe uma lista de caronas que correspondem ao trajeto.
4.  O passageiro seleciona uma carona de interesse.
5.  O sistema exibe informações pertinentes à carona, incluindo foto de perfil, placa, modelo do carro, número de assentos restantes e preço por vaga.
- Fluxo alternativo:  
3a. O passageiro seleciona filtros na barra de pesquisa para filtrar os resultados (ordenação de preço, data, número de vagas, e filtros personalizados como apenas mulheres), e retorna ao passo 3.  
3b. O passageiro não encontra nenhuma carona que atenda o trajeto e desiste do processo.
  

**Fazer Reserva (UC05)**

- Ator: Passageiro.
- Pré-condição: O passageiro encontrou uma carona disponível que atende as suas preferências.
- Pós-condição: O passageiro possui uma reserva confirmada na carona selecionada, atualizando o número de passageiros.
- Fluxo principal:
1.  O passageiro solicita a reserva na carona selecionada.
2.  O sistema confirma a reserva do passageiro. 
3.  O sistema atualiza a carona com a reserva do passageiro, atualizando o número de vagas.
4.  O sistema estabelece um link entre o motorista e o passageiro, criando um chat para discussão.

**Consultar Chat (UC06)**

- Ator: Usuário.
- Pré-condição: O usuário está logado e possui caronas em andamento ou reservas confirmadas.
- Pós-condição: O usuário pode se comunicar com os passageiros.
- Fluxo principal:
1.  O usuário acessa a área de chat a partir da barra de menu.
2.  O usuário visualiza todas as caronas reservadas ou publicadas, ordenados por atividade.
3.  O usuário pode enviar e receber mensagens relacionadas a viagem.

**Consultar Caronas (UC07)**

- Ator: Usuário.
- Pré-condição: O usuário está logado no aplicativo.
- Pós-condição: O usuário visualiza a lista de caronas, podendo verificar suas caronas publicadas ou reservas confirmadas, e obter detalhes adicionais sobre elas.
- Fluxo Principal:
1. O usuário acessa a tela de consulta de caronas a partir da barra de menu.
2. O sistema exibe todas as caronas finalizadas ou em andamento associadas ao perfil.
3. O usuário visualiza o histórico de caronas separadas por mês, tendo a opção de consultar as informações completas de cada viagem.

**Cancelar Viagem (UC08)**

- Ator: Usuário.
- Pré-condição: O motorista ou passageiro está logado e possui uma viagem confirmada.
- Pós-condição: A viagem é cancelada com sucesso.
- Fluxo principal:
1. O usuário acessa a tela de lista de caronas a partir da barra de menu.
2. O usuário seleciona a reserva que deseja cancelar.
3. O sistema aceita a solicitação de cancelamento.
4. O sistema atualiza o número de vagas e notifica o responsável via chat.
- Fluxo alternativo:  
2. Caso a data estipulada para a carona não exceda 2 horas, o passageiro não é reembolsado pelo cancelamento da carona, e retorna para o passo 3.

**Avaliar Experiência (UC09)**

- Ator: Usuário.
- Pré-condição: A viagem foi concluída.
- Pós-condição: A avaliação é registrada no sistema e no perfil dos usuários que receberam avaliações.
- **Fluxo principal**:
1. O usuário acessa a lista de caronas a partir da barra de menu.
2. O usuário seleciona a carona finalizada.
3. O usuário insere uma avaliação, entre 1 a 5 estrelas, e feedback (opcional) pertinente a carona.
4. O sistema registra a avaliação e atualiza a média do recipiente com a nota recebida.
- Fluxo alternativo:
1. O usuário envia sua avaliação por meio do pop-up que o aplicativo mostra após a finalização da carona sobre a estimativa de tempo, e retorna ao passo 4.

**Registrar Carro (UC10)**
- Ator: Motorista.
- Pré-condição: O usuário tem uma conta registrada no sistema.
- Pós-condição: O usuário registra seu carro no sistema com sucesso e está elígivel para oferecer caronas.
- **Fluxo principal**:
1. O usuário acessa o perfil a partir da barra de menu.
2. O usuário clica em "Registrar Carro?" abaixo do campo que lista o carro do usuário.
3. O sistema inicia o processo de registro, com telas para informar as características do carro.
4. O sistema registra o carro no banco de dados e atualiza o perfil do usuário.
1. O usuário envia sua avaliação por meio do pop-up que o aplicativo mostra após a finalização da carona sobre a estimativa de tempo, e retorna ao passo 4.
