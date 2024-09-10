# Zipps

O Zipps é um aplicativo de carona sem fins lucrativos que busca conectar passageiros e motoristas de maneira eficiente e segura. O objetivo é oferecer um meio para o compartilhamento de viagens, facilitar a procura por pessoas com trajetos coincidentes e pontos de partida próximos da sua localização atual, permitindo a divisão de custos no transporte.

Dentre as suas principais funcionalidades, os usuários podem consultar o histórico de caronas e avaliações entre os envolvidos. Ao manifestar interesse em uma publicação, o passageiro ganha acesso ao chat integrado para o esclarecimento de dúvidas e informações adicionais para com o motorista; após a finalização da carona, o sistema de avaliação permite que motoristas e passageiros se avaliem mutuamente. Além disso, o Zipps oferece filtros que possibilitam escolher caronas específicas, como viagens excluvisamente para mulheres ou outras preferências pessoais.

O cliente é cobrado uma taxa para a manutenção de custos operacionais no momento da reserva.

## Requisitos da primeira versão (MVP)

- Usuários podem se cadastrar na plataforma com informações básicas, como nome, e-mail e senha.
- Usuários cadastrados no sistema passarão por um processo de verificação via e-mail.
- Passageiros podem pesquisar caronas com base em critérios como avaliações, preço, data etc.
- O motorista publica a carona, descrevendo o trajeto percorrido até o destino no mapa, o número de vagas e o custo por passageiro.
- Após o processo de geolocalização, o passageiro pode manifestar o seu interesse na carona por meio do ato de reserva, pagando uma taxa pré-definida para o aplicativo.
- Após a reserva, os envolvidos podem se comunicar via chat para discutir outras informações.
- Tanto o motorista quanto o passageiro possuem o direito de cancelar sua reserva; no segundo o caso, o custo de reserva é reembolsado pelo aplicativo.
- Após a conclusão da carona, tanto o passageiro e o motorista podem avaliar a experiência de forma generalizada (1 a 5 estrelas), além de terem a opção de oferecer comentários quanto a cordialidade ou outros atributos.
- Caronas finalizadas e avaliações serão refletidas no perfil do usuário para referência futura.

## Observações

- Manutenção das caronas e filtros associados.
- Manutenção de usuários: nome, CPF, telefone, e-mail, sexo e data de nascimento.
- Compatibilidade com dispositivos móveis Android, responsivo para larguras de tela com 350px ou superior.
- Filtro:

## Casos de Uso

### Diagrama

![Casos de Uso](docs/usecase/usecases.png)

### Descrição dos Casos de Uso

**Registrar Perfil (UC01)**

- Ator: Novo usuário.
- Pré-condição: O usuário acessa o aplicativo sem ter um perfil registrado.
- Pós-condição: O usuário tem um perfil ativo no sistema.
- Fluxo principal:
1.  O usuário acessa a tela de cadastro.
2.  O usuário preenche o e-mail para o processo inicial de verificação.
3.  O sistema envia um código de verificação para o e-mail informado.
4.  O sistema valida o código e procede para a tela de dados pessoais.
5.  O usuário fornece informações relevantes para o seu cadastro, incluindo nome, senha, data de nascimento. placa e modelo de carro (opcional), foto de perfil (opcional), documento de identificação (CPF, RG ou CNH) e minibiografia (opcional).
6.  O sistema valida as informações e cria um perfil para o usuário.
- Fluxo alternativo:
2. O usuário passa o processo de verificação por dados fornecidos pela API do Facebook, e retorna ao passo 3 para as informações restantes.
- Fluxo de exceção:
3. O sistema não permite o cadastro de um usuário que tenha o documento de identificação registrado no banco de dados.

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
1.  O motorista acessa a tela direcionada para oferecer caronas a partir do menu principal.
2.  O motorista insere as informações sobre a carona, incluindo data, horário, local de partida, destino, trajeto e filtros (opcional).
3.  O motorista define o número de vagas disponíveis e o valor estimado por pessoa.
4.  O sistema valida os dados inseridos.
5.  A carona é publicada no sistema.

**Procurar Carona (UC04)**

- Ator: Passageiro.
- Pré-condição: O passageiro está logado no aplicativo.
- Pós-condição: A carona é exibida de acordo com o requisitos especificados.
- Fluxo principal:
1.  O passageiro acessa a tela de buscar caronas a partir do menu principal.
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
1.  O usuário acessa a área de chat a partir do menu principal.
2.  O usuário visualiza todas as caronas reservadas ou publicadas, ordenados por atividade.
3.  O usuário pode enviar e receber mensagens relacionadas a viagem.

**Consultar Caronas (UC07)**

- Ator: Usuário.
- Pré-condição: O usuário está logado no aplicativo.
- Pós-condição: O usuário visualiza a lista de caronas, podendo verificar suas caronas publicadas ou reservas confirmadas, e obter detalhes adicionais sobre elas.
- Fluxo Principal:
1. O usuário acessa a tela de consulta de caronas a partir do menu principal.
2. O sistema exibe todas as caronas finalizadas ou em andamento associadas ao perfil.
3. O usuário visualiza o histórico de caronas separadas por mês, tendo a opção de consultar as informações completas de cada viagem.

**Cancelar Viagem (UC08)**

- Ator: Usuário.
- Pré-condição: O motorista ou passageiro está logado e possui uma viagem confirmada.
- Pós-condição: A viagem é cancelada com sucesso.
- Fluxo principal:
1. O usuário acessa a tela de lista de caronas a partir do menu principal.
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
1. O usuário acessa a lista de caronas a partir do menu principal.
2. O usuário seleciona a carona finalizada.
3. O usuário insere uma avaliação, entre 1 a 5 estrelas, e feedback (opcional) pertinente a carona.
4. O sistema registra a avaliação e atualiza a média do recipiente com a nota recebida.
- Fluxo alternativo:
1. O usuário envia sua avaliação por meio do pop-up que o aplicativo mostra após a finalização da carona sobre a estimativa de tempo, e retorna ao passo 4.
