---
title: Gerir os seus arquivos a partir de um cliente Swift (Cyberduck)
slug: pca/cyberduck
excerpt: Saiba como configurar o Cyberduck para gerir o seu Public Cloud Archive
section: Public Cloud Archive
order: 80
---

> [!primary]
> Esta tradução foi automaticamente gerada pelo nosso parceiro SYSTRAN. Em certos casos, poderão ocorrer formulações imprecisas, como por exemplo nomes de botões ou detalhes técnicos. Recomendamos que consulte a versão inglesa ou francesa do manual, caso tenha alguma dúvida. Se nos quiser ajudar a melhorar esta tradução, clique em "Contribuir" nesta página.
>

**Última atualização: 18/06/2021**

## Objetivo

O Public Cloud Archive é uma solução de armazenamento que pode ser utilizada com a ajuda das API OpenStack. No entanto, é possível que não esteja familiarizado com esta forma de gerir um espaço de armazenamento.

Existem, portanto, soluções gráficas que utilizam de forma invisível APIs OpenStack para si. CyberDuck faz parte destas soluções e é facilmente configurável.

Estão também disponíveis outras interfaces, cuja configuração é semelhante à que iremos apresentar-lhe.

**Saiba como configurar o Cyberduck para poder gerir o seu Public Cloud Archive com a ajuda de uma interface gráfica baseada nas API OpenStack.**

> [!warning]
>
> A responsabilidade sobre a configuração e a gestão dos serviços que a OVHcloud disponibiliza recai sobre o utilizador. Assim, deverá certificar-se de que estes funcionam corretamente.
>
> Este guia explica como implementar algumas medidas para otimizar a performance e a segurança do seu sistema. No entanto, se encontrar dificuldades, recomendamos que recorra a um prestador de serviços especializado e/ou que contacte o editor do serviço. Não poderemos proporcionar-lhe assistência técnica. Para mais informações, aceda à secção «Quer saber mais?» deste guia.
>

## Requisitos

- Descarregar e instalar [Cyberduck](https://cyberduck.io/).
- Ter os dados de utilizador (*OS_USERNAME*) e os projetos (*OS_PROJECT_NAME* ou *OS_TENANT_NAME*) disponíveis para o descarregar o ficheiro "OpenRC" no menu [Users and Roles](https://docs.ovh.com/pt/public-cloud/carregar-as-variaveis-de-ambiente-openstack/#etapa-1-recuperar-as-variaveis) da sua [Área de Cliente Public Cloud da OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt).
- Ter a palavra-passe de utilizador OpenStack.

Se já não conhece a sua palavra-passe de utilizador OpenStack, pode alterá-la através [deste manual](https://docs.ovh.com/pt/public-cloud/alteracao-da-palavra-passe-de-um-utilizador-openstack/).

## Instruções

**Este guia foi atualizado com base na versão 7.9.2 do Cyberduck para MacOS.**

> [!primary]
>
> Consoante a fonte de download do seu ficheiro OpenRC (a partir do Horizon ou a partir do seu Espaço Cliente OVHcloud), o seu identificador de projeto pode ser designado *OS_PROJECT_NAME* ou *OS_TENANT_NAME*.
>

Em Cyberduck, abra uma ligação "OpenStack Swift (Keystone 3)".

![pca-cyberduck](images/login.png){.thumbnail}

Queira introduzir as seguintes informações:

- Servidor: auth.cloud.ovh.net
- Projeto:Domínio:Username: OS_PROJECT_NAME:default:OS_USERNAME
- Password: a palavra-passe do seu utilizador OpenStack

A seguir, clique em `Connecter`{.action}. Uma vez ligado, terá acesso à arborescência das suas pastas e ficheiros.

![pca-cyberduck](images/successful-login.png){.thumbnail}

> [!primary]
>
> Em caso de dificuldade de ligação, pode descarregar o perfil de ligação Cyberduck para OpenStack Swift (Keystone 3) e abri-lo com Cyberduck.
> <br><br>Clique <a href="https://trac.cyberduck.io/browser/shelves/02.2020/profiles/default/Openstack%20Swift%20(Keystone%203).cyberduckprofile?rev=48724&order=name" download>aqui em "Guardar o alvo do link em baixo"</a> para descarregar o perfil.
>

## Saiba mais

[Documentação de Cyberduck](https://trac.cyberduck.io/wiki/help/en){.external}

[Primeiros passos com a API Swift](https://docs.ovh.com/pt/public-cloud/os_primeiros_passos_com_a_api_swift/)

Fale com a nossa comunidade de utilizadores <https://community.ovh.com/en/>.
