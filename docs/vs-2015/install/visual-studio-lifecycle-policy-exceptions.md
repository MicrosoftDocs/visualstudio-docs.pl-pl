---
title: Wyjątki zasad cyklu życia programu Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: cc3a18fe1ce76b6214766ba45fc5441e80c56cef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918486"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Wyłączenia dotyczące zasad korzystania z oprogramowania Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio obejmuje zestaw kompilatorów, języków i środowisk, w tym uruchomieniowych, oraz inne zasoby umożliwiające wdrożenie go na wielu platformach Microsoft. Jako udogodnienie dla klientów program Visual Studio może zainstalować określone zestawy Microsoft SDK i inne składniki Microsoft, które są przeznaczone na te platformy Microsoft i ułatwiają ich obsługę. Te składniki mogą być licencjonowane i obsługiwane zgodnie z oddzielnymi postanowieniami i zasadami.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Składniki zewnętrzne, które są zgodne z zasadami cyklu życia inną niż zasady programu Visual Studio  
 W poniższej tabeli wymieniono składniki platformy firmy Microsoft, które mogą być dołączone do programu Visual Studio (w zależności od wersji oprogramowania Visual Studio), które podlegają własnym zasadom pomocy technicznej i przedziałom czasowym.  
  
|RODZINA PRODUKTÓW|NAZWA ZEWNĘTRZNA|  
|--------------------|-------------------|  
|[.NET 3,5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|Zestaw SDK dla platformy .NET 3.5<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|Zestaw SDK dla platformy .NET 4.5|  
|[.NET 4.5.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 MT Pack (Classic)<br /><br /> .NET 4.5.1 Multi-targeting Pack (Store)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> .NET 4.5.1 Redist<br /><br /> .NET 4.5.1 Redist Language Packs<br /><br /> Zestaw SDK dla platformy .NET 4.5.1|  
|[ASP.NET Web Stack](https://support.microsoft.com/kb/2902020)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET Web API<br /><br /> ASP.NET Web API 2<br /><br /> ASP.NET Web Pages 2<br /><br /> ASP.NET Web Pages 3|  
|[Entity Framework 6](https://support.microsoft.com/kb/2902020)|Entity Framework 6|  
|[Exchange 2013](https://support.microsoft.com/kb/2902020)|Exchange Web Services|  
|[Microsoft OWIN](https://support.microsoft.com/kb/2902020)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](https://support.microsoft.com/kb/2902020)|Microsoft Web Developer Tools 2013|  
|Aktualizacje tych składników są rozpowszechniane za pośrednictwem pakietu NuGet i nie podlegają standardowym zasadom cyklu życia produktów firmy Microsoft.  [http://docs.nuget.org/](/nuget/)Aby uzyskać więcej informacji, zobacz.|Procedura obsługi tokenów sieci Web JSON dla Microsoft .NET Framework 4,5<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Struktura optymalizacji sieci Web<br /><br /> WebGrease|  
|[ODataLib](https://support.microsoft.com/kb/2902020)|ODataLib|  
|[Office 2013](https://support.microsoft.com/lifecycle/search/?p1=16674)|Zestaw SDK Open XML|  
|[Zasady usług online](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Zestaw SDK usługi Microsoft Ads|  
|[SharePoint 2013](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|Składnik klienta programu SharePoint<br /><br /> SharePoint Foundation 2013<br /><br /> Rozszerzenia Windows Identity Foundation|  
|[Program Silverlight 5](https://support.microsoft.com/lifecycle/search/?p1=16278)<br /><br /> <br />> Zobacz również: [http://support.microsoft.com/gp/lifean45](https://support.microsoft.com/gp/lifean45)|Środowisko uruchomieniowe Silverlight 5<br /><br /> Zestaw SDK środowiska Silverlight 5|  
|[SQL Server 2008 R2](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|Typy SQL System CLR (SQL Server 2008 R2)|  
|[SQL Server 2012](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Narzędzia wiersza polecenia SQL<br /><br /> Usługa języka SQL — technologia IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> Typy SQL System CLR (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Narzędzia wiersza polecenia SQL<br /><br /> Usługa języka SQL — technologia IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> Typy SQL System CLR (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](https://support.microsoft.com/lifecycle/search/?p1=16106)|SQL Server Compact Edition 4.0|  
|[Usługi WCF RIA 1.0 z dodatkiem SP2](https://support.microsoft.com/kb/2902020)|Usługi WCF RIA 1.0 z dodatkiem SP2|  
|[Windows Server 2008](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Windows Web Services (WWS) dla Windows Server 2008|  
|[Windows 7](https://support.microsoft.com/lifecycle/search/?c2=14019)|Zestaw SDK systemu Windows 7|  
|[Windows 8](https://support.microsoft.com/lifecycle/search/?c2=16796)|Zestaw SDK systemu Windows 8|  
|[Windows 8.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Zestaw SDK systemu Windows 8.1<br /><br /> Biblioteka systemu Windows dla języka JavaScript (WinJS)|  
|[Microsoft Azure](https://support.microsoft.com/help/18486/lifecycle-faq-azure)<br /><br /> <br />> Zobacz również: [Zasady cyklu życia online](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Zestaw Mobile Services SDK dla systemu Microsoft Azure<br /><br /> Zestaw Mobile Services dla systemu Microsoft Azure|
