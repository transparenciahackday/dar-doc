#################
Tipos de entradas
#################

Esta é uma lista exaustiva de todos os tipos específicos de entradas que podemos
encontrar nas transcrições.  É uma referência para quem tiver curiosidade sobre
como funcionam os scripts que processam os textos e determinam os tipos para
podermos ter transcrições bonitinhas no Demo.cratica (e outros do género).

Em cada tipo são especificados

* **exemplos** adaptados das transcrições originais
* o **nome interno** em inglês, usado nos programas, scripts e transcrições em
  JSON, para manter a coerência com as linguagens de programação, e também para
  permitir a fácil adaptação dos formatos a outras línguas
* o **nome completo** em português, para ser usado em interfaces

.. NOTE::
    Estas categorias dizem apenas respeito à XII Legislatura, iniciada em 2011.  Poderão existir outros tipos de entradas em transcrições anteriores a essa legislatura.

============
Intervenções
============

Intervenção (início)
---------------------

* Quando é dada a palavra a um deputado ou membro de governo e este inicia a sua intervenção. 
* Quando o presidente intervém (em expediente) ou dá a palavra.
* Quando o secretário intervém

Vem sempre precedida do nome do orador. O orador poderá ser um deputado, o presidente, secretário, Primeiro-Ministro, ou uma pessoa externa ao Parlamento (alguns membros do Governo, Presidente da República, convidados). Para cada tipo de orador, determinámos um tipo individual de intervenção, de forma a mostrá-los de forma específica no Demo.cratica.

Exemplo
  O Sr. **Alfredo Nenhures** (PSN): — Sr.ª Presidente, Sr.as e Srs. Deputados, esta
  situação é insustentável.
Nome interno
    ``mp_statement``, ``president_statement``, ``secretary_statement``, ``pm_statement``, ``minister_statement``, ``statesecretary_statement``
Nome completo
    Intervenção, Intervenção (presidente), Intervenção (secretário), Intervenção (PM), Intervenção (Ministro), Intervenção (Sec. Estado)

Aparte
------
* Quando um deputado interrompe outro
* Quando o presidente indica o final do tempo ou faz uma pequena observação
  durante uma intervenção
* Quando um deputado pede a palavra para intervir; se lhe é dada a palavra, a
  seguinte será uma Intervenção normal, mas o pedido deve ser um aparte.

O aparte é um tipo particular de intervenção. A nossa definição pode não
corresponder à figura oficial do aparte. O termo é o que usamos para qualquer
intervenção feita a interromper ou interpelar brevemente outro orador.

Pode ser vindo de um deputado, de uma bancada (ex. "Vozes do PSD: - Muito bem!")
ou do presidente.  No original não existe distinção entre a intervenção e um
aparte, pelo que é necessário determinar se está a aparecer a seguir à
intervenção ou continuação de outro orador. 

Neste momento fazemos uma análise preguiçosa, e presumimos que intervenções com
menos de 80 caracteres são um aparte, excepto quando se seguem a uma intervenção
do presidente a dar a palavra.

Exemplos
  O Sr. **Alfredo Nenhures** (PSN): — É uma vergonha!

  **Vozes do PSN e do PPM**: — Muito bem!

  A Sr.ª **Presidente**: — Sr. Deputado, já ultrapassou em 1 minuto o tempo de que
  dispunha...

Nome interno
    ``mp_aside``, ``president_aside``, ``secretary_aside``, ``pm_aside``,
    ``minister_aside``, ``statesecretary_aside``
Nome completo
    Aparte, Aparte (presidente), Aparte (secretário), Aparte (PM), Aparte
    (Ministro), Aparte (Sec. Estado)

Continuação
-----------
Continuação de uma intervenção: depois de uma interrupção. Às vezes o orador é
identificado novamente, mas muitas vezes a intervenção surge sem isso,
obrigando-nos a análises mais cuidadas das entradas anteriores para determinar
quem é o orador.

Nome interno
    ``mp_cont``, ``president_cont``, ``secretary_cont``, ``pm_cont``,
    ``minister_cont``, ``statesecretary_cont``
Nome completo
    Continuação

Tem a palavra
-------------
Usado quando o presidente dá a palavra a um deputado. Útil para determinar com
certeza a identidade do orador seguinte.

Exemplo
    A Sr.ª **Presidente**: —  Para uma declaração de voto, tem a palavra o Sr.
    Deputado Alfredo Nenhures.
Nome interno
    ``???``
Nome completo
    Presidente (tem a palavra)

============
Interrupções
============

Protestos
---------

O(s) autor(es) do protesto podem ser identificados removendo “Protesto[s]
d[ao]s? ” e o ponto final.

Nome interno
    ``protest``
Nome completo
    Protestos
Regex
    :regexp:`^Protesto.*.`

Aplausos
--------
Exemplo
    *Aplausos do PSN e do PPM.*
Nome interno
    ``applause``
Nome completo
    Aplausos

Risos
-----
Exemplo
    *Risos do PSN.*
Nome interno
    ``laughter``
Nome completo
    Risos

==========
Indicações
==========

Notas da redacção relevantes para a descrição da sessão.

Voto
----
Cada voto pode ser facilmente reconhecido por começar sempre com “Submetido/a(s)
à votação”. O que está a ser votado pode ser determinado lendo a intervenção
anterior do presidente.

Exemplo
    *Submetido à votação, foi aprovado por unanimidade.*
Nome interno
    ``vote``
Nome completo
    Voto
Regex
    `^Submetid[oa]s? à votação,.*`

Pausa
-----
Exemplo
    *Pausa.*
Nome interno
    ``pause``
Nome completo
    Pausa

Mudança de presidente
---------------------
"Entretanto, assumiu a presidência..."

Nome interno
    ``president_switch``
Nome completo
    Mudança de presidente

Hora
----
Nota sobre a hora actual: “Eram 15 horas e 30 minutos”

Nome interno
    ``time``
Nome completo
    Hora

Sumário
-------
Surge no início da transcrição.

Nome interno
    ``summary``
Nome completo
    Sumário

Outras notas
------------
Exemplos
    *Procedeu-se à votação.* (encontrado na eleição do Presidente da AR)
Nome interno
    ``note``
Nome completo
    Nota

Lista de presenças
------------------
Deputados presentes (no início), atrasados, em missão parlamentar, ausentes (no final).

Não utilizado. Todas as listas desde 1991 estão disponíveis no `site do Parlamento
<http://www.parlamento.pt/DeputadoGP/Paginas/reunioesplenarias.aspx>`_, pelo que
removemos esta informação durante a conversão das transcrições.

========================
Outras não implementadas
========================

Documento
---------
Diz respeito a actas e textos de propostas lidos na sessão Surgem normalmente
depois de “É o seguinte:”, ou “do seguinte teor:”

Nome interno
    ``document``
Nome completo
    Documento

Declaração de voto
------------------
Presentes no final da transcrição. Difíceis de processar automaticamente.

Nome interno
    ``vote_statement``
Nome completo
    Declaração de voto


