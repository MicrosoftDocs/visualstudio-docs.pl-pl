---
title: Uruchamianie rozwiązań w różnych wersjach Microsoft Office
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
ms.openlocfilehash: 15d0a3611f314abe4b571f2235346dde55d6e358
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985602"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Uruchamianie rozwiązań w różnych wersjach Microsoft Office

## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Uruchamianie rozwiązań pakietu Office utworzonych przy użyciu programu Visual Studio 2010 lub nowszego

|Wersja pakietu Office wskazywanego przez szablon projektu|.NET Framework docelowe projektu<sup>1</sup>|Wersje pakietu Office, które mogą uruchamiać rozwiązanie|Wymagane środowisko uruchomieniowe na komputerze użytkownika końcowego|
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|
|Pakiet Office 2016 i [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy|Pakiet Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system<sup>2</sup>|Visual Studio 2010 Tools dla pakietu Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy|Pakiet Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office system<sup>2</sup>|Visual Studio 2010 Tools dla pakietu Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Program .NET Framework 3,5|Pakiet Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools dla pakietu Office Runtime|
|System Microsoft Office 2007|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy,<br /><br /> lub<br /><br /> Program .NET Framework 3,5|Pakiet Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> System Microsoft Office 2007|Visual Studio 2010 Tools dla pakietu Office Runtime|

 1. Wersja .NET Framework wymagana przez elementy docelowe projektu na komputerach użytkowników końcowych, aby można było uruchomić rozwiązanie. Na przykład jeśli projekt jest przeznaczony dla .NET Framework 3,5, na komputerach użytkowników końcowych jest wymagany .NET Framework 3,5. W tym przykładzie rozwiązanie nie zostanie uruchomione, jeśli na komputerach użytkowników końcowych zostanie zainstalowany tylko [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

 2. W tym scenariuszu rozwiązanie zostanie uruchomione bez błędów w systemie 2007 Microsoft Office tylko wtedy, gdy nie używa funkcji, które są nowe w [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].

## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Uruchamianie rozwiązań pakietu Office utworzonych przy użyciu wersji programu Visual Studio przed programem Visual Studio 2010
 Aplikacje Microsoft Office mogą uruchamiać rozwiązania utworzone przy użyciu wersji programu Visual Studio przed programem Visual Studio 2010. W niektórych przypadkach te rozwiązania wymagają różnych wersji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Różne wersje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] można zainstalować obok siebie na tym samym komputerze.

 W poniższej tabeli przedstawiono, które wersje Microsoft Office mogą uruchamiać rozwiązania utworzone przy użyciu poprzednich wersji programu Visual Studio, a także wersje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] i .NET Framework są wymagane dla każdego rozwiązania.

|Wersja programu Visual Studio użyta do utworzenia rozwiązania|Wersja pakietu Office wskazywanego przez szablon projektu|Wersje pakietu Office, które mogą uruchamiać rozwiązanie|Wymagane środowisko uruchomieniowe na komputerze użytkownika końcowego|Wymagana .NET Framework wersja na komputerze użytkownika końcowego|
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|
|Visual Studio 2008 Professional<br /><br /> lub<br /><br /> Visual Studio Team System 2008|System Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<sup>1</sup><br /><br /> System Microsoft Office 2007|Visual Studio 2010 Tools dla Office Runtime<sup>1</sup><br /><br /> lub<br /><br /> Visual Studio Tools dla systemu Microsoft Office (wersja 3,0 Runtime)|Program .NET Framework 3,5|
|Zainstalowano jedną z następujących wersji programu Visual Studio 2005 z programem VSTO 2005 SE<sup>2</sup> :<br /><br /> — Narzędzia programu Visual Studio 2005 dla pakietu Office<br />— Visual Studio Team System 2005<br />— Visual Studio 2005 Professional|System Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (tylko 32-bitowe<sup>3</sup>)<br /><br /> System Microsoft Office 2007|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2,0, .NET Framework 3,0 lub .NET Framework 3,5|
|Dowolne z następujących wersji programu Visual Studio:<br /><br /> — Visual Studio 2008 Professional<br />— Visual Studio Team System 2008<br />— Program Visual Studio 2005 Tools for Office (z zainstalowanym programem VSTO 2005 SE<sup>2</sup> lub bez niego)<br />— Visual Studio Team System 2005 (z lub bez zainstalowanego programu VSTO 2005 SE<sup>2</sup> )<br />— Zainstalowano program Visual Studio 2005 Professional z programem VSTO 2005 SE<sup>2</sup>|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (tylko 32-bitowe<sup>3</sup>)<br /><br /> System Microsoft Office 2007<br /><br /> Microsoft Office 2003|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2,0, .NET Framework 3,0 lub .NET Framework 3,5|

 1. aplikacje [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] zawierają narzędzia Visual Studio 2010 Tools for Office Runtime. W związku z tym te aplikacje zawsze korzystają z narzędzi Visual Studio 2010 Tools for Office Runtime, a nie Visual Studio Tools dla systemu Microsoft Office (wersja 3,0 Runtime) w tym scenariuszu. Aplikacje w systemie 2007 Microsoft Office mogą korzystać z narzędzi Visual Studio 2010 Tools for Office Runtime lub Visual Studio Tools dla systemu Microsoft Office (wersja 3,0 Runtime).

 2. VSTO 2005 SE to bezpłatny dodatek programu Visual Studio, który zawiera szablony projektów dodatku VSTO dla Microsoft Office 2003 i 2007 Microsoft Office System. Można go zainstalować za pomocą programu Visual Studio 2005 Professional, Visual Studio 2005 Tools for Office lub wersji w programie Visual Studio Team System 2005. Aby uzyskać więcej informacji, zobacz [Visual Studio 2005 Tools for Office Second Edition](https://developer.microsoft.com/office/docs).

 3. Rozwiązania pakietu Office wymagające programu Visual Studio 2005 Tools for Office Second Edition Runtime nie są zgodne z 64-bitowymi wersjami [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. Aby uruchomić te rozwiązania w 64-bitowej wersji [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] lub [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], należy uaktualnić projekt do [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] lub do projektu programu Visual Studio 2008, który jest przeznaczony dla systemu 2007 Microsoft Office.

## <a name="see-also"></a>Zobacz także
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office — omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Visual Studio Tools dla scenariuszy instalacji środowiska uruchomieniowego pakietu Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
