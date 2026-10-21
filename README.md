# Relatório de Plantão

Formulário que as cuidadoras de Luiz e Luzia preenchem a cada plantão. No fim do plantão, ele gera uma imagem organizada do relatório para enviar no grupo da família pelo WhatsApp. Depois que a cuidadora confirma o envio, os dados vão para a planilha **Report-Luiz-Luzia** no Google Planilhas.

Site: https://lromano000.github.io/plantao/

## Como funciona

1. A cuidadora abre o site e toca em **Começar novo formulário**.
2. Durante o plantão, ela preenche o formulário: pressão e FC, banheiro, remédios, refeições e observações. Cada item pode ter várias linhas, com o horário em manhã, tarde ou noite.
3. No fim, toca em **Compartilhar no WhatsApp** e envia as imagens no grupo.
4. O site pergunta se o relatório foi enviado. Quando ela responde **Sim**, os dados vão para a planilha e o formulário é liberado para o próximo plantão.

Se faltar internet nessa hora, o relatório fica guardado no celular e é enviado sozinho quando a conexão voltar.

## Arquivos

- `index.html`: o site inteiro, num arquivo só.
- O script da planilha (`apps-script.gs`) fica no Apps Script da própria planilha (Extensões → Apps Script), não neste repositório.

## Configurações no `index.html`

No começo do `<script>`, o bloco **CONFIGURAÇÃO** define:

- as cuidadoras, os pacientes, os turnos e as refeições;
- as opções de aceitação e as ocorrências ("Saiu para beber" aparece só para o Luiz);
- `PLANILHA_URL`, o endereço do App da Web do Apps Script, terminado em `/exec`. Se ficar vazio, o site funciona, mas não grava na planilha.

Para mudar o site, edite o `index.html` e faça o commit. O GitHub Pages atualiza em um ou dois minutos.

## Planilha

A planilha tem uma aba para cada tipo de registro: Plantões, Sinais, Banheiro, Remédios e Refeições. Todas as linhas do mesmo plantão têm o mesmo **ID**. Não renomeie as abas nem mude a ordem das colunas, porque o script grava pela posição.

### Publicar o script de novo depois de uma alteração

No Apps Script, abra **Deploy → Manage deployments**, clique no lápis, escolha **New version** e depois **Deploy**. Assim o endereço continua o mesmo e o site não precisa mudar.

### Instalar do zero

1. Na planilha, abra **Extensões → Apps Script**, cole o `apps-script.gs` e salve.
2. Clique em **Deploy → New deployment → Web app** e preencha *Execute as: Me* e *Who has access: Anyone*.
3. Autorize com a conta Google. No aviso "Google hasn't verified this app", clique em *Advanced → Go to … (unsafe)*.
4. Copie o URL que termina em `/exec` e coloque em `PLANILHA_URL` no `index.html`.

## Privacidade

Nenhum dado dos pacientes fica neste repositório. Tudo é preenchido no celular, e os registros vão só para a planilha, que é privada. O endereço do script permite apenas *adicionar* linhas na planilha; ele não deixa ler nem apagar nada.
