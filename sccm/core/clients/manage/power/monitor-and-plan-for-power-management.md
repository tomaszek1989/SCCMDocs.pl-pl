---
title: "Monitorizar e planear a gestão de energia | Microsoft Docs"
description: "Saiba como monitorizar e planear a gestão no System Center Configuration Manager de energia."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 507bf676-2679-4e4d-8831-3ffc9cf8557e
caps.latest.revision: "6"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: b308329635400438cebc4935efe79b46e607fd58
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-monitor-and-plan-for-power-management-in-system-center-configuration-manager"></a>Como monitorizar e planear a gestão de energia no System Center Configuration Manager

*Aplica-se a: O System Center Configuration Manager (ramo atual)*

Utilize as seguintes informações para o ajudar a monitorizar e planear a gestão de energia no System Center Configuration Manager.  

##  <a name="BKMK_How_to_use_reports"></a> Como utilizar relatórios para a gestão de energia  
 Gestão de energia no Configuration Manager inclui vários relatórios para o ajudar a analisar as definições de energia de computador e o consumo de energia na sua organização. Os relatórios também podem ser utilizados para ajudar a resolver problemas.  

 Antes de poder utilizar os relatórios de gestão de energia, é necessário configurá-los na sua hierarquia. Para obter mais informações sobre os relatórios no Configuration Manager, consulte [relatórios no System Center Configuration Manager](../../../../core/servers/manage/reporting.md).  

> [!NOTE]  
>  Informações de gestão de energia utilizadas pelos relatórios diários são mantidas na base de dados do site do Configuration Manager 31 dias.  
>           Informações de gestão de energia utilizadas pelos relatórios diários são mantidas na base de dados do site do Configuration Manager durante 13 meses.  
>   
>  Quando executa relatórios durante as fases de monitorização, planeamento e compatibilidade de gestão de energia, guarde ou exporte os resultados de quaisquer relatórios para o qual pretende manter os dados para comparação posterior caso sejam posteriores removido pelo Configuration Manager.  

## <a name="list-of-power-management-reports"></a>Lista de relatórios de gestão de energia  
 A lista seguinte fornece detalhes sobre os relatórios de gestão de energia que estão disponíveis no Configuration Manager.  

> [!NOTE]  
>  Os relatórios de gestão de energia apresentam o número de computadores físicos e o número de computadores virtuais numa coleção selecionada. No entanto, são apresentadas apenas as informações de gestão de energia de computadores físicos nos relatórios de gestão de energia.  

###  <a name="BKMK_Activity"></a> Relatório Atividade do Computador  
 O relatório **Atividade do Computador** mostra um gráfico que apresenta a seguinte atividade numa coleção especificada e num período de tempo especificado:  

-   **Computador Ativado** – O computador foi ativado.  

-   **Monitorização Ativada** – A monitorização foi ativada.  

-   **Utilizador Ativo** – Foi detetada atividade no rato do computador, no teclado do computador ou numa ligação de Ambiente de Trabalho Remoto para o computador  

 Este relatório é utilizado durante as fases de monitorização, planeamento e imposição para o ajudar a compreender o alinhamento entre a atividade do computador, a atividade de monitorização e a atividade do utilizador durante um período de 24 horas. Se executar o relatório sobre um determinado número de dias, os dados são agregados durante este período. Este relatório pode ajudá-lo a determinar as horas comerciais comuns (pico) e não comerciais (fora de pico) de uma coleção selecionada para o ajudar a decidir quando deve aplicar esquemas de gestão de energia configurados.  

 O gráfico mostra períodos de tempo em que um computador pode ser ativado, mas não existe nenhuma atividade do utilizador. Considere aplicar as definições de energia mais restritivas durante estas horas para poupar nos custos de energia dos computadores que estão ativados, mas não estão a ser utilizados. Um computador é contabilizado como estando ativo se tiver ocorrido atividade de monitorização, do computador ou do utilizador por um minuto ou mais de uma hora apresentada no gráfico. Se um computador não estiver a comunicar dados de gestão de energia, este não será incluído no relatório **Atividade do Computador** .  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Data de início**|Na lista pendente, selecione a data de início para este relatório.|  
|**Data de fim (Opcional)**|Na lista pendente, selecione uma data de fim opcional para este relatório.|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para utilizar para este relatório.|  
|**Tipo de dispositivo**|Na lista pendente, selecione o tipo de computador para o qual pretende um relatório. Os valores válidos são **todos os** (computadores de secretária e portáteis), **ambiente de trabalho** (computadores de secretária apenas), e **portátil** (apenas de computadores portáteis).|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Este relatório não tem parâmetros ocultados que pode definir.  

#### <a name="report-links"></a>Ligações de relatórios  
 Se não for especificado um valor para a **Data de fim (opcional)** , este relatório contém uma ligação para o relatório seguinte que fornece informações adicionais.  

|Nome do Relatório|Detalhes|  
|-----------------|-------------|  
|**Detalhes de Atividade do Computador**|Clique na ligação **Clique para obter informações detalhadas** para ver uma lista de computadores ativos, inativos e sem relatórios para a data especificada.<br /><br /> Para obter mais informações, consulte [Computer Activity Details Report](#BKMK_Activity_Details) neste tópico.|  

###  <a name="BKMK_Comp_Activity_by_computer"></a> Relatório Atividade do Computador por Computador  
 O relatório **Atividade do Computador por Computador** mostra um gráfico que apresenta a seguinte atividade num computador especificado e numa data especificada:  

-   **Computador Ativado** – O computador foi ativado.  

-   **Monitorização Ativada** – A monitorização foi ativada.  

-   **Utilizador Ativo** –  foi detetada atividade no rato do computador, no teclado do computador ou numa ligação de Ambiente de Trabalho Remoto para o computador.  

 Este relatório pode ser executado de forma independente ou denominado pelo relatório **Detalhes de Atividade do Computador** .  

> [!NOTE]  
>  As informações sobre a atividade do computador são recolhidas de computadores cliente durante o inventário de hardware. Consoante o tempo em que o inventário de hardware é executado, a atividade pode ser recolhida durante um esquema de energia sem pico ou de pico aplicado.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Data de relatório**|Na lista pendente, selecione a data para este relatório.|  
|**Nome do computador**|Introduza um nome de computador para o qual pretende um relatório.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Este relatório não tem parâmetros ocultados que pode definir.  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório contém ligações para o relatório seguinte que fornece mais informações sobre o item selecionado.  

|Nome do Relatório|Detalhes|  
|-----------------|-------------|  
|**Detalhes do Computador**|Clique na ligação **Clique para obter informações detalhadas** para ver as capacidades de energia, as definições de energia e os esquemas de energia aplicados ao computador selecionado.|  

###  <a name="BKMK_Activity_Details"></a> Computer Activity Details report  
 O relatório **Detalhes de Atividade do Computador** apresenta uma lista de computadores ativos ou inativos com as respetivas capacidades de suspensão e reativação. Este relatório é denominado por [Computer Activity Report](#BKMK_Activity) e não foi concebido para ser executado diretamente pelo administrador do site.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para utilizar para este relatório.|  
|**Data de relatório**|Na lista pendente, selecione a data a utilizar para este relatório.|  
|**Hora do relatório**|Na lista pendente, selecione a hora a contar da data especificada na qual pretende executar este relatório. Os valores válidos são entre as **12:00** e as **23:00**.|  
|**Estado do computador**|Na lista pendente, selecione o estado do computador no qual pretende executar este relatório. Os valores válidos são **todos os** (computadores que foram ativados ou desativado), **no** (computadores que foram ativados), e **desativar** (computadores que foram ativados desativado, no modo de suspensão, ou em hibernação). Estes valores apenas são devolvidos para escolhida período de relatório.|  
|**Tipo de dispositivo**|Na lista pendente, selecione o tipo de computador para o qual pretende um relatório. Os valores válidos são **todos os** (computadores de secretária e portáteis), **ambiente de trabalho** (computadores de secretária apenas), e **portátil** (apenas de computadores portáteis). Estes valores apenas são devolvidos para escolhida período de relatório.|  
|**Capacidade de suspensão**|Na lista pendente, selecione se pretende apresentar computadores com capacidade de suspensão no relatório. Os valores válidos são **todos os** (ambos os computadores compatíveis com e sem capacidade de suspensão), **não** (computadores sem capacidade de suspensão), e **Sim** (computadores que têm capacidade de suspensão).|  
|**Capacidade de reativação a partir da suspensão**|Na lista pendente, selecione se pretende apresentar computadores com capacidade de reativação a partir da suspensão no relatório. Os valores válidos são **todos os** (ambos os computadores compatíveis com e sem capacidade de reativação da suspensão), **não** (computadores sem capacidade de reativação da suspensão), e **Sim** (computadores que são capazes de reativação da suspensão).|  
|**Esquema de energia**|Na lista pendente, selecione os tipos de esquema de energia que pretende apresentar no relatório. Os valores válidos são **todos os** (computadores que não tem nenhum energia esquemas de gestão aplicados, computadores que têm um esquema de gestão de energia aplicado; computadores excluídos da gestão de energia), **não especificado** (computadores que não têm um esquema de gestão de energia aplicado), **definidas** (computadores que têm um esquema de gestão de energia aplicado), e **excluídas** (computadores que foram excluídos da gestão de energia).|  
|**Sistema operativo**|Na lista pendente, selecione os sistemas operativos dos computadores que pretende apresentar no relatório ou selecione **Todos** para apresentar todos os sistemas operativos.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Este relatório não tem parâmetros ocultados que pode definir.  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório contém ligações para o relatório seguinte que fornece mais informações sobre o item selecionado.  

|Nome do Relatório|Detalhes|  
|-----------------|-------------|  
|**Atividade do Computador por Computador**|Clique num nome de computador para ver a atividade específica para esse computador através de uma período de relatório de escolhida. Estas atividades incluem **computador em** (o computador foi ativado?), **monitorizar no** (o monitor foi ativado?), e **utilizador ativa** (foi detetada atividade do rato do computador, teclado ou uma ligação de ambiente de trabalho remoto).<br /><br /> Para obter mais informações, consulte [Computer Activity by Computer Report](#BKMK_Comp_Activity_by_computer) neste tópico.|  

###  <a name="BKMK_Computer_Details"></a> Relatório Detalhes do Computador  
 O relatório **Detalhes do Computador** mostra informações detalhadas sobre as funcionalidades de energia, definições de energia e esquemas de energia aplicados a um computador especificado. Este relatório é denominado pelos relatórios **Atividade do Computador por Computador** , **Computadores com Vários Esquemas de Energia** , **Capacidades de Energia** e **Detalhes das Definições de Energia** . Não foi concebido para ser executado diretamente pelo administrador do site.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Nome do computador**|Introduza um nome de computador para o qual pretende um relatório.|  
|**Modo de energia**|Na lista pendente, selecione o tipo de definições de energia que pretende apresentar nos resultados do relatório. Selecione **Ligado** para ver as definições de energia configuradas quando o computador está ligado e **Com Bateria** para ver as definições de energia configuradas quando o computador está em execução com energia da bateria.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Este relatório não tem parâmetros ocultados que pode definir.  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório não está associado a quaisquer outros relatórios de gestão de energia.  

###  <a name="BKMK_Not_Reporting"></a> Relatório Computador Não Reporta Detalhes  
 O relatório **Computador Não Comunica Detalhes** apresenta uma lista de computadores numa coleção especificada que não comunicaram qualquer atividade de energia numa data e hora especificadas. Este relatório é denominado por **Computer Activity Report** e não foi concebido para ser executado diretamente pelo administrador do site.  

> [!NOTE]  
>  Os computadores comunicam informações de gestão de energia como parte da respetiva agenda de inventário de hardware. Antes de considerar que um computador não efetua relatórios, certifique-se de que este comunicou o inventário de hardware.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para utilizar para este relatório.|  
|**Data de relatório**|Na lista pendente, selecione a data para este relatório.|  
|**Hora do relatório**|Na lista pendente, selecione a hora a contar da data especificada na qual pretende executar este relatório. Os valores válidos são entre as **12:00** e as **23:00**.|  
|**Tipo de dispositivo**|Na lista pendente, selecione o tipo de computador para o qual pretende um relatório. Os valores válidos são **todos os** (computadores de secretária e portáteis), **ambiente de trabalho** (computadores de secretária apenas), e **portátil** (apenas de computadores portáteis). Estes valores apenas são devolvidos para escolhida período de relatório.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Este relatório não tem parâmetros ocultados que pode definir.  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório não está associado a quaisquer outros relatórios de gestão de energia.  

###  <a name="BKMK_Excluded"></a> Computadores Excluídos  
 O **computadores excluídos** relatório apresenta uma lista de computadores numa coleção especificada que foram excluídos da gestão de energia do Configuration Manager.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Recolha**|Na lista pendente, selecione uma coleção para este relatório.|  
|**Motivo**|Na lista pendente, selecione por que motivo os computadores foram excluídos da gestão de energia. Pode visualizar **todos os** (todos os excluídos computadores), **excluídos pelo administrador** (apenas computadores que foram excluídos por um utilizador administrativo), e **excluídos pelo utilizador** (apenas computadores que foram excluídos por um utilizador do Centro de Software).|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Este relatório não tem parâmetros ocultados que pode definir.  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório contém ligações para o relatório seguinte que fornece mais informações sobre o item selecionado.  

|Nome do Relatório|Detalhes|  
|-----------------|-------------|  
|**Detalhes do Computador de Energia**|Clique no nome do computador para ver as capacidades de energia, as definições de energia e esquemas de energia aplicados para o computador selecionado.<br /><br /> Para obter mais informações, consulte [Computer Details Report](#BKMK_Computer_Details) neste tópico.|  

###  <a name="BKMK_Multiple"></a> Computadores com Vários Esquemas de Energia  
 O relatório **Computadores com Vários Esquemas de Energia** apresenta uma lista de computadores que são membros de várias coleções, cada um aplicando diferentes esquemas de energia. Para cada computador com as definições de energia potencialmente em conflito, o relatório apresenta o nome do computador e os esquemas de energia a serem aplicados para cada coleção de que o computador é membro.  

> [!IMPORTANT]  
>  Se um computador for um membro de várias coleções, em que cada coleção tem diferentes esquemas de energia, em seguida, o esquema de energia menos restritivo será aplicado.  
>   
>  Se um computador for um membro de várias coleções, em que cada coleção tem horas de reativação diferente, será utilizada a hora mais próxima da meia-noite.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para este relatório.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Este relatório não tem parâmetros ocultados que pode definir.  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório contém ligações para o relatório seguinte que fornece mais informações sobre o item selecionado.  

|Nome do Relatório|Detalhes|  
|-----------------|-------------|  
|**Detalhes do Computador de Energia**|Clique no nome do computador para ver as capacidades de energia, as definições de energia e esquemas de energia aplicados para o computador selecionado.<br /><br /> Para obter mais informações, consulte [Computer Details Report](#BKMK_Computer_Details) neste tópico.|  

###  <a name="BKMK_Consumption"></a> Relatório Consumo de Energia  
 O relatório **Consumo de Energia** apresenta as seguintes informações:  

-   Um gráfico que mostra o consumo de energia mensal total de computadores em kiloWatt por hora (kWh) na coleção especificada para o período de tempo especificado.  

-   Um gráfico que mostra o consumo médio de energia em kiloWatt por hora (kWh) de cada computador na coleção especificada para o período de tempo especificado.  

-   Uma tabela que mostra o consumo de energia mensal total de computadores em kiloWatt por hora (kWh) e o consumo médio de energia de computadores na coleção especificada para o período de tempo especificado.  

 Estas informações podem ser utilizadas para ajudar a compreender as tendências de consumo de energia no seu ambiente. Depois de aplicar um esquema de energia aos computadores na coleção selecionada, deve diminuir o consumo de energia dos computadores.  

> [!NOTE]  
>  Se adicionar ou remover membros na coleção depois de ter aplicado um esquema de energia, isto irá afetar os resultados apresentados pelo relatório **Consumo de Energia** e poderá dificultar a comparação dos resultados da fase de monitorização e de planeamento e a fase de imposição.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Data de início**|Na lista pendente, selecione uma data de início para este relatório.|  
|**Data de fim**|Na lista pendente, selecione uma data de fim para este relatório.|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para este relatório.|  
|**Tipo de dispositivo**|Na lista pendente, selecione o tipo de computador para o qual pretende um relatório. Os valores válidos são **todos os** (computadores de secretária e portáteis), **ambiente de trabalho** (computadores de secretária apenas), e **portátil** (apenas de computadores portáteis). Estes valores apenas são devolvidos para escolhida período de relatório.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Os seguintes parâmetros ocultados podem ser, opcionalmente, especificados para alterar o comportamento deste relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Computador de secretária ligado**|Especifique o consumo de energia de um computador de secretária quando está ligado. O valor predefinido é **0,07** kW por hora.|  
|**Computador portátil ligado**|Especifique o consumo de energia de um computador portátil quando está ligado. O valor predefinido é **0,02** kW por hora.|  
|**Computador de secretária suspenso**|Especifique o consumo de energia de um computador de secretária que entrou em suspensão. O valor predefinido é **0,003** kW por hora.|  
|**Computador portátil suspenso**|Especifique o consumo de energia de um computador portátil que entrou em suspensão. O valor predefinido é **0,001** kW por hora.|  
|**Computador de secretária desligado**|Especifique o consumo de energia de um computador de secretária quando está desligado. O valor predefinido é **0** kW por hora.|  
|**Computador portátil desligado**|Especifique o consumo de energia de um computador portátil quando está desligado. O valor predefinido é **0** kW por hora.|  
|**Monitor de secretária ligado**|Especifique o consumo de energia de um monitor de computador de secretária quando está ligado. O valor predefinido é **0,028** kW por hora.|  
|**Monitor de portátil ligado**|Especifique o consumo de energia de um monitor de computador portátil quando está ligado. O valor predefinido é **0** kW por hora.|  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório não está associado a quaisquer outros relatórios de gestão de energia.  

###  <a name="BKMK_Consumption_by_Day"></a> Relatório Consumo de Energia por Dia  
 O relatório **Consumo de Energia por Dia** apresenta as seguintes informações:  

-   Um gráfico que mostra o consumo de energia diário total de computadores em kiloWatt por hora (kWh) na coleção especificada dos últimos 31 dias.  

-   Um gráfico que mostra o consumo médio diário de energia em kiloWatt por hora (kWh) de cada computador na coleção especificada dos últimos 31 dias.  

-   Uma tabela que mostra o consumo de energia diário total de computadores em kiloWatt por hora (kWh) e o consumo médio diário de energia de computadores na coleção especificada dos últimos 31 dias.  

 Estas informações podem ser utilizadas para ajudar a compreender as tendências de consumo de energia no seu ambiente. Depois de aplicar um esquema de energia aos computadores na coleção selecionada, deve diminuir o consumo de energia dos computadores.  

> [!NOTE]  
>  Se adicionar ou remover membros na coleção depois de ter aplicado um esquema de energia, isto irá afetar os resultados apresentados pelo relatório **Consumo de Energia** e poderá dificultar a comparação dos resultados da fase de monitorização e de planeamento e a fase de imposição.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Recolha**|Na lista pendente, selecione uma coleção para este relatório.|  
|**Device Type**|Na lista pendente, selecione o tipo de computador para o qual pretende um relatório. Os valores válidos são **todos os** (computadores de secretária e portáteis), **ambiente de trabalho** (computadores de secretária apenas), e **portátil** (apenas de computadores portáteis). Estes valores apenas são devolvidos para escolhida período de relatório.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Os seguintes parâmetros ocultados podem ser, opcionalmente, especificados para alterar o comportamento deste relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Computador de secretária ligado**|Especifique o consumo de energia de um computador de secretária quando está ligado. O valor predefinido é **0,07** kW por hora.|  
|**Computador portátil ligado**|Especifique o consumo de energia de um computador portátil quando está ligado. O valor predefinido é **0,02** kW por hora.|  
|**Computador de secretária suspenso**|Especifique o consumo de energia de um computador de secretária que entrou em suspensão. O valor predefinido é **0,003** kW por hora.|  
|**Computador portátil suspenso**|Especifique o consumo de energia de um computador portátil que entrou em suspensão. O valor predefinido é **0,001** kW por hora.|  
|**Computador de secretária desligado**|Especifique o consumo de energia de um computador de secretária quando está desligado. O valor predefinido é **0** kW por hora.|  
|**Computador portátil desligado**|Especifique o consumo de energia de um computador portátil quando está desligado. O valor predefinido é **0** kW por hora.|  
|**Monitor de secretária ligado**|Especifique o consumo de energia de um monitor de computador de secretária quando está ligado. O valor predefinido é **0,028** kW por hora.|  
|**Monitor de portátil ligado**|Especifique o consumo de energia de um monitor de computador portátil quando está ligado. O valor predefinido é **0** kW por hora.|  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório não está associado a quaisquer outros relatórios de gestão de energia.  

###  <a name="BKMK_Cost"></a> Relatório Custo da Energia  
 O relatório **Custo da Energia** apresenta as seguintes informações:  

-   Um gráfico que mostra o custo da energia mensal total de computadores na coleção especificada para o período de tempo especificado.  

-   Um gráfico que mostra o custo da energia mensal médio de cada computador na coleção especificada para o período de tempo especificado.  

-   Uma tabela que mostra o custo da energia mensal total e o custo da energia médio mensal para computadores da coleção especificada nos últimos 31 dias.  

 Estas informações podem ser utilizadas para ajudar a compreender as tendências de custo de energia no seu ambiente. Depois de aplicar um esquema de energia aos computadores na coleção selecionada, deve diminuir o custo de energia dos computadores.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Data de início**|Na lista pendente, selecione uma data de início para este relatório.|  
|**Data de fim**|Na lista pendente, selecione uma data de fim para este relatório.|  
|**Custo de KwH**|Especifique o custo por kWh de eletricidade. O valor predefinido é **0,09**.<br /><br /> Pode modificar a unidade de moeda utilizada por este relatório na secção de parâmetros ocultos.|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para utilizar para este relatório.|  
|**Tipo de dispositivo**|Na lista pendente, selecione o tipo de computador para o qual pretende um relatório. Os valores válidos são **todos os** (computadores de secretária e portáteis), **ambiente de trabalho** (computadores de secretária apenas), e **portátil** (apenas de computadores portáteis). Estes valores apenas são devolvidos para escolhida período de relatório.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Os seguintes parâmetros ocultados podem ser, opcionalmente, especificados para alterar o comportamento deste relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Computador de secretária ligado**|Especifique o consumo de energia de um computador de secretária quando está ligado. O valor predefinido é **0,07** kW por hora.|  
|**Computador portátil ligado**|Especifique o consumo de energia de um computador portátil quando está ligado. O valor predefinido é **0,02** kW por hora.|  
|**Computador de secretária suspenso**|Especifique o consumo de energia de um computador de secretária que entrou em suspensão. O valor predefinido é **0,003** kW por hora.|  
|**Computador portátil suspenso**|Especifique o consumo de energia de um computador portátil que entrou em suspensão. O valor predefinido é **0,001** kW por hora.|  
|**Computador de secretária desligado**|Especifique o consumo de energia de um computador de secretária quando está desligado. O valor predefinido é **0** kW por hora.|  
|**Computador portátil desligado**|Especifique o consumo de energia de um computador portátil quando está desligado. O valor predefinido é **0** kW por hora.|  
|**Monitor de secretária ligado**|Especifique o consumo de energia de um monitor de computador de secretária quando está ligado. O valor predefinido é **0,028** kW por hora.|  
|**Monitor de portátil ligado**|Especifique o consumo de energia de um monitor de computador portátil quando está ligado. O valor predefinido é **0** kW por hora.|  
|**Moeda**|Especifique a etiqueta de moeda a utilizar para este relatório. O valor predefinido é **USD ($)**.|  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório não está associado a quaisquer outros relatórios de gestão de energia.  

###  <a name="BKMK_Cost_by_Day"></a> Relatório Custo da Energia por Dia  
 O relatório **Custo da Energia por Dia** apresenta as seguintes informações:  

-   Um gráfico que mostra o custo da energia diário total de computadores na coleção especificada dos últimos 31 dias.  

-   Um gráfico que mostra o custo da energia médio diário de cada computador na coleção especificada dos últimos 31 dias.  

-   Uma tabela que mostra o custo de energia diário total e o custo de energia médio diário para computadores da coleção especificada nos últimos 31 dias.  

 Estas informações podem ser utilizadas para ajudar a compreender as tendências de custo de energia no seu ambiente. Depois de aplicar um esquema de energia aos computadores na coleção selecionada, deve diminuir o custo de energia dos computadores.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para utilizar para este relatório.|  
|**Tipo de dispositivo**|Na lista pendente, selecione o tipo de computador para o qual pretende um relatório. Os valores válidos são **todos os** (computadores de secretária e portáteis), **ambiente de trabalho** (computadores de secretária apenas), e **portátil** (apenas de computadores portáteis). Estes valores apenas são devolvidos para escolhida período de relatório.|  
|**Custo de KwH**|Especifique o custo por kWh de eletricidade. O valor predefinido é **0,09**.<br /><br /> Pode modificar a unidade de moeda utilizada por este relatório na secção de parâmetros ocultos.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Os seguintes parâmetros ocultados podem ser, opcionalmente, especificados para alterar o comportamento deste relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Computador de secretária ligado**|Especifique o consumo de energia de um computador de secretária quando está ligado. O valor predefinido é **0,07** kW por hora.|  
|**Computador portátil ligado**|Especifique o consumo de energia de um computador portátil quando está ligado. O valor predefinido é **0,02** kW por hora.|  
|**Computador de secretária suspenso**|Especifique o consumo de energia de um computador de secretária que entrou em suspensão. O valor predefinido é **0,003** kW por hora.|  
|**Computador portátil suspenso**|Especifique o consumo de energia de um computador portátil que entrou em suspensão. O valor predefinido é **0,001** kW por hora.|  
|**Computador de secretária desligado**|Especifique o consumo de energia de um computador de secretária quando está desligado. O valor predefinido é **0** kW por hora.|  
|**Computador portátil desligado**|Especifique o consumo de energia de um computador portátil quando está desligado. O valor predefinido é **0** kW por hora.|  
|**Monitor de secretária ligado**|Especifique o consumo de energia de um monitor de computador de secretária quando está ligado. O valor predefinido é **0,028** kW por hora.|  
|**Monitor de portátil ligado**|Especifique o consumo de energia de um monitor de computador portátil quando está ligado. O valor predefinido é **0** kW por hora.|  
|**Moeda**|Especifique a etiqueta de moeda a utilizar para este relatório. O valor predefinido é **USD ($)**.|  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório não está associado a quaisquer outros relatórios de gestão de energia.  

###  <a name="BKMK_Environmental_Impact"></a> Relatório Impacto Ambiental  
 O relatório **Impacto Ambiental** apresenta as seguintes informações:  

-   Um gráfico que mostra o CO2 mensal total gerado (em toneladas) para computadores na coleção especificada para o período de tempo especificado.  

-   Um gráfico que mostra o CO2 médio mensal gerado (em toneladas) de cada computador na coleção especificada para o período de tempo especificado.  

-   Uma tabela que mostra o CO2 mensal total gerado e o CO2 médio mensal gerado de computadores na coleção especificada para o período de tempo especificado.  

 O **impacto ambiental** relatório calcula a quantidade de CO2 gerado (em toneladas) utilizando a hora em que um computador ou monitor foi ligado num período de 24 horas.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Data de início do relatório**|Na lista pendente, selecione uma data de início para este relatório.|  
|**Data de fim do relatório**|Na lista pendente, selecione uma data de fim para este relatório.|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para este relatório.|  
|**Tipo de dispositivo**|Na lista pendente, selecione o tipo de computador para o qual pretende um relatório. Os valores válidos são **todos os** (computadores de secretária e portáteis), **ambiente de trabalho** (computadores de secretária apenas), e **portátil** (apenas de computadores portáteis). Estes valores apenas são devolvidos para escolhida período de relatório.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Os seguintes parâmetros ocultados podem ser, opcionalmente, especificados para alterar o comportamento deste relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Computador de secretária ligado**|Especifique o consumo de energia de um computador de secretária quando está ligado. O valor predefinido é **0,07** kW por hora.|  
|**Computador portátil ligado**|Especifique o consumo de energia de um computador portátil quando está ligado. O valor predefinido é **0,02** kW por hora.|  
|**Computador de secretária suspenso**|Especifique o consumo de energia de um computador de secretária que entrou em suspensão. O valor predefinido é **0,003** kW por hora.|  
|**Computador portátil suspenso**|Especifique o consumo de energia de um computador portátil que entrou em suspensão. O valor predefinido é **0,001** kW por hora.|  
|**Computador de secretária desligado**|Especifique o consumo de energia de um computador de secretária quando está desligado. O valor predefinido é **0** kW por hora.|  
|**Computador portátil desligado**|Especifique o consumo de energia de um computador portátil quando está desligado. O valor predefinido é **0** kW por hora.|  
|**Monitor de secretária ligado**|Especifique o consumo de energia de um monitor de computador de secretária quando está ligado. O valor predefinido é **0,028** kW por hora.|  
|**Monitor de portátil ligado**|Especifique o consumo de energia de um monitor de computador portátil quando está ligado. O valor predefinido é **0** kW por hora.|  
|**Fator de carbono (toneladas/kWh)** (CO2Mix)|Especifique o valor do fator de carbono (em toneladas/kWh) que, normalmente, pode obter a partir da sua empresa de energia. O valor predefinido é **0,0015** toneladas por kWh.|  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório não está associado a quaisquer outros relatórios de gestão de energia.  

###  <a name="BKMK_Environmental_Impact_by_Day"></a> Relatório Impacto Ambiental por Dia  
 O relatório **Impacto Ambiental por Dia** apresenta as seguintes informações:  

-   Um gráfico que mostra o CO2 diário total gerado (em toneladas) de computadores na coleção especificada dos últimos 31 dias.  

-   Um gráfico que mostra o CO2 médio diário gerado (em toneladas) de cada computador na coleção especificada dos últimos 31 dias.  

-   Uma tabela que mostra o CO2 diário total gerado e o média diário CO2 gerado de computadores na coleção especificada dos últimos 31 dias.  

 O **impacto ambiental por dia** relatório calcula a quantidade de CO2 gerado (em toneladas) utilizando a hora em que um computador ou monitor foi ligado num período de 24 horas.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para este relatório.|  
|**Tipo de dispositivo**|Na lista pendente, selecione o tipo de computador para o qual pretende um relatório. Os valores válidos são **todos os** (computadores de secretária e portáteis), **ambiente de trabalho** (computadores de secretária apenas), e **portátil** (apenas de computadores portáteis). Estes valores apenas são devolvidos para escolhida período de relatório.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Os seguintes parâmetros ocultados podem ser, opcionalmente, especificados para alterar o comportamento deste relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Computador de secretária ligado**|Especifique o consumo de energia de um computador de secretária quando está ligado. O valor predefinido é **0,07** kWh.|  
|**Computador portátil ligado**|Especifique o consumo de energia de um computador portátil quando está ligado. O valor predefinido é **0,02** kWh.|  
|**Computador de secretária desligado**|Especifique o consumo de energia de um computador de secretária quando está desligado. O valor predefinido é **0** kWh.|  
|**Computador portátil desligado**|Especifique o consumo de energia de um computador portátil quando está desligado. O valor predefinido é **0** kWh.|  
|**Computador de secretária suspenso**|Especifique o consumo de energia de um computador de secretária que entrou em suspensão. O valor predefinido é **0,003** kWh.|  
|**Computador portátil suspenso**|Especifique o consumo de energia de um computador portátil que entrou em suspensão. O valor predefinido é **0,001** kWh.|  
|**Monitor de secretária ligado**|Especifique o consumo de energia de um monitor de computador de secretária quando está ligado. O valor predefinido é **0,028** kWh.|  
|**Monitor de portátil ligado**|Especifique o consumo de energia de um monitor de computador portátil quando está ligado. O valor predefinido é **0** kWh.|  
|**Fator de carbono (toneladas/kWh)** (CO2Mix)|Especifique um valor do fator de carbono (em toneladas/kWh) que, normalmente, pode obter a partir da sua empresa de energia. O valor predefinido é **0,0015** toneladas por kWh.|  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório não está associado a quaisquer outros relatórios de gestão de energia.  

###  <a name="BKMK_Insomnia_Computer_Details"></a> Relatório Detalhes do Computador com Insónia  
 O relatório **Detalhes do Computador com Insónia** apresenta uma lista de computadores que não entraram em modo de suspensão ou hibernação por um motivo específico durante um período de tempo especificado. Este relatório é denominado por **Relatório de Insónia** e não foi concebido para ser executado diretamente pelo administrador do site.  

 O **Relatório de Insónia** apresenta computadores como **Sem capacidade de suspensão** quando estes não têm capacidade de suspensão e foram ligados durante o intervalo completo de relatório especificado. O relatório apresenta computadores como **Sem capacidade de hibernação** quando estes não têm capacidade de hibernação e foram ligados durante o intervalo completo de relatório especificado.  

> [!NOTE]  
>  A gestão de energia só pode recolher as causas que impediram que os computadores introduzissem o modo de suspensão ou hibernação de computadores com o Windows 7 ou o Windows Server 2008 R2.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para utilizar para este relatório.|  
|**Intervalo de relatório (dias)**|Especifique o número de dias do relatório. O valor predefinido é **7** dias.|  
|**Causa da Insónia**|Na lista pendente, selecione uma das causas que podem impedir que os computadores introduzam o modo de suspensão ou hibernação.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Este relatório não tem parâmetros ocultados que pode definir.  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório contém ligações para o relatório seguinte que fornece mais informações sobre o item selecionado.  

|Nome do Relatório|Detalhes|  
|-----------------|-------------|  
|**Detalhes do Computador**|Clique na ligação **Clique para obter informações detalhadas** para ver as capacidades de energia, as definições de energia e os esquemas de energia aplicados ao computador selecionado.<br /><br /> Para obter mais informações, consulte [Computer Details Report](#BKMK_Computer_Details) neste tópico.|  

###  <a name="BKMK_Insomnia"></a> Insomnia report  
 O **Relatório Insónia** mostra uma lista de causas comuns que impedem os computadores de entrarem em suspensão ou hibernação e o número de computadores que foram afetados por cada causa durante um período de tempo especificado. Existe um número de causas que poderá impedir que um computador entre em suspensão ou hibernação, tal como a execução de um processo no computador, uma sessão aberta de Ambiente de Trabalho Remoto ou o computador sem capacidade de suspensão ou hibernação. A partir deste relatório, pode abrir o relatório **Detalhes do Computador com Insónia** que apresenta uma lista dos computadores afetados por cada causa dos computadores que não entram em modo de suspensão ou hibernação.  

 O relatório Insónia de Energia apresenta computadores como **Sem capacidade de suspensão** quando estes não têm capacidade de suspensão e foram ligados durante o intervalo completo de relatório especificado. O relatório apresenta computadores como **Sem capacidade de hibernação** quando estes não têm capacidade de hibernação e foram ligados durante o intervalo completo de relatório especificado.  

> [!NOTE]  
>  A gestão de energia só pode recolher as causas que impediram que os computadores introduzissem o modo de suspensão ou hibernação de computadores com o Windows 7 ou o Windows Server 2008 R2.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para utilizar para este relatório.|  
|**Intervalo de relatório (dias)**|Especifique o número de dias do relatório. O valor predefinido é **7** dias. O valor máximo é **365** dias. Especifique **0** para executar o relatório hoje.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Este relatório não tem parâmetros ocultados que pode definir.  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório contém ligações para o relatório seguinte que fornece mais informações sobre o item selecionado.  

|Nome do Relatório|Detalhes|  
|-----------------|-------------|  
|**Detalhes do Computador com Insónia**|Clique num número na coluna **Computadores Afetados** para ver uma lista dos computadores que não conseguiram entrar em modo de suspensão ou hibernação devido à causa selecionada.<br /><br /> Para obter mais informações, consulte [Insomnia Computer Details Report](#BKMK_Insomnia_Computer_Details) neste tópico.|  

###  <a name="BKMK_Capabilites"></a> Relatório Capacidades de Energia  
 O relatório **Capacidades de Energia** mostra as funcionalidades de hardware de gestão de energia dos computadores na coleção especificada. Este relatório é geralmente utilizado na fase de monitorização de gestão de energia para determinar as capacidades de gestão de energia dos computadores na sua organização. As informações apresentadas no relatório podem então ser utilizadas para criar coleções de computadores para aplicar os esquemas de energia ou para excluir da gestão de energia. As capacidades de gestão de energia apresentadas neste relatório são:  

-   **Com Capacidade de Suspensão** - Indica se o computador tem a capacidade de entrar em suspensão se estiver configurado para tal.  

-   **Com Capacidade de Hibernação** – Indica se o computador pode entrar em hibernação se estiver configurado para tal.  

-   **Reativação da Suspensão** – Indica se o computador pode ser reativado da suspensão se estiver configurado para tal.  

-   **Reativação da Hibernação** – Indica se o computador pode ser reativado da hibernação se estiver configurado para tal.  

 Os valores indicados pelo relatório **Capacidades de Energia** indicam as capacidades de suspensão e hibernação de computadores, conforme comunicado pelo Windows. No entanto, os valores comunicados não refletem casos em que as definições do Windows ou o BIOS impedem estas funções de funcionarem.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Recolha**|Na lista pendente, selecione uma coleção para este relatório.|  
|**Filtro de Apresentação**|Na lista pendente, selecione **não suportado** para apresentar apenas os computadores na coleção especificada que estão sem capacidade de suspensão, hibernação, reativação da suspensão ou reativação da hibernação. Selecione **Mostrar tudo** para apresentar todos os computadores na coleção especificada.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Este relatório não tem parâmetros ocultados que pode definir.  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório contém ligações para o relatório seguinte que fornece mais informações sobre o item selecionado.  

|Nome do Relatório|Detalhes|  
|-----------------|-------------|  
|**Detalhes do Computador**|Clique no nome do computador para ver as capacidades de energia, as definições de energia e esquemas de energia aplicados para o computador selecionado.<br /><br /> Para obter mais informações, consulte [Computer Details Report](#BKMK_Computer_Details) neste tópico.|  

###  <a name="BKMK_Settings"></a> Relatório Definições de Energia  
 O relatório **Definições de Energia** mostra uma lista agregada de definições de energia utilizadas pelos computadores na coleção especificada. Para cada definição de energia, os modos possíveis de energia, valores e unidades são apresentados, juntamente com uma contagem do número de computadores que utilizam esses valores. Este relatório pode ser utilizado durante a fase de monitorização de gestão de energia para ajudar o administrador a compreender as definições de energia existentes utilizadas por computadores do site e para ajudar as definições de energia ideais do plano a serem aplicadas utilizando um esquema de gestão de energia. O relatório também é útil durante a resolução de problemas para validar as definições de energia aplicadas corretamente.  

> [!NOTE]  
>  As definições apresentadas são recolhidas de computadores cliente durante o inventário de hardware. Consoante o tempo em que o inventário de hardware é executado, as definições dos esquemas de energia sem pico ou de pico aplicado podem ser recolhidas.  

 Utilize os parâmetros seguintes para configurar este relatório.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Nome da coleção**|Na lista pendente, selecione uma coleção para este relatório.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Os seguintes parâmetros ocultados podem ser, opcionalmente, especificados para alterar o comportamento deste relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**numberOfLocalizations**|Especifique o número de idiomas em que pretende ver os nomes de definição de energia comunicados pelos computadores cliente. Se pretender ver apenas o idioma mais popular, deixe esta definição com a predefinição de **1**. Para ver todos os idiomas, defina este valor para **0**.|  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório contém ligações para o relatório seguinte que fornece mais informações sobre o item selecionado.  

|Nome do Relatório|Detalhes|  
|-----------------|-------------|  
|**Detalhes das Definições de Energia**|Clique no número de computadores na coluna **Computadores** para ver uma lista de todos os computadores que utilizam as definições de energia nessa linha.<br /><br /> Para obter mais informações, consulte [Power Settings Details Report](#BKMK_Settings_Details) neste tópico.|  

###  <a name="BKMK_Settings_Details"></a> Power Settings Details report  
 O relatório **Detalhes de Definições de Energia** apresenta informações adicionais sobre os computadores selecionados no relatório **Definições de Energia** . Este relatório é denominado pelo relatório **Definições de Energia** e não foi concebido para ser executado diretamente pelo administrador do site.  

#### <a name="required-report-parameters"></a>Parâmetros de relatório necessários  
 Tem de especificar os parâmetros seguintes para executar este relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**Recolha**|Na lista pendente, selecione uma coleção para utilizar para este relatório.|  
|**Definição de Energia GUID**|Na lista pendente, selecione a definição de energia GUID em que pretende um relatório. Para obter uma lista de todas as definições de energia e respetivas utilizações, consulte [definições do plano de gestão de energia disponíveis](../../../../core/clients/manage/power/create-and-apply-power-plans.md#BKMK_Plans) no tópico [como criar e aplicar esquemas de energia no System Center Configuration Manager](../../../../core/clients/manage/power/create-and-apply-power-plans.md).|  
|**Power Mode**|Na lista pendente, selecione o tipo de definições de energia que pretende apresentar nos resultados do relatório. Selecione **Ligado** para ver as definições de energia configuradas quando o computador está ligado e **Com Bateria** para ver as definições de energia configuradas quando o computador está em execução com energia da bateria.|  
|**Índice de Definição**|Na lista pendente, selecione o valor do nome da definição de energia selecionado no qual pretende um relatório. Por exemplo, se pretender apresentar todos os computadores com a definição **desligar o disco rígido após** configurada para **10** minutos, selecione **desligar o disco rígido após** no **Nome da Definição de Energia** e **10** no **Índice de Definição**.|  

#### <a name="hidden-report-parameters"></a>Parâmetros de relatório ocultos  
 Os seguintes parâmetros ocultados podem ser, opcionalmente, especificados para alterar o comportamento deste relatório.  

|Nome do Parâmetro|Descrição|  
|--------------------|-----------------|  
|**numberOfLocalizations**|Especifique o número de idiomas em que pretende ver os nomes de definição de energia comunicados pelos computadores cliente. Se pretender ver apenas o idioma mais popular, deixe esta definição com a predefinição de **1**. Para ver todos os idiomas, defina este valor para **0**.|  

#### <a name="report-links"></a>Ligações de relatórios  
 Este relatório contém ligações para o relatório seguinte que fornece mais informações sobre o item selecionado.  

|Nome do Relatório|Detalhes|  
|-----------------|-------------|  
|**Detalhes do Computador**|Clique no nome do computador para ver as capacidades de energia, as definições de energia e esquemas de energia aplicados para o computador selecionado.<br /><br /> Para obter mais informações, consulte [Computer Details Report](#BKMK_Computer_Details) neste tópico.|  
