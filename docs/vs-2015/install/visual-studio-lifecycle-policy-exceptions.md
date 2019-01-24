---
title: Wyjątki od zasad cyklu życia programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b17693523c75dc434fdda258c07a9b17ecfda1b0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763092"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Wyjątki od zasad cyklu życia programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio obejmuje zestaw kompilatorów, języków i środowisk, w tym uruchomieniowych, oraz inne zasoby umożliwiające wdrożenie go na wielu platformach Microsoft. Jako udogodnienie dla klientów program Visual Studio może zainstalować określone zestawy Microsoft SDK i inne składniki Microsoft, które są przeznaczone na te platformy Microsoft i ułatwiają ich obsługę. Te składniki mogą być licencjonowane i obsługiwane zgodnie z oddzielnymi postanowieniami i zasadami.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Składniki zewnętrzne, które należy wykonać zasadom cyklu życia innym niż zasady programu Visual Studio  
 W poniższej tabeli wymieniono składniki platformy firmy Microsoft, które mogą być dołączone do programu Visual Studio (w zależności od określonej wersji oprogramowania Visual Studio), i które wymagają własne zasady pomocy technicznej i przedziały czasu.  
  
|RODZINA PRODUKTÓW|NAZWA ZEWNĘTRZNA|  
|--------------------|-------------------|  
|[.NET 3.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|Zestaw SDK dla platformy .NET 3.5<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|Zestaw SDK dla platformy .NET 4.5|  
|[.NET 4.5.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 MT Pack (Classic)<br /><br /> .NET 4.5.1 Multi-targeting Pack (Store)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> .NET 4.5.1 Redist<br /><br /> .NET 4.5.1 Redist Language Packs<br /><br /> Zestaw SDK dla platformy .NET 4.5.1|  
|[ASP.NET Web Stack](http://go.microsoft.com/fwlink/?LinkId=328918)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET Web API<br /><br /> ASP.NET Web API 2<br /><br /> ASP.NET Web Pages 2<br /><br /> ASP.NET Web Pages 3|  
|[Entity Framework 6](http://go.microsoft.com/fwlink/?LinkId=328950)|Entity Framework 6|  
|[Exchange 2013](http://go.microsoft.com/fwlink/?LinkId=328950)|Exchange Web Services|  
|[Microsoft OWIN](http://go.microsoft.com/fwlink/?LinkId=328951)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](http://go.microsoft.com/fwlink/?LinkId=328952)|Microsoft Web Developer Tools 2013|  
|Aktualizacje tych składników są rozpowszechniane za pośrednictwem pakietu NuGet i nie podlegają standardowym zasadom cyklu życia produktów firmy Microsoft.  Zobacz [ http://docs.nuget.org/ ](http://docs.nuget.org/) Aby uzyskać więcej informacji.|JSON Web Token Handler dla programu Microsoft .NET Framework 4.5<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Struktura optymalizacji sieci Web<br /><br /> WebGrease|  
|[ODataLib](http://go.microsoft.com/fwlink/?LinkId=328954)|ODataLib|  
|[Office 2013](http://support.microsoft.com/lifecycle/?p1=16674)|Zestaw SDK Open XML|  
|[Online Services Policy](http://support.microsoft.com/gp/OSSLpolicy)|Zestaw SDK usługi Microsoft Ads|  
|[SharePoint 2013](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|Składnik klienta programu SharePoint<br /><br /> SharePoint Foundation 2013<br /><br /> Rozszerzenia Windows Identity Foundation|  
|[Silverlight 5](http://support.microsoft.com/lifecycle/?p1=16278)<br /><br /> <br />> Zobacz też: [http://support.microsoft.com/gp/lifean45](http://support.microsoft.com/gp/lifean45)|Środowisko uruchomieniowe Silverlight 5<br /><br /> Zestaw SDK środowiska Silverlight 5|  
|[SQL Server 2008 R2](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|Typy SQL System CLR (SQL Server 2008 R2)|  
|[SQL Server 2012](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Narzędzia wiersza polecenia SQL<br /><br /> Usługa językowa SQL — IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> Typy SQL System CLR (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Narzędzia wiersza polecenia SQL<br /><br /> Usługa językowa SQL — IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> Typy SQL System CLR (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](http://support.microsoft.com/lifecycle/?p1=16106)|SQL Server Compact Edition 4.0|  
|[Usługi WCF RIA Services w wersji 1.0 z dodatkiem SP2](http://go.microsoft.com/fwlink/?LinkId=328955)|Usługi WCF RIA 1.0 z dodatkiem SP2|  
|[Windows Server 2008](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Windows Web Services (WWS) dla Windows Server 2008|  
|[Windows 7](http://support.microsoft.com/lifecycle/?c2=14019)|Zestaw SDK systemu Windows 7|  
|[Windows 8](http://support.microsoft.com/lifecycle/?c2=16796)|Zestaw SDK systemu Windows 8|  
|[Windows 8.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Zestaw SDK systemu Windows 8.1<br /><br /> Biblioteka systemu Windows dla języka JavaScript (WinJS)|  
|[Microsoft Azure](http://support.microsoft.com/gp/azure-cloud-lifecycle-faq)<br /><br /> <br />> Zobacz też: [Zasady cyklu życia online](http://support.microsoft.com/gp/OSSLpolicy)|Zestaw Mobile Services SDK dla systemu Microsoft Azure<br /><br /> Zestaw Mobile Services dla systemu Microsoft Azure|