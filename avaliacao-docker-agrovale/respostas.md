# Respostas · Avaliação Prática de Docker · Cooperativa AgroVale (Turma A)

Nome: Denis Goes do Nascimento
Matrícula: 26128943
Usuário do GitHub: DenisGoes
Usuário do Docker Hub: denisgoes

Responda com as suas palavras e com o que aconteceu na SUA máquina. Resposta curta e certa vale mais
do que texto longo copiado. Resposta que contradiz o seu próprio Dockerfile ou compose vale zero.

## Parte 1 · Dockerfile do portal

1. Qual imagem base você usou e qual o tamanho final da imagem do portal (saída de `docker images`)? - nginx alpine. 


2. Em qual pasta do container o Nginx procura os arquivos do site? Mostre o comando que você usou para
   conferir que o `index.html` está lá dentro. - /usr/share/nginx/html/

## Parte 2 · Docker Hub

3. Nome completo da imagem publicada e link público do repositório no Docker Hub. denisgoes/agrovale-portal https://hub.docker.com/repository/docker/denisgoes/agrovale-portal/general

4. Por que o `docker login` foi feito com um token de acesso e não com a senha da conta? - O token de acesso foi utilizado para aumentar a segurança

## Parte 3 · Página de manutenção

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

| # | Instrução | O que estava errado | O que você viu acontecer | Como corrigiu |
|---|---|---|---|---|
| 1 | FROM| Uso de tag :latest em vez de tag fixa de versão| Alerta do verificador sobre falta de tag de versão fixa | Alterado para nginx:alpine no Dockerfile|
| 2 | COPY| Destino do arquivo index.html estava em caminho incorreto| Container subia, mas exibia a página padrão de erro/welcome do Nginx|Corrigido o caminho para COPY site/index.html /usr/share/nginx/html/index.html |
| 3 | CMD / EXPOSE| Falta do EXPOSE 80 e Nginx configurado sem manter o processo ativo| Container encerrava a execução imediatamente após subir (Exited (0))| Adicionado EXPOSE 80 e mantido o Nginx em primeiro plano (daemon off;)|


6. Qual a diferença entre `-p 7042:80` e `-p 80:7042` no `docker run`? Qual dos dois números é a porta do container? Portas do container: 80 e 7042, -p 7042:80 é a porta do container como 80 e do host como 7042` e `-p 80:7042 porta do container como 7042 e do host como 80`.

## Parte 4 · docker-compose.yml

7. No serviço `blog`, por que `WORDPRESS_DB_HOST` recebe `db` e não `localhost`? - Está recebendo variavel de ambiente.

8. Por que o serviço `db` não publica a porta 3306? Se precisar consultar o banco, como faz sem publicar
   a porta? Mostre o comando. - Por segurança e isolamento da rede

## Parte 5 · Persistência

9. Quais comandos você usou para derrubar e subir a stack? Qual comando teria apagado o post que você criou,
   e por quê? docker compose down docker compose up -d e docker compose down -v - precisava atualizar o container. 

10. Código de conclusão impresso pelo verificador:

```
(AGROVALE-26128943-F66900BF)
```
