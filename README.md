<p align="center"> 
      <img src="https://avatars.githubusercontent.com/u/48964967?v=4 width="350px" height="400px"/>
      <img src="https://static.wixstatic.com/media/b62a2d_c2df19675c714549aaa69b335bf37e13~mv2.png/v1/fill/w_188,h_188,al_c,q_85,usm_0.66_1.00_0.01/monitec_2.webp" alt="monitec_2.png" style="width: 94px; height: 94px; object-fit: cover; object-position: 50% 50%;">  
     
                                                                                                                                                 
<p align="center"> 

## 💻 Econect-Server
                 
O econect-server é responsável por por fazer o intermédio entre o econect e a Orizon uma plataforma PBM (Programa de Benefício em Medicamentos) que oferece descontos para medicamentos. O econect faz uma requisição para o econect-server e o mesmo se comunica com a Orizon.
              
## Tópicos

- [Tecnologias](#-Tecnologias)
- [Como executar o Econect-Server](#-Como-executar-o-Econect-Server)
- [Features](#-Features)
- [Contribuidores](#-Contribuidores)
- [Autor](#-Autor)
- [Licença](#-Licença)

## 🛠 Tecnologias

As seguintes ferramentas foram usadas na construção do projeto:
                 
<ul> 
  <li><a href="https://www.java.com">
    <img src="https://img.shields.io/badge/Java%2012.0-ED8B00?style=for-the-badge&logo=java&logoColor=white" alt="java">
  </a></li>
  <li><a href="https://www.mysql.com">
    <img src="https://img.shields.io/badge/MySQL_v1.7-316192?style=for-the-badge&logo=mysql&logoColor=white" alt="mysql">
  </a> </li>                                                                                                                     
  <li><a href="https://spring.io/projects/spring-boot">
    <img src="https://img.shields.io/badge/Spring_Boot_2.1.6-%6DB33F.svg?&style=for-the-badge&logo=spring&logoColor=white" alt="spring-boot">
  </a></li>
  <li><a href="https://site.mockito.org/">
    <img src="https://img.shields.io/badge/Mockito_1.9.5-6DB33F?style=for-the-badge&logo=Mocha&logoColor=white" alt="mockito">
  </a></li>                                                                                                                                          
  <li><a href="https://maven.apache.org/">
    <img src="https://img.shields.io/badge/Apache Maven_3.8.1-E4405F.svg?&style=for-the-badge&logo=apachemaven&logoColor=white" alt="apache-maven">
  </a></li>
    <li><a href="https://projectlombok.org/">
    <img src="https://img.shields.io/badge/Xstream_1.4.11.1-black?style=for-the-badge&logo=xrp&logoColor=Black" alt="Xstream">
  </a></li>                                                                                                                                               
   <li><a href="https://projectlombok.org/">
    <img src="https://img.shields.io/badge/Lombok_1.18.8-F7B500.svg?&style=for-the-badge&logo=&logoColor=white" alt="Lombok">
  </a></li>
   <li><a href="https://sites.google.com/site/gson/gson-user-guide">
    <img src="https://img.shields.io/badge/gson_2.8.5-007CFF?&style=for-the-badge&logo=&logoColor=white" alt="gson">
  </a></li>
   <li><a href="https://www.h2database.com/html/main.html">
    <img src="https://img.shields.io/badge/h2database_1.4.199-43B02A?&style=for-the-badge&logo=white" alt="h2database">
  </a></li>
   <li> <a href="https://www.postgresql.org/">
    <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" alt="postgresql">
  </a> </li>                                                                                                                     
</ul>                            
                                                                                                                                       

## 🚀 Como executar o Econect-Server
                                                                                                                 
### Pré-requisitos

Antes de começar, você vai precisar ter instalado em sua máquina o e-conect, Java JDK 1.8, MySQL 5.7, FTP e SSH, Mavem,
além disto é bom ter um editor para trabalhar com o código como Eclipse ou o Intellij em ambos é necessário instalar e configurar o lombok.


### 🎲 Executando o Econect-Server
                                                                                                                      
## Instruções de Configuração
### Configurações 
#### Base de Dados
Se você deseja configurar database com o docker veja a [documentação aqui](https://github.com/socin-econect/econect-server/wiki/Docker). Para configurar o acesso a base de dados, você deve editar o application.properties como o exemplo abaixo. Para verificar como instalar no cliente [documentação aqui](https://github.com/socin-econect/econect-server/wiki/Instala%C3%A7%C3%A3o-no-cliente).
*Atenção: Só devem ser alterados os pontos delimitados com <>, a alteração de qualquer outro ponto pode gerar impactos negativos para execução da aplicação*
```
# ===============================
#  DATA SOURCE
# ===============================

# Configurações do Datasource da Aplicação

# Url de Conexão
local.datasource.jdbc-url = mysql://<IP-DO-ECONECT-SERVER>:3306/econect-server?useSSL=false

# Usuário e Senha
local.datasource.username = <USUARIO-DO-ECONECT-SERVER>
local.datasource.password = <SENHA-DO-USUARIO

# NÃO ALTERAR: Properties Específicas do Postgres
local.jpa.properties.hibernate.temp.use_jdbc_metadata_defaults = false
local.jpa.database-platform=org.hibernate.dialect.MySQL5Dialect

# NÃO ALTERAR: VALIDAÇÕES
local.datasource.testWhileIdle = true
local.datasource.validationQuery = SELECT 1

# NÃO ALTERAR: DRIVER DE CONEXÃO
local.datasource.driver-class-name = com.mysql.jdbc.Driver

# ===============================
# = JPA DO DATASOURCE
# ===============================

# Se deve mostrar ou na a query do sql.
spring.jpa.show-sql = true

# Tipo de Ação que o Hibernate deve tomar com a database
#spring.jpa.hibernate.ddl-auto = update
#spring.jpa.hibernate.ddl-auto = drop-and-create
local.jpa.hibernate.ddl-auto = validate

# Estratégia de Nomeação de Atributos do Hibernate
local.jpa.hibernate.naming-strategy = org.hibernate.cfg.ImprovedNamingStrategy

# Permite que o Hibernate gere um SQL otimizado para uma versão particular de gerenciamento de banco de dados
local.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQL5Dialect
local.jdbc.lob.non_contextual_creation = true

# ===============================
#  FLYWAY
# ===============================

# Configuração do diretório do flyway
flyway.local.locations.classpath = resources/db/migration/

# ===============================
# = CONCENTRADOR
# ===============================

# Configuração da URL do Concentrador
concentrador.datasource.jdbc-url = jdbc:mysql://<IP-DO-CONCENTRADOR>:<PORTA-DO-CONCENTRADOR>/<DATABASE-DO-CONCENTRADOR>?useSSL=false


# Usuário e senha do concentrador
concentrador.datasource.username = <USUARIO-DO-CONCENTRADOR>
concentrador.datasource.password = <SENHA-DO-CONCENTRADOR>

# NÃO ALTERAR: VALIDAÇÕES
concentrador.datasource.testWhileIdle = true
concentrador.datasource.validation-query = SELECT 1

# NÃO ALTERAR: DRIVER DE CONEXÃO
concentrador.datasource.driver-class-name=com.mysql.jdbc.Driver

# ===============================
# = JPA do CONCENTRADOR
# ===============================

concentrador.jpa.properties.hibernate.temp.use-jdbc-metadata-defaults = false
concentrador.jpa.database-platform = org.hibernate.dialect.MySQL5Dialect
concentrador.jpa.show-sql = true
concentrador.jpa.properties.show-sql = true
concentrador.jpa.hibernate.ddl-auto = validate
concentrador.jpa.hibernate.naming-strategy = org.hibernate.cfg.ImprovedNamingStrategy
concentrador.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQL5Dialect
concentrador.jpa.properties.hibernate.current_session_context_class=org.springframework.orm.hibernate5.SpringSessionContext
concentrador.jdbc.lob.non_contextual_creation = true

#============================== #
# CONFIGURAÇÕES DO JWT          #
#============================== #
app.authorization=PDVMovel
jwt.header=Authorization
# Tempo de Expiração em segundos
jwt.expires_in = 600
# Chave secreta de Autenticação
jwt.secret= pdvsocinmovel
jwt.cookie= AUTH-TOKEN

#============================== #
# CONFIGURAÇÃO DO SERVIDOR      #
#============================== #
# Porta que o Serviço vai subir
server.port = 8091
logging.level.root=INFO
management.security.enabled=false

#============================== #
# CONFIGURAÇÃO DO SERVIDOR      #
#============================== #
socin.produtos.integracao.orizon=false

orizon.api.url.validacao=https://api-homolog.orizonbrasil.com.br/pbm/venda-produtos/0.0.1-rc2/validaBeneficiario
orizon.api.url.planos=https://api-homolog.orizonbrasil.com.br/pbm/venda-produtos/0.0.1-rc2/planos
orizon.api.url.envia.autorizacao=https://api-homolog.orizonbrasil.com.br/pbm/venda-produtos/0.0.1-rc2/autorizacoes
orizon.api.url.devolucao.venda=https://api-homolog.orizonbrasil.com.br/pbm/venda-produtos/0.0.1-rc2/vendas/${orizon.url.patch.devolucao.venda}/itens
orizon.api.url.venda=https://api-homolog.orizonbrasil.com.br/pbm/venda-produtos/0.0.1-rc2/vendas
orizon.imagem.altura=500
orizon.imagem.largura=780
orizon.imagem.tempo.atualizacao=6
orizon.url.patch.devolucao.venda=codigoVenda

orizon.api.url.consulta.autorizacao=https://api-homolog.orizonbrasil.com.br/pbm/venda-produtos/0.0.1-rc2/autorizacoes

# Token para API Orizon
orizon.api.headers.token.nome=X-API-Key
orizon.api.headers.token.valor=f22f78e1-4bc3-434d-b93c-021c1bdb3a8e

socin.econectserver.datasource.mysql = true
socin.econectserver.datasource.postgre = true

# Nome do Header que vai definir a linguagem das mensagens
locale.header.name=Accept-Language
```


## Importar Bibliotecas Locais
- Verifique se o maven está instalado (execute no terminal o comando `mvn -version`)
- Se não estiver instalado execute o seguinte comando `sudo apt install maven`
- Na pasta attach abra o arquivo cfe-api.txt
- Abra o terminal e navegue até a pasta cfe dentro de attach
- Execute os comandos dentro de cfe-api.txt no terminal que está na pasta cfe

## Configurações de IDE
### Intellij
[Baixe o Intellij Aqui](https://www.jetbrains.com/idea/download/#section=linux)

Lista de Plug-ins utilizados:

| Plugin | Descrição |
| ------ | ------ |
|Eclipse Code Formatter|Permite a formação de código no estilo do esclipse, mantendo o padrão de formatação entre Eclipse e Intellij|
|Lombok|Plug-in que permite a suporte a biblioteca do Lombok|
##### Eclipse Code Formatter
- Installe o plug-in eclipse code formatter no Intellij
- Reinicie o Intellij
- Vá em Configurações -> Other Settings -> Eclipse Code Formatter
- Selecione 'Use the Eclipse code formatter'
- Em Eclipse Java Formatter config file selecione em 'Browse' o arquivo de formatação de código, localizado na pasta 'attach' do projeto

##### Lombok
- Veja a documentação para instalação do `Lombok` [aqui](https://github.com/socin-econect/econect-server/wiki/Instala%C3%A7%C3%A3o-Lombok).


#### Configurações do Ambiente
##### Code Style:
- Vá em Settings -> Editor -> Code Style, mude Hard wrap para 100 e Visual guides para 100 colunas.
##### Tabs e Ident:
- Vá em Settings -> Editor -> Code Style -> Java -> Tabs and Idents e defina Tab Size e Ident para 2 e Continuation ident para 4
##### Imports:
- Vá em Settings -> Editor -> Code Style -> Java -> Imports e mude Class count to use import with '*' e Names count to use static import with '*' para 999
##### Java (Última Versão):
- [Baixe o open-jdk 12 aqui](https://download.java.net/java/GA/jdk12/GPL/openjdk-12_linux-x64_bin.tar.gz)
  - Extraia o arquivo para o local desejado (que não a pasta do projeto)
- Vá em File -> Settings -> Build, Execution, Deployment -> Compiler -> Java Compiler
  - Mude o Target bytecode version para 12
  - Dê apply
- Em seguida vá para File -> Project Structure -> Project
  - Mude o project SDK e aponte para o java extraído
  - Mude Project language level para 12
  - Dê apply
- Logo após vá em Run -> Edit Configurations -> Templates -> Application
  - Em JRE aponte selecione SDK do java extraído
  - No canto esquerdo desta janela clique em '+' -> Application
  - Defina um nome para a Application
  - Em Main Class defina a classe principal do projeto
  - Dê Appl

### Eclipse

#### Lombok
- Baixe o jar do Lombok em "https://projectlombok.org/setup/eclipse"
- Execute o Jar como administardor
- Se o Lombok não houver o nome da IDE do eclipse no campo "IDEs" da tela clique em "Specify location..."
- Selecione o Diretorio onde se encontra o Eclipse, após clique em "Select"
- Após clique em "Install/Update"
- Aparecera a mensagem Install successful
- Feche a janela do Lombok

#### GIT

- Abra "Window"-> "Preferences", após abra "Network Connections" -> "SSH2"
- Em "SSH2 Home", selecione o path das chaves ssh, após adicione a chave privada em "Private Keys"
 -Após selecione a aba "Key management", clique em "Load Existing key..."
- Insir a Chave ssh exixtente, após clique me "Applay and close"
- Clique em "File" -> "Import"
- Na tela de Importação clique em "Git" -> "Porjects from Git", logo após clique em "Next"
- Selecione "Clone URI" e logo após clique em "Next"
- Insira os dados do Repositório GIT, logo após clique me "Next"
- Selecione as Branch que devem ser baixadas, após clique em "Next"
- Selecione o diretorio local onde o projeto será baixado, após clique em "Next", o projeto será baixado em um repositorio local
- Clique em "Next" e logo após em "Cancel"
- Clique em "File" -> "Import"
- Na tela de Importação clique em "Maven" -> "Existing Maven Projects", logo após clique em "Next"
- Selecione o diretorio onde se encontra o aquivo pom.xml do projeto, logo após clique em "Finish"



#### Configurações do Ambiente


##### Java (Última Versão):
- Baixe o open-jdk 12 aqui
- Extraia o arquivo para o local desejado (que não a pasta do projeto)
- No Eclipse clique com o botão direito do mouse no projeto
- Clique em "Properties"
- Clique em "Java Build Path"
- Em "Libraries" selecione clique em "JRE System Library", logo após clique em "Edit.."
- Clique em "Intalled JREs..."
- Clique em "ADD"
- Selecione "Standard VM", logo após clique em "Next"
- Clique em "Directory..." e selecione o diretorio onde foi extraido a open-jdk 12
- Clique em "Finish"
- Selecione a jdk 12, após clique em "Apply and Close"
- Verifique se o campo "Workspace Default JRE" está com a jdk 12
- Se não estiver entre os parenteses a jdk 12, baixe novamente a JDK, extraia fora da pasta do projeto e repita o Processo
- Selecione o "Workspace Default JRE", após clique em "Finsh"
- Clique em "Apply and Close"


### Configurar base Docker
- Copie o diretório BaseAmbiente dentro de um didetorio local fora do projeto
- No terminal vá até o diretório BaseAmbiente que foi copiado fora do projeto
- Use o seguinte comando "docker-compose -f teste.yml up -d"
                                                                                               
### 🎁 Geração do executavel de produção
                                                                                                                 
- Fazer o build usando o mvn clean install
- O artefato gerado se encontra dentro do econect-server no diretório target
                                                                                                        
## 💫 Features

O conteúdo referente as features do Econect-Server se encontra no local  do link abaixo.

https://socincompany.atlassian.net/wiki/spaces/E

## 😃 Autor

<p align="center"> 
   <a href="https://www.socin.com.br/">
      <img style="border-radius: 50%;" src="https://avatars.githubusercontent.com/u/48964967?v=4" width="100px;" alt="socin"/>
   </a>
</p>
<p align="center"> 
      <sub><b>Socin Sistemas</b></sub></a> <a href="https://www.socin.com.br/" title="Socin">🚀</a>
<p align="center"> 
 Feito com ❤️  pela equipe de desenvolvimento Socin Sistemas!
</p>
<p align="center"> 
 <a href="https://www.facebook.com/socinsistemas"><img src="https://img.shields.io/badge/Facebook-1877F2?style=for-the-badge&logo=facebook&logoColor=white" alt="Facebook"></a>
<a href="https://www.linkedin.com/company/socinsistemas/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="Linkedin"></a>
<a href="https://www.instagram.com/socinsistemas/?hl=pt-br"><img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white" alt="Instagram"></a> 
</p>

## 📝 Licença

🚧 Em construção... 🚧

