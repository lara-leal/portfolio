# Lara Oliveira Leal
## Introdução
<img align='right' src="https://media.discordapp.net/attachments/888964389368131629/1175834034404872253/fotor-2023111913227.png?ex=656cabc7&is=655a36c7&hm=5b0e72e0874ba809bb134b2ba1a0893a520970e815da7124df84da8dc042a61b&=&width=565&height=565" width="200" height="200"/>

<p style="text-align: justify;"> 
Olá! Meu nome é Lara Leal, sou de São José dos Campos - SP, e tenho 22 anos. Desde criança sempre fui muito curiosa, algo que me acompanha até hoje. No Ensino Médio, cursei Técnico em Química no CEPHAS (Centro Educacional Hélio Augusto de Souza) movida pela minha curiosidade. Terminei o técnico e, logo em seguida, veio o início da pandemia. Foi nesse momento que tomei conhecimento do Vestibular da FATEC e decidi prestá-lo para explorar mais sobre o mundo da tecnologia. Visto que seria online naquele momento, achei que seria uma ótima oportunidade para adquirir conhecimento durante essa fase desafiadora.

Minha primeira experiência com programação aconteceu na faculdade, onde aprendi Python nas aulas de LP 1. Atualmente, meu foco principal é o Back-End e Ciência de Dados. Tenho mais familiaridade com as linguagens Python e Java, o que me permite desenvolver web services, utilizar padrões de projetos e criar arquiteturas. Também tenho conhecimento em frameworks amplamente utilizados no mercado, como Quarkus, SpringBoot e Flask.

Atualmente, trabalho como Analista de Sistemas na Farma Conde. Minhas principais responsabilidades envolvem levantamento de requisitos, arquitetura e modelagem de banco de dados, além do desenvolvimento de automações de processos. </p>

<h1 align="center"> Projeto 1: 1º Semestre de 2021 </h1>

<div align="center"> Projeto Integrador - 1° Semestre | Fatec Prof. Jessen Vidal - 2021 | Cliente parceiro: Professor Fabiano Sabha </div>


## Visão do Projeto

Com o propósito de trazer para os estudantes em geral uma forma mais centralizada e organizada de cuidar da vida acadêmica e se manter atualizado em suas atividades, criamos a Athena- Assistente Pessoal de Estudos. O seu diferencial é reunir diversas ferramentas úteis em um único lugar.

## Tecnologias adotadas na solução

### Python

Python é uma linguagem de programação popular que foi criada na década de 1990 por Guido van Rossum. É conhecida por sua sintaxe simples e fácil de ler, o que a torna uma ótima escolha para iniciantes em programação. Python é usado em muitas áreas diferentes, incluindo ciência de dados, desenvolvimento web, automação de tarefas, inteligência artificial e muito mais. É uma linguagem interpretada, o que significa que o código é executado linha por linha sem a necessidade de compilação. Além disso, Python é uma linguagem de programação de alto nível, o que significa que é mais próxima da linguagem humana do que de uma linguagem de máquina, tornando a programação em Python mais intuitiva e acessível para muitas pessoas.

### **SQLite**

SQLite é um sistema de gerenciamento de banco de dados relacional que é fácil de usar e não requer uma configuração complexa. Ele é conhecido por sua portabilidade, confiabilidade e eficiência, e é usado em muitas aplicações em dispositivos móveis e de desktop. O SQLite é incorporado diretamente em muitos aplicativos e sistemas operacionais, o que significa que não é necessário instalar nenhum software adicional para usar bancos de dados SQLite. Ele é executado em um único arquivo, tornando-o ideal para pequenos projetos ou para aplicações que não requerem uma grande quantidade de dados. Além disso, o SQLite é compatível com SQL, o que significa que você pode usar as mesmas consultas SQL que você usaria em outros sistemas de gerenciamento de banco de dados relacionais, como o MySQL ou o PostgreSQL.

### SpeechRecognition

A biblioteca SpeechRecognition é uma ferramenta de reconhecimento de fala para a linguagem de programação Python. Com ela, é possível capturar e converter áudio em texto, tornando a interação com aplicativos mais intuitiva e acessível.

Com essa biblioteca, é possível desenvolver aplicativos que utilizam a fala como entrada de dados, como assistentes virtuais, sistemas de controle de voz, transcrições de áudio, entre outros. A biblioteca SpeechRecognition simplifica muito a tarefa de processar áudio em texto, permitindo que desenvolvedores implementem recursos de reconhecimento de fala em suas aplicações de forma rápida e fácil.

### Interface com o usuário

Esse projeto não possui interface gráfica pois foi baseado 100% em comandos de voz. 

### BackEnd

Python é uma linguagem de programação de alto nível e de código aberto amplamente utilizada em desenvolvimento de software, análise de dados, IA e automação de tarefas. Possui sintaxe simples e legível, ampla biblioteca padrão e é uma escolha popular para iniciantes e profissionais.

## Contribuições pessoais

Minhas contribuições pessoais neste projeto foram principalmente na parte de definição do escopo do produto e divisão das tarefas atuando como Scrum Master, também com desenvolvimento do backend e criação do banco de dados.

A ferramenta utilizada para desenvolver o banco de dados nesse primeiro projeto foi o SQLite por se tratar de uma ferramenta simples e menos complexa. 

Fui a responsável pelo desenvolvimento das seguintes funções da nossa assistente de voz:

</details>

<details>
<summary> Cálculo de média </summary>

Através de comandos de voz, a aplicação pergunta ao usuário a matéria desejada e realiza uma consulta SQL. Em seguida, calcula a média com base em valores específicos das colunas do resultado da consulta e informa o resultado ao usuário por voz.

```` if there_exists(["calcule a média", "mostrar média", "visualizar média"]):
        speak("Para qual matéria gostaria de calcular sua média ")
        vsqlin = " SELECT * FROM GERAL"
        res = consulta(vcon, vsqlin)
        materias_media = []
        for result in res:
            materias_media.append(result[1])
        voice = record_audio().strip().lower()
        index_media = materias_media.index(voice)
        if voice in materias_media:
            if res[index_media][4] != -1 or res[index_media][5] != -1 or res[index_media][6] != \
                    -1 or res[index_media][7] != -1:
                media = (res[index_media][4] + res[index_media][5] + res[index_media][6] + res[index_media][7]) / 4
                speak(f'a média para a matéria "{voice}" é: {media}')
            else:
                speak('Não foi possível calcular sua média, tente cadastrar todas suas notas e tente novamente!')
        else:
            speak('Não encontrei essa matéria no meu banco de dados, para criar uma nova matéria basta dizer '
                  '"Cadastrar Matéria" ')
            return record_audio()
````
</details>

<details>
<summary> Controle de faltas </summary>

A lógica implementada foi fazer a aplicação verificar se o usuário quer registrar, adicionar ou remover faltas. Solicita a matéria e a quantidade de faltas desejada, realizando as operações necessárias no banco de dados. 

````
if there_exists(["registrar faltas", "anotar faltas", "adicionar faltas", "cadastrar faltas",
                     "cadastrar falta", "registrar falta", "anotar falta"]):
        try:
            vsqlin = " SELECT * FROM GERAL"
            res = consulta(vcon, vsqlin)
            materias_faltas = []
            for result in res:
                materias_faltas.append(result[1])
            speak('Para qual matéria gostaria de registrar suas faltas?')
            fal = record_audio().strip().lower().split()
            if fal[0] in materias_faltas:
                index = materias_faltas.index(fal[0])
                if res[index][8] == -1:
                    speak(f'quantas faltas gostaria de registrar para a matéria: "{fal[0]}"')
                    int_faltas = record_audio().strip()
                    update("FALTAS", int(int_faltas), res[index][8])
                else:
                    speak(' Voce deseja "somar" ou "remover" suas faltas ?')
                    resp = record_audio().strip().lower()
                    if resp == "somar":
                        speak('Para qual matéria gostaria de adicionar suas faltas?')
                        fal = record_audio().strip().lower().split()
                        if fal[0] in materias_faltas:
                            speak(f'Quantas faltas gostaria de adicionar para a matéria: "{fal[0]}"')
                            int_faltas = record_audio().strip()
                            index = materias_faltas.index(fal[0])
                            update("FALTAS", int(int_faltas) + res[index][8], res[index][8])
                        else:
                            speak('Não encontrei essa matéria no meu banco de dados, para criar uma nova matéria '
                                  'basta dizer "Cadastrar Matéria" ')
                    if resp == "remover":
                        speak('Para qual matéria gostaria de remover suas faltas ?')
                        fal = record_audio().strip().lower().split()
                        if fal[0] in materias_faltas:
                            speak(f'Quantas faltas gostaria de remover para a matéria: "{fal[0]}"')
                            int_faltas = record_audio().strip()
                            index = materias_faltas.index(fal[0])
                            update("FALTAS", res[index][8] - int(int_faltas), res[index][8])
````


</details>

### Aprendizados Efetivos HS

Neste projeto pude começar a desenvolver minhas habilidades em linguagens de programação do zero. Aprendendo o que é uma função, entender como funciona a linguagem de programação Python e aplicar lógica de programação. 
    
Tendo também a oportunidade de conhecer metodologias ágeis e atuar como Scrum Master.  
    
- Usar lógica de programação para desenvolver cálculos;
- Aprender como programar;
- Aprender como usar uma IDE;
- Aprender como fazer uma modelagem de banco de dados;
- Aprender como usar bibliotecas;
- Utilizar a biblioteca SpeechRecognition;




<h1 align="center"> Projeto 2: 2º Semestre de 2021 </h1>

<div align="center"> Projeto Integrador - 2° Semestre | Fatec Prof. Jessen Vidal - 2023 | Cliente parceiro: Necto Systems </div>

## Visão do Projeto

Desenvolver um software integrado que monitore e apresente métricas referentes ao uso e a saúde do SGBD em tempo real. Além de oferecer um pós gerenciamento de múltiplos BD’s no servidor, como diferencial.

## Tecnologias adotadas na solução

### Java

Java é uma linguagem de programação orientada a objetos que foi criada na década de 1990 pela Sun Microsystems, e atualmente é propriedade da Oracle Corporation. É uma das linguagens de programação mais populares do mundo, usada em uma ampla variedade de aplicativos e sistemas, desde desenvolvimento de aplicativos desktop e web até jogos e dispositivos móveis.

### PostgreSQL

PostgreSQL é um sistema de gerenciamento de banco de dados relacional (SGBDR) de código aberto e altamente confiável. Ele é amplamente conhecido por sua robustez, escalabilidade e recursos avançados que o tornam uma escolha popular para uma variedade de aplicações.

Uma das principais características do PostgreSQL é sua capacidade de suportar grandes volumes de dados e cargas de trabalho intensivas.

### SQLite

O SQLite é um banco de dados embutido, rápido e leve que não requer um servidor separado para funcionar. Diferente dos bancos de dados tradicionais, o SQLite armazena todo o banco de dados em um único arquivo, tornando-o fácil de implantar e usar em aplicativos.

O SQLite é amplamente utilizado em aplicativos móveis, desktop e em outras aplicações que precisam de um banco de dados local. Ele é escrito em linguagem C e disponibiliza uma interface simples através de comandos SQL para executar operações de banco de dados, como criação de tabelas, inserção, atualização, exclusão e consulta de dados.

### Interface com o usuário

Esse projeto não possui interface gráfica pois tinha como objetivo ser executado apenas no terminal.

## Contribuições pessoais

Minhas contribuições  neste projeto foram principalmente na parte extração e implementação de métricas sobre a saúde do banco de dados. 

Para extrair as métricas utilizei como referencia um artigo **“Extraindo Metadados de SGBDs”** da **PONTIFÍCIA UNIVERSIDADE CATÓLICA DO RIO DE JANEIRO.** Esse artigo me ajudou a identificar as tabelas e schemas que extraiam as métricas que definimos como escopo para nosso projeto. Como por exemplo:

- pg_stat_statements
- pg_stat_database
- information_schema.tables

A maior parte do esforço desse semestre foi encontrar documentação que nos instruísse como extrair as métricas sobre a saúde do SGBD e como elaborar as querys. 

Como estávamos no 2º semestre, ainda não tínhamos experiência efetiva em elaborar querys que fossem bem estruturadas. Então a maior parte do desenvolvimento foi constituído por isso. 

Também utilizamos Java como linguagem de programação da aplicação, que também foi um desafio visto que durante esse projeto foi a primeira vez que tivemos contato com a linguagem. 

Desenvolvi a conexão do banco de dados utilizando o SQLite, com nosso “historico.db”. como o trecho de código a seguir: 

```
public static void main(String[] args) throws SQLException, IOException  {
mainClass  con = new mainClass ("postgres");
	String SqLite = "jdbc:sqlite:historico.db";
	try {
		Class.forName("org.sqlite.JDBC");
	} catch (ClassNotFoundException e2) {
		// TODO Auto-generated catch block
		e2.printStackTrace();
	}
	Connection connSqlite = DriverManager.getConnection(SqLite);
	 Statement statement = connSqlite.createStatement();
	 statement.setQueryTimeout(30);
}
```

O banco que usamos para realizar o monitoramento foi um banco PostgreSQL.

### Aprendizados Efetivos HS

- Aprender a programar em Java;
- Aprender a elaborar queries em SQL;
- Aprender a usar o postgreSQL;
- Aprender a lidar diretamente com o cliente;



<h1 align="center"> Projeto 3: 1º Semestre de 2022 </h1>

<div align="center"> Projeto Integrador - 3° Semestre | Fatec Prof. Jessen Vidal - 2023 | Cliente parceiro: Midall </div>

## Visão do Projeto

"Temos um problema para criação de **promoções em um Ecommerce**. Precisamos de uma solução inteligente onde, as mecânicas das promoções sejam feitas de forma flexível e de rápida atualização no sistema." - MidAll.

A ideia era criar um motor de regras com uma interface onde as regras das promoções possam ser cadastradas e aplicadas no momento que os itens forem para o carrinho de compras.

## Tecnologias adotadas na solução

### Interface com o usuário

**JavaScript** é uma linguagem de programação de alto nível criada, a princípio, para ser executada em navegadores e manipular comportamentos de páginas web.

Segundo a **Mozilla Foundation**, atual nome da antiga **Netscape Communications Corporations**, empresa responsável pela criação do JS, "*JavaScript é uma linguagem de programação, leve, interpretada, orientada a objetos, baseada em protótipos e em first-class functions (funções de primeira classe), mais conhecida como a linguagem de script da Internet.*"

O **jQuery** trata-se de uma biblioteca JavaScript que pode ser adicionada aos projetos de codificação. Basicamente, o jQuery permite que os desenvolvedores web conectem recursos de rotina de JavaScript em uma página da web para que possam passar mais tempo focando em recursos complicados que são exclusivos do site.

### BackEnd

Java é uma linguagem de programação e um ambiente computacional criado pela Sun Microsystems na década de 90, sendo posteriormente adquirido pela Oracle.

Devido a possibilidade de escrever o código apenas uma vez e rodá-lo em diferentes dispositivos, a tecnologia logo se tornou popular, passando a ser implementada em praticamente qualquer lugar, desde sites e computadores até datacenters, celulares, calculadoras, videogames, etc.

Como linguagem de programação, o código Java é baseado em classes e orientado a objetos, com foco em segurança, portabilidade e alta performance.

## Contribuições pessoais

Minhas contribuições pessoais neste projeto foram principalmente na parte do desenvolvimento do backend e na modelagem e criação do banco de dados. 

Para a modelagem do banco utilizei a ferramenta brModelo para criar as entidades, atributos e definir seus relacionamentos. Onde foi definido que: Um produto pode fazer parte de vários carrinhos e um carrinho precisa receber pelo menos um ou vários produtos. Uma promoção pertence a apenas um produto, já um produto pode fazer parte de diversas promoções, ou seja, uma promoção não pode existir sem um produto.
<details>
<summary>Modelagem</summary>
<img src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F718ca954-37be-47dd-8e1d-46bb63ffad25%2FUntitled.png?table=block&id=36cc1090-d8f6-4f7e-872e-83d9dad12b32&spaceId=70f68203-9aa8-48f2-9c19-ba66c1511816&width=2000&userId=607976c1-73b5-4be3-8f82-323ac698a9fd&cache=v2" width="500" height="400"/>
</details>  

Fui a responsável pelo desenvolvimento do projeto utilizando programação OO e a definição da utilização do Arquitetura do projeto: Models, Services, Repositories e Resources. Contribui também no desenvolvimento da lógica de verificar as promoções dos produtos no carrinho de compras. 
<details>
<summary> Packages </summary>
<img src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F7de10511-ef9a-4955-9d4e-e3b7d744e72a%2Fpatterns.png?table=block&id=566df640-3624-4898-889d-f0e018fb6683&spaceId=70f68203-9aa8-48f2-9c19-ba66c1511816&width=2000&userId=607976c1-73b5-4be3-8f82-323ac698a9fd&cache=v2" width="500" height="400"/>
</details>

Durante o desenvolvimento se tornou necessário a refatoração do código para adicionar Dto's e injeções de dependência onde contribui efetivamente, o que ajudou a deixar o código mais desacoplado e facilitar na hora de ampliar a aplicação.
<details>
<summary> DTO </summary>
<img src="https://user-images.githubusercontent.com/80706297/204786984-af27a088-7eeb-446e-b6cd-25374a1425c0.png" width="500" height="300"/>
</details>  

<details>
<summary> Injeção de dependências </summary>
<img src="https://user-images.githubusercontent.com/80706297/204789559-e565bf85-1519-496f-b81c-1f239a0f0f45.png" width="600" height="400"/>
</details>  


A linguagem de programação JavaScript foi utilizada sem nenhuma framework para o desenvolvimento do front-End, ou seja, a  interface com o usuário via  aplicação web. 

Durante o projeto utilizamos o JQuery  para simplificar os scripts e interações com o HTML.

### Aprendizados Efetivos HS

Neste projeto desenvolvi mais minhas habilidades no back-End, aprendendo com utilizar uma Rest API considerada nova no mercado chamada Quarkus. Essa experiência me ajudou muito a como pesquisar  informações nas fontes primárias, que são as publicações técnicas geralmente realizadas pelos próprios criadores e responsáveis pelas mais diversas tecnologias. Considero esse aprendizado fundamental para minha trajetória pessoal e profissional, me tornando mais proativa em minhas skills de programação.

Já no front-End aprendi poucas coisas pois não foi minha principal foco de desenvolvimento no projeto mas aprendi um pouco sobre estruturas das páginas em HTML e funcionalidades em JavaScript.

- Criação de CRUD’S completos;
- Requisição GET, POST, PUT, DELETE;
- Organizar a arquitetura do projeto de forma correta;
- Usar lógica de programação para desenvolver regras para criação de promoções;
- Desenvolver aplicações utilizando frameworks de REST API: Sei fazer com autonomia;




<h1 align="center"> Projeto 4: 2º Semestre de 2022 </h1>

<div align="center"> Projeto Integrador - 4° Semestre | Fatec Prof. Jessen Vidal - 2022 | Cliente parceiro: Subiter </div>

## Visão do Projeto

Desenvolver uma plataforma web que organiza todos os dados referentes aos serviços prestados pela empresa, de forma interpretada, cujo o principal objetivo é criar chamados e agendamentos conforme as necessidades do cliente e solucioná-los de forma ponta a ponta entre a relação do cliente com o suporte e, suporte com a do administrador que, trabalha na criação e sincronização dos dados em um único lugar.

## Tecnologias adotadas na solução

### Java

Java é uma linguagem de programação orientada a objetos que foi criada na década de 1990 pela Sun Microsystems, e atualmente é propriedade da Oracle Corporation. É uma das linguagens de programação mais populares do mundo, usada em uma ampla variedade de aplicativos e sistemas, desde desenvolvimento de aplicativos desktop e web até jogos e dispositivos móveis.

### Vue.js

Vue.js é um framework de desenvolvimento web de código aberto e progressivo, amplamente utilizado para a criação de interfaces de usuário interativas. Ele se destaca pela sua simplicidade e facilidade de aprendizado, permitindo aos desenvolvedores criar aplicativos complexos de forma eficiente. Com uma arquitetura baseada em componentes, o Vue.js oferece uma abordagem modular para a construção de interfaces, facilitando a reutilização de código e a manutenção do projeto.

### SpringBoot

O Spring Boot é um framework de desenvolvimento de aplicativos Java que visa facilitar a criação de aplicativos robustos e escaláveis. Ele fornece uma configuração simplificada e pré-definida, permitindo aos desenvolvedores se concentrarem na lógica de negócios em vez de tarefas de configuração. Com o Spring Boot, é possível criar rapidamente aplicativos Java de maneira eficiente, aproveitando a poderosa plataforma Spring.

## Contribuições pessoais
Nesse projeto contribui principalmente na parte da definição de relacionamentos nas classes da aplicação, baseado em nossa modelagem do banco de dados. 
Desenvolvi também os CRUDS das classes de Chamados, Usuários e Agendamentos e a implementação de DTO'S nas classes que foram necessários.


<details>
<summary> Relacionamento usando annotations do javax.persistence: </summary>

![Untitled](https://media.discordapp.net/attachments/888964389368131629/1113104716151398532/image.png)
</details> 



<details>
<summary> DTO: </summary>
  
![Untitled](https://media.discordapp.net/attachments/888964389368131629/1113104206262456400/image.png?width=783&height=401)
</details> 


<details>
<summary> Métodos GET, POST, UPDATE E DELETE:</summary>
  
![Untitled](https://media.discordapp.net/attachments/888964389368131629/1113105760218533918/image.png?width=621&height=401)
</details>

<details>
<summary> MER:</summary>
  
![Untitled](https://media.discordapp.net/attachments/888964389368131629/1113101276616601630/WhatsApp_Image_2023-05-30_at_10.37.07.png?width=439&height=401)
</details>

### Aprendizados Efetivos HS
- Utilizar persistência de dados;
- Utilizar relacionamentos entre classes;
- Implementar níveis de acesso (Spring Security + JWT);
- Utilizar ORM;




<h1 align="center"> Projeto 5: 1º Semestre de 2023 </h1>

<div align="center"> Projeto Integrador - 5° Semestre | Fatec Prof. Jessen Vidal - 2023 | Cliente parceiro: Midall </div>

## Visão do Projeto
Automatizar a jornada de download de arquivos, armazenados em uma plataforma de vídeo, efetuando essa transferência para a nuvem, através do desenvolvimento de um serviço tipo aplicação, tendo como funcionalidade junto ao usuário apenas um menu de configuração, que terá os parâmetros necessários para que o serviço de download seja executado. processar automaticamente, gerando alertas caso ocorram erros de processamento. Salvar metadados de arquivos para construção de dashboard de monitoramento da execução do serviço e posterior análise de resultados e indicadores (ex.: quantidade de arquivos transferidos, quantidade de bytes transferidos, tempo de transferência, etc.).

## Tecnologias adotadas na solução

### Java
Java é uma linguagem de programação orientada a objetos que foi criada na década de 1990 pela Sun Microsystems, e atualmente é propriedade da Oracle Corporation. É uma das linguagens de programação mais populares do mundo, usada em uma ampla variedade de aplicativos e sistemas, desde desenvolvimento de aplicativos desktop e web até jogos e dispositivos móveis.

### SpringBoot
O Spring Boot é um framework de desenvolvimento de aplicativos Java que visa facilitar a criação de aplicativos robustos e escaláveis. Ele fornece uma configuração simplificada e pré-definida, permitindo aos desenvolvedores se concentrarem na lógica de negócios em vez de tarefas de configuração. Com o Spring Boot, é possível criar rapidamente aplicativos Java de maneira eficiente, aproveitando a poderosa plataforma Spring.

### AWS
A AWS (Amazon Web Services) é uma plataforma líder em serviços de computação em nuvem fornecida pela Amazon, que oferece uma ampla gama de serviços de infraestrutura escaláveis e seguros para empresas e desenvolvedores.

### Google Drive 
O Google Drive é um serviço de armazenamento em nuvem oferecido pelo Google. Ele permite que os usuários armazenem, compartilhem e acessem arquivos e documentos de forma online. Com recursos de colaboração em tempo real, o Google Drive é amplamente utilizado para armazenar documentos, fotos, vídeos e outros tipos de arquivos de forma acessível a partir de qualquer dispositivo com acesso à internet. 

## Contribuições Pessoais
Durante o desenvolvimento desse projeto, fui responsável na área de desenvolvimento na extração de metadados durante o envio de um arquivo do Google Drive para a AWS, para a elaboração da dashboard de monitoramento do cliente utilizando os recursos do fileMetadata do Google Drive API. 


<details> 
 <summary> Trecho do controller de extração de metadados </summary>

  
		@PostMapping("/upload")
	public ResponseEntity<?> uploadBasic(@RequestParam("file") MultipartFile file)
			throws IOException {
    Drive service = new Drive.Builder(new NetHttpTransport(), GsonFactory.getDefaultInstance(), requestInitializer)
				.setApplicationName("Drive samples").build();
   
	 Instant inicio = Instant.now();
		List<String> list = new ArrayList<>();
		list.add("1LFzz6RB4d-ePzRmyzVUC8zebcrYHzDTF");
		File fileMetadata = new File();
		fileMetadata.setParents(list);
		fileMetadata.setName(file.getOriginalFilename());
		String filePathd = new java.io.File(".").getCanonicalPath() + file.getOriginalFilename();
		file.transferTo(new java.io.File(filePathd));
  
		java.io.File filePath = new java.io.File(filePathd);
		FileContent mediaContent = new FileContent("multipart/form-data", filePath); 
		FileContent mediaContent = new FileContent("multipart/form-data", filePath);
		File files = service.files().create(fileMetadata, mediaContent).setFields("id").execute();
		System.out.println("File ID: " + files.getId());


		History history = new History();
		history.setNome_arquivo(file.getOriginalFilename());
		history.setFile_id(files.getId());
		history.setTamanho(file.getSize());
		history.setData_envio(LocalDate.now());

		FoldersSelect fol = folderService.findById(repo.findAll().get(0).getId());
		fileDownload.getFile(fol.getCodigo(), files.getId());


		Instant fim = Instant.now();
		Long duracao = Duration.between(inicio, fim).getSeconds();
		history.setTempo(duracao);
		historyService.save(history);
		return ResponseEntity.status(HttpStatus.OK).body(files);

	}

	@GetMapping("/files/{id}/metadata")
	public ResponseEntity<File> getFileMetadata(@PathVariable("id") String fileId) throws IOException {
		GoogleCredentials credentials = GoogleCredentials.getApplicationDefault()
				.createScoped(Arrays.asList(DriveScopes.DRIVE_METADATA));
		HttpRequestInitializer requestInitializer = new HttpCredentialsAdapter(credentials);
		Drive service = new Drive.Builder(new NetHttpTransport(), GsonFactory.getDefaultInstance(), requestInitializer)
				.setApplicationName("Drive samples").build();

		File filemetadata = service.files().get(fileId).execute();

		return ResponseEntity.ok(filemetadata);
	}

	@ExceptionHandler(IOException.class)
	public ResponseEntity<String> handleIOException(IOException e) {
		return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR)
				.body("Erro ao recuperar metadados do arquivo: " + e.getMessage());
	}

	@ExceptionHandler(Exception.class)
	public ResponseEntity<String> handleException(Exception e) {
		return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR)
				.body("Erro interno do servidor: " + e.getMessage());
    }
	}
	
A parte mais desafiadora, foi compreender o funcionamento da API do Google pois tive que me aprofundar em leituras da documentação disponibilizada no Google e não existiam muitos artigos mais detalhados que pudessem nos auxiliar na implementação em nosso projeto. A parte de extração de metadados era crucial para que fosse possível seguir com o desenvolvimento do nosso Dashboard de monitoramento de desempenho da aplicação. A lógica utilizada para o desenvolvimento dessa funcionalidade foi: Após a realização do upload do arquivo (imagem ou vídeo) era realizado um GETresponsável por recuperar os metadados de um arquivo no Google Drive com base em seu ID. 

 </details>

 <details>
  <summary> Desenvolvimento da dashboard </summary>
	 <img src="https://github.com/lara-leal/bertoti/assets/80706297/40392e65-11b5-4b75-891f-4845bd49b066"/>
	 <br></br>
	 Durante o desenvolvimento da dashboard, pude utilizar diferentes  recursos como o DAX do power BI com campos calculados, para armazenar e extrair informações como, tamanho do arquivo compartilhado e o tipo de arquivo mais compartilhado através da ferramenta.
  	 <br></br>


``` 
tamanho_arquivo = 
    IF (
        history[tamanho] < 1024,
        FORMAT ( history[tamanho] , "#0.0# B" ),
        IF (
            history[tamanho]  < POWER ( 2, 20 ),
            FORMAT ( history[tamanho]  / POWER ( 2, 10 ), "#0.0# KB" ),
            IF (
                history[tamanho]  < POWER ( 2, 30 ),
                FORMAT ( history[tamanho]  / POWER ( 2, 20 ), "#0.0# MB" ),
                FORMAT ( history[tamanho]  / POWER ( 2, 30 ), "#0.0# GB" )
            )
        )
    )
 ```

```
mais_utilizado = 
MAXX (
    TOPN (
        1,
        SELECTCOLUMNS (
            SUMMARIZE (
                'history',
                'history'[tipo_arquivo],
                "Count", COUNTROWS ('history')
            ),
            "tipo_arquivo", 'history'[tipo_arquivo],
            "Count", [Count]
        ),
        [Count],
        DESC
    ),
    [tipo_arquivo]
)
```

 </details>

Também nesse semestre atuei como Product Owner, onde fui responsável por realizar a prototipagem da aplicação utilizando a ferramenta Figma para que o cliente aprovasse o design da aplicação e validar se tinhamos entendido o desafio da maneira correta. Durante as sprints fui responsável por realizar a negociação da entregas, visando solucionar a dor do cliente e criar entregas possíveis para nosso time. 

<img src="https://i.ibb.co/zfLLfdW/image.png" alt="image" border="0"></a>

Outro tópico que tive como responsabilidade foi implementar o Issue Controll para que  as "issues" fossem usadas para rastrear tarefas, melhorias, bugs e discussões em nosso repositório. 


 ### Aprendizados Efetivos HS
 - Trabalhar com ferramentas da AWS; 
 - Utilizar Google drive API;
 - Entender insights de metadados para elaboração de dashboard de monitoramento;





<h1 align="center"> Projeto 6: 2º Semestre de 2023 </h1>

<div align="center"> Projeto Integrador - 6° Semestre | Fatec Prof. Jessen Vidal - 2023 | Cliente parceiro: Visiona </div>

## Visão do Projeto

O Proagro é um programa governamental que financia atividades agrícolas de pequenos e médios produtores no Brasil. Ao participar, o produtor precisa fornecer detalhes sobre sua atividade agrícola e a localização das áreas cultivadas. Esses dados são armazenados em tabelas e em um banco de dados. Além disso, informações sobre técnicas de cultivo, tipos de plantas, potencial de produção, dados de plantio e colheita são essenciais. O uso de sensoriamento remoto tem sido eficaz para monitorar atividades agrícolas, e os dados do Proagro são valiosos para criar modelos de inteligência artificial com base em informações obtidas por satélite. O desafio é apresentar esses dados de forma clara e intuitiva em um sistema de informação geográfica, combinando informações sobre operações agrícolas e dados de sensoriamento remoto.

## Tecnologias adotadas na solução

### Python

Python é uma linguagem de programação popular que foi criada na década de 1990 por Guido van Rossum. É conhecida por sua sintaxe simples e fácil de ler, o que a torna uma ótima escolha para iniciantes em programação. Python é usado em muitas áreas diferentes, incluindo ciência de dados, desenvolvimento web, automação de tarefas, inteligência artificial e muito mais. É uma linguagem interpretada, o que significa que o código é executado linha por linha sem a necessidade de compilação. Além disso, Python é uma linguagem de programação de alto nível, o que significa que é mais próxima da linguagem humana do que de uma linguagem de máquina, tornando a programação em Python mais intuitiva e acessível para muitas pessoas.

### PostgreSQL

PostgreSQL é um sistema de gerenciamento de banco de dados relacional (SGBDR) de código aberto e altamente confiável. Ele é amplamente conhecido por sua robustez, escalabilidade e recursos avançados que o tornam uma escolha popular para uma variedade de aplicações. Uma das principais características do PostgreSQL é sua capacidade de suportar grandes volumes de dados e cargas de trabalho intensivas.


### PostGIS
O PostGIS é uma extensão do PostgreSQL para lidar com dados geoespaciais em bancos de dados relacionais. Ele permite armazenar, consultar e analisar informações de localização, sendo essencial para sistemas de informação geográfica (SIG) e análises territoriais, oferecendo operações complexas e indexação espacial para eficiência na manipulação de dados geográficos.

## Contribuições Pessoais
Durante o projeto, minha principal contribuição consistiu na execução do extração, tratamento e carregamento de dados. O cliente nos forneceu os dados do banco por meio de arquivos .csv, juntamente com a modelagem atual do banco de dados. Inicialmente, realizei uma análise da modelagem, procedendo com a normalização e remodelagem do banco. 


<img src="https://i.ibb.co/2hyqpXV/mer-3.png" alt="mer-3" border="0">


Após essa fase, me dediquei ao tratamento dos dados, utilizando a biblioteca Pandas para filtrar exclusivamente as informações relacionadas à cultura de SOJA, uma vez que esses dados eram cruciais para atender às exigências da regra de negócio de nossa aplicação.
````
import pandas as pd
produtos = pd.read_csv(r'../../data/Produto.csv', encoding='ISO-8859-1')
soja = produtos[produtos['DESCRICAO'] == 'SOJA']`

empreendimento = pd.read_csv(r'../../data/Empreendimento.csv', sep=';', encoding='ISO-8859-1')
cod_empreendimento =  empreendimento[empreendimento['PRODUTO'] == 'SOJA']

sicor_cop_basico = pd.read_csv("C:/Users/leall/OneDrive/Área de Trabalho/02_TABS_BASICAS_OPERACAO_CREDITO_RURAL_PROAGRO_RECURSOS_PUBLICOS_PRIVADOS/SICOR_COP_BASICO.csv", sep=';', encoding='ISO-8859-1')
sicor_cop_basico = sicor_cop_basico.drop(columns=['DT_FIM_COLHEITA', 'DT_FIM_PLANTIO', 'DT_INICIO_PLANTIO', 'DT_INICIO_COLHEITA'])

merged = ref_bacen.merge(sicor_cop_basico, on=['REF_BACEN', 'NU_ORDEM'], how='inner')

glebas = pd.read_csv(r'C:/Users/leall/OneDrive/Área de Trabalho/03_TABS_COMP_BASICAS_OPERACOES_CREDITO_RURAL_PROAGRO_RECURSOS_PUB/Glebas.csv', sep=';', encoding='ISO-8859-1')
glebas_soja = glebas[(glebas['REF_BACEN'].isin(set(merged['REF_BACEN']))) & (glebas['NU_ORDEM'].isin(set(merged['NU_ORDEM'])))]
````





Posteriormente, após concluir o tratamento dos dados, realizei a criação dos comandos de INSERT dos dados no novo banco que fora criado.
````
with open('C:/Users/leall/OneDrive/Área de Trabalho/api-lara/GeoForesight-back/database/insert_postgres/insert_op.sql', 'w') as file:

    for index, row in df.iterrows():
        ref_bacen = str(row['ref_bacen'])
        nu_ordem = str(row['nu_ordem'])
        inicio_plantio = row['inicio_plantio']
        final_plantio = row['final_plantio']
        inicio_colheita = row['inicio_colheita']
        final_colheita = row['final_colheita']
        data_vencimento = row['data_vencimento']
        idempreendimento = row['idempreendimento']
        idevento = row['idevento']
        idsolo = row['idsolo']
        idirrigacao = row['idirrigacao']
        idciclo = row['idciclo']
        idgrao = row['idgrao']
        idcultivar = row['idcultivar']
        idprograma = row['idprograma']
        estado = row['estado']

        
        dataframe = query = f"INSERT INTO PUBLIC.operacao_credito_estadual(ref_bacen, nu_ordem, inicio_plantio, final_plantio, inicio_colheita, final_colheita, data_vencimento, idempreendimento, idevento, idsolo, idirrigacao, idciclo, idgrao, idcultivar, idprograma, estado) VALUES ('{ref_bacen}', '{nu_ordem}', '{inicio_plantio}', '{final_plantio}', '{inicio_colheita}', '{final_colheita}', '{data_vencimento}', {idempreendimento}, {idevento}, {idsolo}, {idirrigacao}, {idciclo}, {idgrao}, {idcultivar}, {idprograma}, '{estado}');\n"
        file.write(query)
````

Desempenhei um papel fundamental na implementação de alguns conceitos da Lei Geral de Proteção de Dados (LGPD) no backend da aplicação. Isso envolveu a elaboração de termos de uso e consentimento, a validação do aceite desses termos e a modificação da permissão concedida.

````
@app.route('/verificar_aceitacao', methods=['GET'])
@jwt_required()
def verificar_aceitacao():
    current_user = get_jwt_identity()

    query = text("""
        SELECT id_user, au.id_termo , data_aceitacao, au.aceite
            FROM aceitacao_usuario AS au
            join public.user as u on u.id = au.id_user 
            WHERE au.aceite = True
            AND au.data_aceitacao = ( SELECT MAX(data_aceitacao)
            FROM aceitacao_usuario
            WHERE id_user = au.id_user);
    """)

    result = db.session.execute(query, {'current_user': current_user})

    
    termos_aceitos = []
    for row in result:
        termos_aceitos.append({
            'id_user': row[0],
            'id_termo': row[1],
            'data_aceitacao': row[2].isoformat(),
            'aceite': row[3]
        })
    print(termos_aceitos)

    if termos_aceitos:
        return jsonify({'termos_aceitos': termos_aceitos})
    else:
        return jsonify({'message': 'Nenhum termo aceito encontrado'}), 404

````

Também tive a oportunidade de aprender como utilizar a extensão postGIS do PostgreSQL, que cria primeiramente tabelas com colunas espaciais, e entender como é feito um insert de dados geográficos. Por exemplo, na criação da coluna "coordenadas" é utilizado o tipo geography(Point,4326), que é utilizado para armazenar informações geográficas no formato Point usando o sistema de referência espacial WGS 84 (SRID 4326). 

````
CREATE TABLE IF NOT EXISTS public.glebas
(
    idgleba integer SERIAL,
    ref_bacen numeric,
    nu_ordem numeric,
    longitude character varying(255) COLLATE pg_catalog."default",
    latitude character varying(255) COLLATE pg_catalog."default",
    coordenadas geography(Point,4326),
    altitude numeric,
    nu_ponto numeric,
    nu_identificador numeric,
    nu_indice numeric,
    CONSTRAINT glebas_pkey PRIMARY KEY (idgleba),
    CONSTRAINT glebas_ref_bacen_nu_ordem_fkey FOREIGN KEY (nu_ordem, ref_bacen)
        REFERENCES public.operacao_credito_estadual (nu_ordem, ref_bacen) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)
````
Já para criar um insert é necessário utilizar a função ST_GeogFromText que cria um ponto em um espaço bidimensional usando as coordenadas, gerando um dado geográfico.
````
INSERT INTO PUBLIC.GLEBAS(REF_BACEN,  NU_ORDEM, LONGITUDE, LATITUDE,  COORDENADAS, ALTITUDE, NU_PONTO,NU_IDENTIFICADOR) VALUES('513678782','1',-52.2909909,-27.7581412,ST_GeogFromText('POINT(-52.2909909 -27.7581412)'),0,29,1);
````
###  Aprendizados Efetivos HS
- Trabalhar com a biblioteca Pandas do Python para extrair, transformar e carregar dados;
- Utilizar a extensão postGIS do PostgreSQL;
- Remodelagem e normalização de um banco de dados legado;
- Trabalhar com Flask para desenvolvimento do backend da aplicação;
