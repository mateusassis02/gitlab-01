# Gitlab-01
 
Iniciei mais um projeto com Pipelines, dessa vez utilizando o GitLab. 

Como de costume, todo o ambiente é hospedado na AWS, então para criação da maquina EC2 Ubuntu, utilizei o Terraform, e então realizei os updates inicias na maquina e após isso instalei o docker e o docker-compose, além da configuração inicial do GitLab na maquina Ubuntu da AWS. Basicamente a configuração do GitLab na maquina é a configuração de executores específicos, que é a instalação do GitLab Runner. Registrar o executor com a URL do GitLab e depois registrar o tokken. Após todo esse procedimento é possível já fazer a conteinerização da primeira imagem docker, que é o gitlab-runner para pode utilizar o executor que foi configurado na parte web do GitLab. Também é necessário fazer um pull da imagem do mysql:5.7 e do wordpress:latest. Após todos esses procedimentos inicias a maquina está pronta e toda a configuração restante será feita no próprio GitLab.  
 Pois bem, foi necessário também fazer a integração do Gitlab com o SonarCloud, a autenticação foi feita com o mesmo acesso do GitLab e integrado o repositório que foi criado chamado de gitlab-01. Após fazer essa integração também é necessário fazer as configurações inicias e criar um arquivo chamado sonar-project.properties, pois nesse projeto terá um stage que o código vai ser testado também pelo SonarCloud. Após todas essas configurações, foi criado o primeiro arquivo gitlab-ci.yml que basicamente contem toda a estrutura do código, inclusive um deploy para o wordpress, e um outro arquivo no repositório chamado de docker-compose.yml que contém uma estrutura para criação do ambiente do wordpress com a imagem do mysql, a criação do usuário, banco de dados do wordpress e também a porta que o wordpress vai utilizar. O arquivo gitlab-ci.yml é dividido em 4 stages principais que são eles; 

- Qualidade - Responsável por verificar o compose e o sonacloud-check(o arquivo configurado de sonar-project.properties) 

- Build - A construção 

- Deploy - A implantação dividido em 2 partes, que são o deploy do wordpress e após isso uma verificação no deploy 

- Notificação - Notifica se o código foi realizado com sucesso ou com falhas no Telegram. 

Após todos esses stages, é recebido uma mensagem pelo Telegram, através de um bot criado e ingressado em um grupo para esse projeto, de que a Pipeline foi executada com sucesso, ou em caso de falhas, também terá o retorno informado que houve falhas. 

Você pode encontrar o projeto em um repositório no meu GitLab: https://lnkd.in/d5iEdtiF

Por fim as imagens do projeto estão anexadas no repositório do GitLab. 

Referencias: curso de GitLab CI - Para Pipelines CI/CD & DevOps do Claudio Antonio da Silva , que inclusive tive alguns problemas inicias com a Pipeline, e o mesmo foi muito prestativo, fez ate uma call comigo, compartilhei a minha tela, e só finalizou depois de solucionar o problema. Recomendo demais!


#AWS #docker #github #pipeline #terraform #IaC



