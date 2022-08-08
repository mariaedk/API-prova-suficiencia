# API Prova Suficiência

Repositório para a API da prova de suficiência da matéria PROG. WEB II

ENUNCIADO:
1. Faça um Web Service REST com comunicação JSON conforme os serviços 
definidos a seguir. Os serviços devem retornar os códigos de erros conforme os 
códigos de resposta REST (https://docs.microsoft.com/pt-br/partner/develop/errorcodes), caso um serviço seja invocado de forma incorreta. (25%)
2. A partir dos serviços, os dados devem ser persistidos em um banco de dados 
relacional através de um framework ORM (JPA, Entity Manager, Sequelize, etc) com 
nomenclatura padrão de BD, isto é, nome da tabela no plural e nome da classe no 
singular, por exemplo. As tabelas e atributos devem ser gerados por este 
framework (25%)
3. Algum serviço deve ser configurado para ser acessado somente caso o usuário 
estiver autenticado por meio de um token. Para isso, deve-se utilizar algum 
framework de segurança como o OAuth (15%)
4. Deve-se disponibilizar uma documentação utilizando Swagger (15%)
5. Uso de MVC + DAO (15%)
6. Todos os atributos nas classes modelo devem ser validados (5%)
7. Fique à vontade para incluir novos serviços em caso de necessidade.

## Detalhes

* Linguagem: Java 11
* Framework: Springboot
* Banco de Dados: MYSQL
* Para acessar a documentação (com projeto rodando): http://localhost:8080/swagger-ui.html#/

## Instruções para rodar o projeto:

* Importe o projeto para IDE de sua preferência. Recomendável: https://spring.io/tools
* Adeque o arquivo application.properties do projeto:
![image](https://user-images.githubusercontent.com/62608046/183316809-d97e3dd8-38f5-44ac-bd22-2e3feefeceae.png)

* Caso esteja usando outro banco, adicione o driver correspondente, junto com a URL, e adeque o usuário e a senha do banco para o seu.
* Como é usado autenticação via token, deve-se primeiro criar ao menos um usuário no banco de dados. Essa inserção foi feita manualmente.
* No arquivo ApiRestProvaApplication, descomente o método "public static String getPasswordEncoder(String senha)" na classe e também descomente o System.out.println() no método main
![image](https://user-images.githubusercontent.com/62608046/183317047-58c5263b-78cf-4e41-a068-8df181c8ce68.png)
* Rode o projeto. No VS CODE, usar o comando <code> ./mvnw spring-boot:run </code> . Na IDE do springboot, apenas clicar no botão "Run".
* Será exibida na console algo parecido com:
<code>$2a$10$d3kCkIeCk5n35amQWZqkpuDv83likUMqEF6L2EwqcvK5vgThTbWX6</code>
* Isso é equivalente a String "senha123". Caso deseje que seu usuário tenha outra senha, altere a string passada como parâmetro.
* Feito isso, insira manualmente no banco de dados, um nome de usuário, um id, e passe na senha, o que foi printado na console do projeto.

## Como utilizar
* O arquivo "api-rest-furb.postman_collection.json" que está no repositório pode ser importado no POSTMAN. Ele é um arquivo de coleção de requisições.
* Com isso, será possível testar o projeto.
* Como descrito no enunciado, um serviço deveria ser acessado apenas por autenticação. O serviço é o de produtos. Para que seja possível inserir uma comanda com produtos, é necessário, primeiro, que estes produtos existam. Para criar produtos, deve-se estar autenticado.
* No ENDPOINT /login:
![image](https://user-images.githubusercontent.com/62608046/183317307-2e0c56de-5be0-48d2-b157-c600e0289fa6.png)
* Passe o usuário e senha escolhidos por você como descrito na imagem. 
* Se obter sucesso, um TOKEN será devolvido
![image](https://user-images.githubusercontent.com/62608046/183317341-024df7ef-00dd-4a58-9b3e-acad812eb226.png)
* Este token deve ser utilizado em qualquer requisição do serviço PRODUTO
![image](https://user-images.githubusercontent.com/62608046/183317356-50502c8b-823b-4681-8dcf-0f08d22d72fd.png)



