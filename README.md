# Relatório Banco de Dados


Trabalho final da disciplina "Banco de Dados" - Bacharelado em Inteligência Artificial 2024.1 - UFG

Bancos de dados como ferramenta para a análise de desempenho de atletas

Alunos: Matheus Franco Medeiros e Murilo Alvares Silva

## Sobre o Tema

Tema: Análise de Desempenho no Mercado de Transferências do Futebol

Para o projeto final, o objetivo era desenvolver um sistema de banco de dados, de tema livre, mas que atendesse aos requisitos de nossa ideia e no qual pudéssemos realizar análises e consultas dos dados escolhidos.

Sabemos que a área da Inteligência Artificial é extremamente ampla e com infinitas possibilidades, e por isso, decidimos realizar o nosso projeto final em uma área que gostamos e temos muita afinidade: o futebol

Assim, tomamos como objetivo a criação de um sistema de banco de dados que permita analisar o desempenho de jogadores de futebol. O sistema deveria ser capaz de responder a consultas específicas e fornecer uma interface interativa para filtragem e comparação de dados dos jogadores, auxiliando na tomada de decisões sobre contratações.

## Dados Utilizados

Para dar vida ao nosso projeto, utilizamos o dataset “2022-2023 Football Player Stats”, que conta com 116 estatísticas diferentes para mais de 2000 jogadores das principais ligas europeias (Premier League - ING, La Liga - ESP, Bundesliga - ALE, Serie A - ITA, Ligue 1 - FRA)  durante a temporada de 2022-2023. 

## Ferramentas Utilizadas

Para criar o Banco de Dados. Utilizamos duas ferramentas principais: um Banco de Dados Relacional por meio de uma instância MySQL, e um Data Warehouse por meio do BigQuery, ambos disponibilizados pelo GCP (Google Cloud Platform). Para a dashboard interativa de visualização de dados, utilizamos a plataforma PowerBI. 
#### MySQL:
Utilizamos o MySQL para armazenar e organizar os dados dos jogadores e suas estatísticas em tabelas relacionais. 
#### BigQuery:
Migramos os dados do MySQL para o BigQuery, a fim de executar consultas de maior complexidade, além de integrar esses dados para a plataforma PowerBI
#### PowerBI:
Utilizamos a plataforma para criar uma dashboard interativa, em que o usuário possa filtrar, consultar e analisar todos os dados.

## Modelagem e Implementação do Banco de Dados

### Banco de Dados Relacional (MySQL):

Foram criadas 2 tabelas: 
#### Jogadores: tabela contendo as informações básicas e gerais sobre os jogadores.
#### Estatísticas: tabela contendo as estatísticas detalhadas dos jogadores.

#### Códigos de criação das tabelas no Cloud SQL Studio:

##### Tabela “Jogadores”: 
    CREATE TABLE Jogadores (
        Rk INT PRIMARY KEY,
        Player VARCHAR(100),
        Nation VARCHAR(50),
        Pos VARCHAR(50),
        Squad VARCHAR(100),
        Comp VARCHAR(50),
        Age INT,
        Born INT,
        MP INT,
        Starts INT
    );

##### Tabela “Estatisticas”:
    CREATE TABLE Estatisticas (
      Rk INT,
      MP INT,
      Starts INT,
      Min INT,
      Ninetys FLOAT,
      Goals INT,
      Shots INT,
      SoT INT,
      SoT_perc FLOAT,
      G_Sh FLOAT,
      G_SoT FLOAT,
      ShoDist FLOAT,
      ShoFK INT,
      ShoPK INT,
      PKatt INT,
      PasTotCmp INT,
      PasTotAtt INT,
      PasTotCmp_perc FLOAT,
      PasTotDist INT,
      PasTotPrgDist INT,
      PasShoCmp INT,
      PasShoAtt INT,
      PasShoCmp_perc FLOAT,
      PasMedCmp INT,
      PasMedAtt INT,
      PasMedCmp_perc FLOAT,
      PasLonCmp INT,
      PasLonAtt INT,
      PasLonCmp_perc FLOAT,
      Assists INT,
      PasAss INT,
      Pas3rd INT,
      PPA INT,
      CrsPA INT,
      PasProg INT,
      PasAtt INT,
      PasLive INT,
      PasDead INT,
      PasFK INT,
      TB INT,
      Sw INT,
      PasCrs INT,
      TI INT,
      CK INT,
      CkIn INT,
      CkOut INT,
      CkStr INT,
      PasCmp INT,
      PasOff INT,
      PasBlocks INT,
      SCA INT,
      ScaPassLive INT,
      ScaPassDead INT,
      ScaDrib INT,
      ScaSh INT,
      ScaFld INT,
      ScaDef INT,
      GCA INT,
      GcaPassLive INT,
      GcaPassDead INT,
      GcaDrib INT,
      GcaSh INT,
      GcaFld INT,
      GcaDef INT,
      Tkl INT,
      TklWon INT,
      TklDef3rd INT,
      TklMid3rd INT,
      TklAtt3rd INT,
      TklDri INT,
      TklDriAtt INT,
      TklDri_perc FLOAT,
      TklDriPast INT,
      Blocks INT,
      BlkSh INT,
      BlkPass INT,
      Interceptions INT,
      Tkl_Int INT,
      Clr INT,
      Err INT,
      Touches INT,
      TouDefPen INT,
      TouDef3rd INT,
      TouMid3rd INT,
      TouAtt3rd INT,
      TouAttPen INT,
      TouLive INT,
      ToAtt INT,
      ToSuc INT,
      ToSuc_perc FLOAT,
      ToTkl INT,
      ToTkl_perc FLOAT,
      Carries INT,
      CarTotDist INT,
      CarPrgDist INT,
      CarProg INT,
      Car3rd INT,
      CPA INT,
      CarMis INT,
      CarDis INT,
      Rec INT,
      RecProg INT,
      CrdY INT,
      CrdR INT,
      SecondCrdY INT,
      Fls INT,
      Fld INT,
      Off INT,
      Crs INT,
      TklW INT,
      PKwon INT,
      PKcon INT,
      OG INT,
      Recov INT,
      AerWon INT,
      AerLost INT,
      AerWon_perc FLOAT,
      FOREIGN KEY (Rk) REFERENCES Jogadores(Rk)
    );

### Data Warehouse (BigQuery):

Importamos os dados do banco de dados relacional por Google Cloud Storage.

### PowerBI:

Importamos os dados do BigQuery para o PowerBI por meio de uma ferramenta da plataforma que permite realizar essa conexão. Criamos o relacionamento entre as tabelas para garantir que a chave primária (Rk) esteja funcionando. Depois disso, criamos tabelas de parâmetros, inserindo as colunas das tabelas, e as estatísticas se conectam ao jogador

#### Acesso ao PowerBI:
https://ufgbr-my.sharepoint.com/:u:/g/personal/murilo_silva_discente_ufg_br/EWeB95wGo2RCmADZaVL9V5cB8fnUJwAZjq-7o9eYOkAlCg?e=A4pAsL

## Consultas implementadas:

Realizamos algumas consultas nos dois bancos de dados:
https://docs.google.com/document/d/1uS8zETPNaOyaL9vKZUGZcbhU5JoOAQ4CrlSTPWjzqq4/edit

## Objetivos futuros:
Alguns dos objetivos e ações futuras planejadas para o projeto são:
- Adição de valor de mercado
- Comparação entre jogadores
- Inclusão de dados de mais temporadas
- Análise da evolução do desempenho dos jogadores
- Inclusão de novas ligas e, consequentemente, novos jogadores
- Implementação de análises preditivas para possíveis contratações

## Conclusão

O projeto foi extremamente gratificante de se realizar, principalmente pelo seu tema, o que nos motivou a trabalhar nele incansavelmente e continuar trabalhando mesmo após sua entrega. Acreditamos que criamos uma ótima ferramenta que, além de permitir que apliquemos conhecimentos e técnicas aprendidas ao longo da disciplina, nos fez criar um carinho e atenção especial para a área de Banco de Dados. Agradecemos o professor Sávio Teles pela oportunidade e pelos ensinamentos em sala de aula, que temos certeza que vai nos ajudar em nossa formação profissional.


