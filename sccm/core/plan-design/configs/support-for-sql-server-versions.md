---
title: "Versões do SQL Server suportadas | Microsoft Docs"
description: "Obter os requisitos de configuração e a versão do SQL Server para alojar uma base de dados do site do System Center Configuration Manager."
ms.custom: na
ms.date: 05/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35e237b6-9f7b-4189-90e7-8eca92ae7d3d
caps.latest.revision: "21"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b35e45b9514297e2f9ce405a3244462ed735f39f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2017
---
# <a name="supported-sql-server-versions-for-system-center-configuration-manager"></a>Versões suportadas do SQL Server para o System Center Configuration Manager

*Aplica-se a: O System Center Configuration Manager (ramo atual)*

Cada site do System Center Configuration Manager requer uma versão do SQL Server suportadas e a configuração para alojar a base de dados do site.  

##  <a name="bkmk_Instances"></a> Instâncias e localizações do SQL Server  
 **Site de administração central e sites primários:**  
A base de dados do site tem de utilizar uma instalação completa do SQL Server.  

 SQL Server pode estar localizada em:  

-   O computador de servidor do site.  
-   Um computador que seja remoto do servidor do site.  

São suportadas as seguintes instâncias:  

-   A instância predefinida ou nomeada do SQL Server.  
-   Configurações de várias instâncias.  
-   Um cluster do SQL Server. Consulte [utilizar um cluster do SQL Server para alojar a base de dados do site](../../../core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database.md).
-   Um grupo de Disponibilidade AlwaysOn do SQL Server. Esta opção requer o Configuration Manager versão 1602 ou posterior. Para obter mais informações, consulte [SQL Server AlwaysOn para uma base de dados do site de elevada disponibilidade para o System Center Configuration Manager](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).


 **Sites secundários:**  
 A base de dados do site pode utilizar a instância predefinida de uma instalação completa do SQL Server ou SQL Server Express.  

 SQL Server tem de estar localizado no computador do servidor do site.  

 **Limitações para suportar**   
 Não são suportadas as seguintes configurações:
 -   Um cluster do SQL Server numa configuração de cluster de balanceamento de carga na rede (NLB)
 -   Um cluster do SQL Server num Cluster partilhado Volume (CSV)
 -   Base de dados do SQL Server espelhamento de tecnologia e replicação ponto-a-ponto

Replicação transacional do SQL Server só é suportada para replicar objetos para pontos de gestão que estão configurados para utilizar [réplicas de base de dados](https://technet.microsoft.com/library/mt608546.aspx).  

##  <a name="bkmk_SQLVersions"></a> Versões suportadas do SQL Server  
 Numa hierarquia com múltiplos sites, sites diferentes podem utilizar diferentes versões do SQL Server para alojar a base de dados do site, desde que os seguintes são verdadeiras:
 -  O Configuration Manager suporta as versões do SQL Server que utilizar.
 -  Versões do SQL Server que utilizar permanecem no suporte de pela Microsoft.
 -  SQL Server suporta a replicação entre duas versões do SQL Server.  Por exemplo, [do SQL Server não suporta a replicação entre SQL Server 2008 R2 e o SQL Server 2016](https://docs.microsoft.com/sql/relational-databases/replication/deprecated-features-in-sql-server-replication).



 Salvo especificação em contrário, as seguintes versões do SQL Server são suportadas com todas as versões de Active Directory do System Center Configuration Manager. Se suportar para uma nova versão do SQL Server ou o pacote de serviço é adicionado, a versão do Configuration Manager que adiciona que suportam será indicada. Da mesma forma, se o suporte foi preterido, em seguida, procure detalhes sobre as versões afetados do Configuration Manager.   

Suporte para um pacote de serviço do SQL Server específico inclui atualizações cumulativas para esse pacote de serviço, a menos que uma atualização cumulativa interrompe o com versões anteriores para essa versão do pacote de serviço de base. Quando é indicado versão sem service pack, o suporte destina-se que a versão do SQL Server sem nenhum service pack. No futuro, se um service pack for lançado para essa versão, uma declaração de suporte separado será de ser declarada antes dessa nova versão do pacote de serviço é suportada.


> [!IMPORTANT]  
>  Quando utiliza o SQL Server Standard para a base de dados no site de administração central, limitar o número total de clientes que uma hierarquia consegue suportar. Consulte [Dimensionamento e números da escala](../../../core/plan-design/configs/size-and-scale-numbers.md).

### <a name="sql-server-2016-sp1-standard-enterprise"></a>SQL Server 2016 SP1: Standard, Enterprise  
Pode utilizar esta versão do SQL Server sem versão de atualização cumulativa mínima para o seguinte:  

-   Um site de administração central  
-   Um site primário  
-   Um site secundário  

### <a name="sql-server-2016-standard-enterprise"></a>SQL Server 2016: Standard, Enterprise  
Pode utilizar esta versão do SQL Server sem versão de atualização cumulativa mínima para o seguinte:  

-   Um site de administração central  
-   Um site primário  
-   Um site secundário  


### <a name="sql-server-2014-sp2-standard-enterprise"></a>SQL Server 2014 SP2: Standard, Enterprise  
Pode utilizar esta versão do SQL Server sem versão de atualização cumulativa mínima para o seguinte:  

-   Um site de administração central  
-   Um site primário  
-   Um site secundário



### <a name="sql-server-2014-sp1-standard-enterprise"></a>SQL Server 2014 SP1: Standard, Enterprise  
 Pode utilizar esta versão do SQL Server sem versão de atualização cumulativa mínima para o seguinte:  

-   Um site de administração central  
-   Um site primário  
-   Um site secundário


### <a name="sql-server-2012-sp3-standard-enterprise"></a>SQL Server 2012 SP3: Standard, Enterprise  
 Pode utilizar esta versão do SQL Server sem versão de atualização cumulativa mínima para o seguinte:  

-   Um site de administração central  
-   Um site primário  
-   Um site secundário  

<!-- Support for this service pack version has been dropped by Microsoft    
### SQL Server 2012 SP2: Standard, Enterprise   
 You can use this version of SQL Server with no minimum cumulative update version for the following:  

-   A central administration site  
-   A primary site  
-   A secondary site  
-->

### <a name="sql-server-2008-r2-sp3-standard-enterprise-datacenter"></a>SQL Server 2008 R2 SP3: Standard, Enterprise, Datacenter     
  Não é suportada nesta versão do SQL Server [a partir da versão 1702](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-support-for-sql-server-versions-as-a-site-database).  
 Esta versão do SQL Server continua a ser suportada quando utiliza uma versão do Configuration Manager antes de 1702.

Quando suportado pela versão do Configuration Manager, pode utilizar esta versão do SQL Server sem versão de atualização cumulativa mínima para o seguinte:  

-   Um site de administração central  
-   Um site primário
-   Um site secundário



### <a name="sql-server-2016-express-sp1"></a>SP1 Express do SQL Server 2016  
Pode utilizar esta versão do SQL Server sem versão de atualização cumulativa mínima para o seguinte:
-   Um site secundário

### <a name="sql-server-2016-express"></a>Express do SQL Server 2016
Pode utilizar esta versão do SQL Server sem versão de atualização cumulativa mínima para o seguinte:
-   Um site secundário


### <a name="sql-server-2014-express-sp2"></a>SQL Server 2014 SP2 rápida   
Pode utilizar esta versão do SQL Server sem versão de atualização cumulativa mínima para o seguinte:  

-   Um site secundário  


### <a name="sql-server-2014-express-sp1"></a>SQL Server 2014 Express SP1   
 Pode utilizar esta versão do SQL Server sem versão de atualização cumulativa mínima para o seguinte:  

-   Um site secundário  

### <a name="sql-server-2012-express-sp3"></a>SQL Server 2012 Express SP3  
Pode utilizar esta versão do SQL Server sem versão de atualização cumulativa mínima para o seguinte:  

-   Um site secundário  

<!-- Support for this service pack version has been dropped by Microsoft   
### SQL Server 2012 Express SP2   
 You can use this version of SQL Server with no minimum cumulative update version for the following:  

-   A secondary site  
-->


##  <a name="bkmk_SQLConfig"></a> Configurações necessárias para o SQL Server  
 O seguinte é necessário para todas as instalações do SQL Server que utiliza para uma base de dados do site (incluindo o SQL Server Express). Quando o Configuration Manager instala o SQL Server Express como parte de uma instalação de site secundário, estas configurações são criadas automaticamente para si.  

 **Versão de arquitetura do SQL Server:**  
 O Configuration Manager requer uma versão de 64 bits do SQL Server para alojar a base de dados do site.  

 **Agrupamento da base de dados:**  
 Em cada site, a instância do SQL Server que é utilizado para o site e a base de dados do site tem de utilizar o seguinte agrupamento: **SQL_Latin1_General_CP1_CI_AS**.  

 O Configuration Manager suporta duas exceções a este agrupamento para cumprir as normas definidas na GB18030 para utilização na China. Para obter mais informações, veja [Suporte internacional no System Center Configuration Manager](../../../core/plan-design/hierarchy/international-support.md).  

 **Funcionalidades do SQL Server:**  
 Só é necessária a funcionalidade **Serviços de Motor da Base de Dados** para cada servidor do site.  

 Replicação de base de dados do Configuration Manager não requer o **replicação do SQL Server** funcionalidade. No entanto, esta configuração de SQL Server é necessária se utilizar [da base de dados réplicas para pontos de gestão do System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Autenticação do Windows:**  
 O Configuration Manager requer **autenticação do Windows** para validar as ligações à base de dados.  

 **Instância do SQL Server:**  
 Tem de utilizar uma instância dedicada do SQL Server para cada site. Isto pode ser uma **instância nomeada** ou a **instância predefinida**.  

 **Memória do SQL Server:**  
 Reserve memória para o SQL Server utilizando o SQL Server Management Studio e definição de **memória de servidor mínima** em **opções de memória de servidor**. Para obter mais informações sobre como definir uma quantidade fixa de memória, consulte [como: Definir uma quantidade fixa de memória (SQL Server Management Studio)](http://go.microsoft.com/fwlink/p/?LinkId=233759).  

-   **Para um servidor de base de dados que está instalado no mesmo computador do servidor do site:** Limite a memória do SQL Server para 50 a 80 por cento da memória de sistema acessível disponível.  

-   **Para um servidor de base de dados dedicado (remoto a partir do servidor do site):** Limite a memória do SQL Server para 80 a 90 por cento da memória de sistema acessível disponível.  

-   **Para uma reserva de memória para o conjunto de memória intermédia de cada instância do SQL Server em utilização:**  

    -   Para um site de administração central: Defina um mínimo de 8 gigabytes (GB).  
    -   Para um site primário: Defina um mínimo de 8 gigabytes (GB).  
    -   Para um site secundário: Defina um mínimo de 4 gigabytes (GB).  

**Acionadores aninhados SQL:**  
 Os[acionadores aninhados SQL](http://go.microsoft.com/fwlink/?LinkId=528802) têm de estar ativados.  

 **Integração de CLR do SQL Server**  
  A base de dados de sites necessita do tempo de execução de idioma comum (CLR) do SQL Server para ser ativada. Isto é ativado automaticamente quando instala o Configuration Manager. Para obter mais informações sobre o CLR, consulte [introdução à integração do CLR do SQL Server](https://msdn.microsoft.com/library/ms254498\(v=vs.110\).aspx).  

##  <a name="bkmk_optional"></a> Configurações necessárias para o SQL Server  
 As seguintes configurações são opcionais para cada base de dados que utiliza uma instalação completa do SQL Server.  

 **Serviço do SQL Server:**  
 Pode configurar o serviço do SQL Server para executar utilizando:  

-   O **utilizador de domínio local** conta:  

    -   Esta é uma melhor prática e pode implicar registar manualmente o nome principal de serviço (SPN) para a conta.  

-   O **sistema local** conta do computador que executa o SQL Server:  

    -   Utilize a conta de sistema local para simplificar o processo de configuração.  
    -   Quando utiliza a conta de sistema local, o Configuration Manager regista automaticamente o SPN para o serviço SQL Server.  
    -   Tenha em atenção que utilizar uma conta de sistema local para o serviço do SQL Server não é uma melhor prática do SQL Server.  

Quando o computador a executar o SQL Server não utiliza a respetiva conta de sistema local para executar o serviço do SQL Server, tem de configurar o SPN da conta que executa o serviço do SQL Server nos serviços de domínio do Active Directory. (Quando é utilizada a conta de sistema, o SPN é automaticamente registado.)

Para obter informações sobre SPNs para a base de dados do site, consulte [gerir o SPN para o servidor de base de dados do site](../../../core/servers/manage/modify-your-infrastructure.md#bkmk_SPN) no [modificar a infraestrutura do System Center Configuration Manager](../../../core/servers/manage/modify-your-infrastructure.md) tópico.  

Para obter informações sobre como alterar a conta que é utilizada pelo serviço do SQL Server, consulte [como: Alterar a conta de arranque do serviço do SQL Server (SQL Server do Configuration Manager)](http://go.microsoft.com/fwlink/p/?LinkId=237661).  

**SQL Server Reporting Services:**  
SQL Server Reporting Services é necessário para instalar um ponto do Reporting Services que lhe permite executar relatórios.  

> [!IMPORTANT]  
> Depois de atualizar o SQL Server de uma versão anterior, poderá ver o seguinte erro:  *Report Builder não existe*.    
> Para resolver este erro, terá de reinstalar a função de sistema de sites de ponto do Reporting Services serviços.

**Portas do SQL Server:**  
Para comunicação com o motor de base de dados do SQL Server e para replicação entre sites, pode utilizar as configurações de porta do SQL Server predefinida ou especificar portas personalizadas:  

-   **Comunicações entre sites** utilizar o SQL Server Service Broker, que utiliza a porta TCP 4022 por predefinição.  
-   **Comunicações intra-site** entre o motor de base de dados do SQL Server e o sistema de sites do Configuration Manager várias funções de utilizam a porta TCP 1433, por predefinição. As seguintes funções do sistema de sites comunicam diretamente com a base de dados do SQL Server:  

    -   Ponto de gestão  
    -   Computador do Fornecedor de SMS  
    -   Ponto do Reporting Services  
    -   Servidor do site  

Quando um computador com o SQL Server aloja bases de dados de mais de um site, cada base de dados tem de utilizar uma instância separada do SQL Server. Além disso, cada instância tem de ser configurada para utilizar um conjunto exclusivo de portas.  

> [!WARNING]  
>  O Configuration Manager não suporta portas dinâmicas. Uma vez que, por predefinição, as instâncias nomeadas de SQL Server utilizam portas dinâmicas para ligações ao motor da base de dados, quando utilizar uma instância nomeada tem de configurar manualmente a porta estática que pretende utilizar para comunicação entre sites.  

Se tiver uma firewall ativada no computador que está a executar o SQL Server, certifique-se de que está configurada para permitir as portas que estão a ser utilizadas pela sua implementação e quaisquer localizações na rede entre computadores que comunicam com o SQL Server.  

Para obter um exemplo de como configurar o SQL Server para utilizar uma porta específica, consulte [como: Configurar um servidor para escutar numa porta TCP específica (SQL Server Configuration Manager)](http://go.microsoft.com/fwlink/p/?LinkID=226349) na Biblioteca TechNet do SQL Server.  

## <a name="upgrade-options-for-sql-server"></a>Opções de atualização para o SQL Server
Se precisar de atualizar a sua versão do SQL Server, recomendamos os seguintes métodos, de fácil mais complexas.
1. [Atualizar o SQL Server no local](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (recomendado).
2. Instalar uma nova versão do SQL Server num novo computador e, em seguida, [utilizar a opção de mover a base de dados](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) de configuração do Configuration Manager para apontar o seu servidor do site para o novo SQL Server.
3. Utilize [cópia de segurança e recuperação](/sccm/protect/understand/backup-and-recovery).
