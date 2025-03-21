---
title: 'Adicionar um campo MX à configuração do domínio'
slug: e-mail-partilhado-manual-de-configuracao-mx-com-zona-dns-ovh
excerpt: 'Saiba como adicionar um campo MX ao seu domínio da OVH'
section: 'DNS e zona DNS'
order: 4
---

**Última atualização: 05/02/2019**

## Sumário

O campo MX permite associar um domínio a um servidor de e-mail para que os servidores que têm de enviar e-mails para os seus endereços saibam para onde os devem enviar. É provável que o seu fornecedor tenha vários servidores de e-mail, caso em que deverá criar vários campos MX.

**Saiba como adicionar um campo MX à configuração do seu domínio da OVH.**

## Requisitos

- Ter acesso à secção de gestão do domínio na [Área de Cliente OVH](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt){.external}.
- Ter acesso à [Área de cliente OVH](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt){.external}.
- O domínio do e-mail tem de usar a configuração da OVH (os servidores DNS da OVH).

> [!warning]
>
> - Se o domínio não usar os servidores DNS da OVH, os campos MX deverão ser alterados a partir da interface do agente responsável pela configuração do seu domínio.
>
> - Se o seu domínio for gerido pela OVH, verifique se este está a usar a configuração OVH. Para tal, aceda à [Área de Cliente](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt){.external}, selecione o domínio e clique em `Servidores DNS`{.action}.
>

## Instruções

### 1 - Informações básicas sobre o campo MX

Um campo MX associa o seu domínio ao servidor do seu fornecedor de e-mail (a OVH, por exemplo). Quando um dos seus contactos lhe envia um e-mail, o servidor que realiza o envio sabe para que servidor o deve reencaminhar graças ao campo MX.

Uma vez que é impossível configurar vários campos MX para o mesmo domínio, é necessário definir prioridades para cada um deles. Isto permite que os servidores que enviam e-mails saibam para que servidor devem dar prioridade. No entanto, não poderá adicionar campos MX que pertençam ao mesmo fornecedor.

De forma geral, **alterar os campos MX do domínio é uma operação delicada**: uma alteração inadequada poderia, por exemplo, impossibilitar a receção de novas mensagens nos seus endereços de e-mail. Assim, recomendamos vivamente que tome as devidas precauções ao realizar esta operação.

### 2 - Conhecer a configuração MX da OVH

Consulte abaixo a configuração MX da OVH que deve utilizar nas soluções MX Plan (só ou incluída numa oferta de [alojamento web da OVH](https://www.ovhcloud.com/pt/web-hosting/){.external}, [E-mail Pro](https://www.ovhcloud.com/pt/emails/email-pro/){.external} e [Exchange](https://www.ovh.com/pt/emails/){.external}. Os nossos servidores de e-mail dispõem de um anti-spam e antivírus.

|Domínio|TTL|Tipo de registo|Prioridade|Destino|
|---|---|---|---|---|
|*deixar em branco*|3600|MX|1|mx0.mail.ovh.net.|
|*deixar em branco*|3600|MX|5|mx1.mail.ovh.net.|
|*deixar em branco*|3600|MX|50|mx2.mail.ovh.net.|
|*deixar em branco*|3600|MX|100|mx3.mail.ovh.net.|
|*deixar em branco*|3600|MX|200|mx4.mail.ovh.net.|

Deve utilizar estes diferentes campos MX na configuração DNS do seu domínio. O passo seguinte permite-lhe efetuar esta operação na configuração DNS da OVH do domínio.

### 3 - Alterar a configuração de um campo MX da OVH

Para alterar os campos MX na configuração da OVH do seu domínio, aceda à [Área de Cliente OVH](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt){.external}. No menu à esquerda, selecione `Domínios`{.action}, clique no domínio pretendido e aceda ao separador `Zona DNS`{.action}.

Na tabela pode ver a configuração OVH do seu domínio. Cada linha corresponde a um registo DNS. Recomendamos que comece por verificar se já existem registos MX na configuração DNS da OVH do seu domínio através dos filtros.

![dnsmxrecord](images/mx-records-dns-zone.png){.thumbnail}

Se já existirem e pretender substituí-los, clique no ícone dos três pontos à direita da linha correspondente e clique em `Eliminar entrada`{.action}. Contudo, certifique-se de que não deixa o seu domínio sem registos MX quando adicionar os registos MX pretendidos.

Para isso, clique no botão `Adicionar uma entrada`{.action} e selecione a opção `MX`{.action}. Introduza as informações necessárias em função da solução de e-mail selecionada:

- **se possuir uma solução de e-mail da OVH**: consulte as informações no passo [“2 - Conhecer a configuração MX da OVH”](https://docs.ovh.com/pt/domains/e-mail-partilhado-manual-de-configuracao-mx-com-zona-dns-ovh/#2-conhecer-a-configuracao-mx-da-ovh){.external};

- **se possuir outra solução de e-mail**: consulte as informações comunicadas pelo seu fornecedor de serviço de e-mail.

Depois de preencher os dados, finalize os passos e clique em `Validar`{.action}.

> [!primary]
>
> A propagação das alterações efetuadas pode demorar entre 4 e 24 horas.
>

## Quer saber mais?

[Alterar os servidores DNS de um nome de domínio OVH](https://docs.ovh.com/pt/domains/partilhado_generalidades_sobre_os_servidores_dns/){.external}.

[Como editar a minha zona DNS?](https://docs.ovh.com/pt/domains/alojamento_partilhado_como_editar_a_minha_zona_dns/){.external}

Fale com a nossa comunidade de utilizadores em [https://community.ovh.com/en/](https://community.ovh.com/en/){.external}