# Monitoramento-java

# Justificativa:

O projeto “ingresse monitora” nasceu com o objetivo e proposito de monitorar hardwares a fim de facilitar o trabalho de profissionais que diretamente e indiretamente trabalham com a tecnologia de Sinalética digital em cinemas. Acretido que com serviços especializados de monitoria, seja para médias ou grandes empresas da área, podem aumentar a durabilidade dos hardware's, economizar recursos (caso os mesmos estejam desalinhados),reduzindo queda de performance e gargalos, diminuindo assim o tempo em filas de espera para a compra de ingressos. Diminuição com gastos frequentes com manutenção e recolocação de hardwares, Diminuição de tempo para compra de ingressos por performance de hardwares, monitoria constante de como seu hardware está atuando, redução de clientes desistentes por uma alta demora em filas.

 # Banco de dados na azure. 
 # Testado para rodar em vm ec2 AWS (versão 3 vm)
 
# Token foi fixado para o uso:
1234

# Login:

email:
Jose@gmail.com

senha:
teste

Após o login, para iniciar o monitoramento é necessário adicionar totem e confirmar seu usuário.

# Script banco de dados para rodar localmente:

CREATE DATABASE ingresse;

USE ingresse;
CREATE TABLE filial(
	idFilial INT PRIMARY KEY AUTO_INCREMENT,
	email_corporativo varchar(45),
	senha varchar(45),
	cnpj varchar(45)
);

create table lancamento_futuro(
	idLancamento INT PRIMARY KEY AUTO_INCREMENT,
	nomeFilme varchar(45),
	dataFilme char(10),
	dias_para_lancamento int
);

create table logs(
	idLog INT PRIMARY KEY AUTO_INCREMENT,
	fkTotem int,
    FOREIGN KEY (fkTotem) REFERENCES totem(idTotem),
	pctg_processador int,
	pctg_memoria_uso int,
	pctg_disco_uso int,
	qtd_servicos int,
	temp float,
	data_hora dateTime
);

create table ocorrencias(
	idOcorrencia INT PRIMARY KEY AUTO_INCREMENT,
	fkLog int,
    fkUsuario int,
    FOREIGN KEY (fkLog) REFERENCES logs(idTotem),
    FOREIGN KEY (fkUsuario) REFERENCES usuario(idUsuario),
	fkUsuario int,
	descricao_erro varchar(45),
	descricao_concerto varchar(45),
	data_inicio date,
	data_final date
);

create table totem(
	idTotem INT PRIMARY KEY AUTO_INCREMENT,
	fkFilial int,
    FOREIGN KEY (fkFilial) REFERENCES filial(idFilial),
	ram_total float,
	espaco_disco float,
	processador varchar(45),
	data_compra date,
	id_processador varchar(45),
	serial_disco varchar(45),
	hostname varchar(45)
);

create table usuario(
	idUsuario INT PRIMARY KEY AUTO_INCREMENT,
	nome varchar(45),
	email_usuario varchar(45),
	tipo_acesso varchar(45),
	fkFilial int,
    FOREIGN KEY (fkFilial) REFERENCES filial(idFilial),
	senha varchar(45)
);

# Selenium-Java

# Como usar?

Para a utilização você deve atualizar o chrome driver para um compativél.
Em seu chrome, lá em opções (personalizar e controlar chrome) -> clique em ajuda -> clique em "sobre o google chrome".
Irá pararecer a versão de seu chrome.

vá até o site:
https://chromedriver.chromium.org/downloads

E procure pela sua versão e baixe.
Dentro da pasta Selenium procure o arquivo chromedriver e o substitua por um compatível em sua máquina.
