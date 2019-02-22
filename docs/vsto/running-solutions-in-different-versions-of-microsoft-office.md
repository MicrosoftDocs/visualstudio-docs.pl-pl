---
title: Uruchamianie rozwiązań w różnych wersjach pakietu Microsoft Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4db3b9694ed8a21786933c3975e9f0970f60c7aa
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633905"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Uruchamianie rozwiązań w różnych wersjach pakietu Microsoft Office

## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Uruchamianie rozwiązań pakietu Office utworzonych przy użyciu programu Visual Studio 2010 i nowszych

|Wersja pakietu Office przez szablon projektu|Docelowy .NET Framework projektu<sup>1</sup>|Wersje pakietu Office, które można uruchamiać rozwiązanie|Wymagane środowisko uruchomieniowe na komputerze użytkownika końcowego|
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|
|Pakiety Office 2016 i [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office system 2007<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office system 2007<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Program .NET Framework 3,5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools for Office Runtime|
|System Microsoft Office 2007|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy,<br /><br /> lub<br /><br /> Program .NET Framework 3,5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> System Microsoft Office 2007|Visual Studio 2010 Tools for Office Runtime|

 1. .NET Framework w wersji wymagające projekt jest ukierunkowany na komputerach użytkowników końcowych dla rozwiązania w celu uruchomienia. Na przykład jeśli projekt jest przeznaczony dla .NET Framework 3.5, .NET Framework 3.5 jest wymagany na komputerach użytkowników końcowych. W tym przykładzie rozwiązania nie będzie działać w przypadku tylko [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jest zainstalowany na komputerach użytkowników końcowych.

 2. W tym scenariuszu rozwiązania uruchomią się bez błędów w programie Microsoft Office system 2007 tylko wtedy, gdy nie używa funkcji, które są nowością w programie [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].

## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Uruchamianie rozwiązań pakietu Office utworzonych przy użyciu wersji programu Visual Studio przed Visual Studio 2010
 Aplikacje Microsoft Office, można uruchomić rozwiązania utworzone przy użyciu wersji programu Visual Studio przed Visual Studio 2010. W niektórych przypadkach te rozwiązania wymagają różnych wersji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Różne wersje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] można zainstalować obok siebie na tym samym komputerze.

 W poniższej tabeli przedstawiono, które wersje programu Microsoft Office, można uruchomić rozwiązań utworzonych za pomocą wcześniejszych wersji programu Visual Studio, a które wersje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] i .NET Framework są wymagane dla każdego rozwiązania.

|Wersja programu Visual Studio, użyty do utworzenia rozwiązania|Wersja pakietu Office przez szablon projektu|Wersje pakietu Office, które można uruchamiać rozwiązanie|Wymagane środowisko uruchomieniowe na komputerze użytkownika końcowego|Wymagana wersja programu .NET Framework na komputerze użytkownika końcowego|
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|
|Visual Studio 2008 Professional<br /><br /> lub<br /><br /> Visual Studio Team System 2008|System Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> System Microsoft Office 2007|Visual Studio 2010 Tools for Office Runtime<sup>1</sup><br /><br /> lub<br /><br /> Visual Studio Tools dla pakietu Microsoft Office system (wersja 3.0 Runtime)|Program .NET Framework 3,5|
|Jedną z następujących wersji programu Visual Studio 2005 za pomocą VSTO 2005 SE<sup>2</sup> zainstalowane:<br /><br /> — Program visual Studio 2005 Tools dla pakietu Office<br />-   Visual Studio Team System 2005<br />-   Visual Studio 2005 Professional|System Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32-bitowych<sup>3</sup>)<br /><br /> System Microsoft Office 2007|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET framework 2.0, .NET Framework 3.0 lub .NET Framework 3.5|
|Dowolny z następujących wersji programu Visual Studio:<br /><br /> -   Visual Studio 2008 Professional<br />-   Visual Studio Team System 2008<br />— Program visual Studio 2005 Tools dla pakietu Office (z lub bez VSTO 2005 SE<sup>2</sup> zainstalowane)<br />— Program visual Studio Team System 2005 (z lub bez VSTO 2005 SE<sup>2</sup> zainstalowane)<br />— Program visual Studio Professional 2005 z VSTO 2005 SE<sup>2</sup> zainstalowane|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32-bitowych<sup>3</sup>)<br /><br /> System Microsoft Office 2007<br /><br /> Microsoft Office 2003|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET framework 2.0, .NET Framework 3.0 lub .NET Framework 3.5|

 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikacji obejmują Visual Studio 2010 Tools dla pakietu Office runtime. W związku z tym, te aplikacje zawsze korzystają z programu Visual Studio 2010 Tools dla pakietu Office runtime zamiast programu Visual Studio Tools dla pakietu Microsoft Office (wersja 3.0 Runtime) w tym scenariuszu. Aplikacji w programie Microsoft Office system 2007 można użyć Visual Studio 2010 Tools dla pakietu Office Runtime lub Visual Studio Tools dla pakietu Microsoft Office system (wersja 3.0 Runtime).

 2. VSTO 2005 SE jest bezpłatnym dodatkiem programu Visual Studio, który zapewnia dodatku narzędzi VSTO szablony projektu dla programu Microsoft Office 2003 i Microsoft Office system 2007. Można go zainstalować za pomocą programu Visual Studio 2005 Professional, Visual Studio 2005 Tools dla pakietu Office lub wersji programu Visual Studio Team System 2005. Aby uzyskać więcej informacji, zobacz [Visual Studio 2005 Tools for Office Second Edition](http://go.microsoft.com/fwlink/?LinkId=148446).

 3. Rozwiązań pakietu Office, które wymagają programu Visual Studio 2005 Tools for Office Second Edition Runtime nie są zgodne z 64-bitowe wersje [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. Do uruchamiania tych rozwiązań w 64-bitową wersję [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] lub [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], należy uaktualnić projekt, aby [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] lub projektu programu Visual Studio 2008, który jest przeznaczony dla systemu Microsoft Office 2007.

## <a name="see-also"></a>Zobacz także
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Visual Studio Tools dla pakietu Office Runtime ― scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
