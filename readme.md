[![Visual Studio](https://badgen.net/badge/icon/visualstudio?icon=visualstudio&label)](https://visualstudio.microsoft.com) ![Pfsense](https://badgen.net/badge/Pfsense%20CE%20/2.8.1?color=blue) ![E2Guardian](https://badgen.net/badge/E2Guardian/5.5.9?color=purple) [![made-with-Markdown](https://img.shields.io/badge/Made%20with-Markdown-1f425f.svg)](http://commonmark.org)

# Proxy Cotefácil

#### Objetivo

Esse repositório tem como objetivo armazenar uma copia das configurações das ACLS do proxy da empresa. Para uma melhor visualização optei por separar cada departamento em uma pasta com sua respectiva blacklist e as exceções.

#### A Blacklist

Para facilitar a configuração foi usada uma blacklist da The Université Toulouse (https://en.univ-toulouse.fr), pois além de possuir uma gama enorme de sites ela é atualizada com frequência. Abaixo será disponibilizado uma tabela com cada categoria disponível e uma breve descrição dela.
<br>

| **Categoria**           | **Descrição**                                                  |
|:------------------------|:---------------------------------------------------------------|
| adult                   | Sites adultos, variando de erótico a pornografia explícita.    |
| agressif                | Sites racistas, antissemitas ou que incitam o ódio.            |
| ai                      | Sites de Inteligência Artificial.                              |
| arjel                   | Sites de apostas online certificados pela ARJEL.               |
| associations_religieuse | Sites de associações religiosas.                               |
| astrology               | Astrologia.                                                    |
| audio-video             | Sites focados em conteúdo de áudio e vídeo.                    |
| bank                    | Internet Banking.                                              |
| bitcoin                 | Sites relacionados a Bitcoin.                                  |
| blog                    | Plataformas e sites que hospedam blogs.                        |
| celebrity               | Notícias sobre celebridades e fofocas.                         |
| chat                    | Sites de bate-papo e conversação online.                       |
| child                   | Conteúdo livre/autorizado para crianças.                       |
| cleaning                | Sites para limpeza e atualização de computadores.              |
| cooking                 | Sites de culinária e receitas.                                 |
| cryptojacking           | Sites de mineração via sequestro de navegador.                 |
| dangerous_material      | Sites sobre materiais perigosos (explosivos, venenos, etc.).   |
| dating                  | Sites de encontros e relacionamentos.                          |
| ddos                    | Sites relacionados a ataques de negação de serviço.            |
| dialer                  | Sites de discadores (dialers).                                 |
| doh                     | Servidores DNS sobre HTTP ou equivalentes.                     |
| download                | Sites que permitem o download de softwares.                    |
| drogue                  | Conteúdo relacionado a drogas.                                 |
| dynamic-dns             | Sites que oferecem serviços de DNS dinâmico.                   |
| educational_games       | Sites de jogos educativos.                                     |
| examen_pix              | Lista exclusiva para exames PIX (França). Não usar fora disso. |
| fakenews                | Sites que propagam notícias falsas.                            |
| filehosting             | Hospedagem de arquivos (vídeos, imagens, sons).                |
| financial               | Informações financeiras e mercado de ações.                    |
| forums                  | Fóruns de discussão.                                           |
| gambling                | Sites de apostas online, cassinos, etc.                        |
| games                   | Sites de jogos online ou distribuição de jogos.                |
| hacking                 | Sites de piratagem e ataques cibernéticos.                     |
| jobsearch               | Sites de busca de empregos.                                    |
| lingerie                | Sites de lingerie.                                             |
| liste_bu                | Sites educativos para bibliotecas (Univ-Toulouse).             |
| malware                 | Sites que injetam malwares.                                    |
| manga                   | Conteúdo relacionado a mangás e quadrinhos.                    |
| marketingware           | Sites de marketing com práticas agressivas.                    |
| mixed_adult             | Sites com porções de conteúdo adulto não estruturado.          |
| mobile-phone            | Sites para celulares (toques, etc.).                           |
| phishing                | Sites de phishing e golpes (cópia de malware).                 |
| press                   | Sites de imprensa e notícias.                                  |
| publicite               | Publicidade e anúncios.                                        |
| radio                   | Sites de rádio online.                                         |
| reaffected              | Sites que mudaram de dono e conteúdo.                          |
| redirector              | Sites que permitem contornar filtros.                          |
| remote-control          | Sites de controle remoto de dispositivos.                      |
| residential-proxies     | Sites que distribuem proxies residenciais.                     |
| sect                    | Seitas.                                                        |
| sexual_education        | Educação sexual (pode ser detectado como pornografia).         |
| shopping                | Sites de compras e e-commerce.                                 |
| shortener               | Encurtadores de URL.                                           |
| social_networks         | Redes sociais.                                                 |
| sports                  | Esportes.                                                      |
| stalkerware             | Sites com ferramentas de espionagem pessoal.                   |
| strict_redirector       | Redirector aplicado a motores de busca.                        |
| strong_redirector       | Redirector para Google/outros (bloqueio de termos).            |
| translation             | Sites de tradução.                                             |
| tricheur                | Sites que ensinam como trapacear em exames.                    |
| tricheur_pix            | Sites bloqueados para exames PIX (França).                     |
| update                  | Atualizações de sistemas e softwares.                          |
| vpn                     | Sites de serviços VPN.                                         |
| warez                   | Distribuição de softwares ou vídeos piratas.                   |
| webhosting              | Sites de hospedagem web.                                       |
| webmail                 | Serviços de webmail (Hotmail, Gmail, etc.).                    |

#### Os grupos

Depois de analisar quais seriam os acessos liberados para cada departamento busquei reduzuir ao máximo a quantidade de grupos para melhorar o processamento e o fluxo de trabalho do proxy, afim de evitar lentidão na rede. Atualmente há 3 grupos configurados para o prédio do Jardim Contorno:
* **Administrativo**: É composto pelos os departamentos de Coodenação de vendas, Recurosos Humanos e Treinamento
* **Comercial**: Grupo para os operadores de vendas e Financeiro (cobrança)
* **Suporte**: Engloba os depatamentos de Suporte (Help Desk, Service Desk, Monitoramento e OL), Customer Success, Fornecedores e Parceiros, Novos Negócios
E 3 para o prédio da Av. Duque de Caxias:
* **Desenvolvimeto**: É o grupo padrão para o desenvolvimento, posssui 2 variações, uma com acesso ao WhatsApp Web e outra com acesso ao Linkedin
* **Desenvolvimeto_WhatsApp**: Possui as mesmas configurações de acesso do grupo Desenvolvimento mas tem permissão de acesso ao WhatsApp
* **Desenvolvimeto_Linkedin**: Possui as mesmas configurações de acesso do grupo Desenvolvimento mas tem permissão de acesso ao Linkedin
