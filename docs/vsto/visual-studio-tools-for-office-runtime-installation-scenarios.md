---
title: Visual Studio Tools dla scenariuszy instalacji środowiska uruchomieniowego pakietu Office
description: Dowiedz się, jak zainstalować narzędzia Visual Studio 2010 Tools for Office Runtime. W tym artykule opisano trzy scenariusze instalacji.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 10b747602a1c5af9f63c567103a80405341019af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921795"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools dla scenariuszy instalacji środowiska uruchomieniowego pakietu Office
  Program Visual Studio 2010 Tools for Office Runtime można zainstalować na trzy sposoby:

- Po zainstalowaniu programu Visual Studio.

- Podczas instalowania Microsoft Office.

- Po zainstalowaniu pakietu redystrybucyjnego programu Visual Studio 2010 Tools for Office Runtime.

  Zainstalowane składniki środowiska uruchomieniowego zależą od konfiguracji komputera i scenariusza instalacji.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Składniki środowiska uruchomieniowego, które są zainstalowane w każdym scenariuszu instalacji
 Program Visual Studio 2010 Tools for Office Runtime ma trzy składniki: program ładujący rozwiązanie pakietu Office, rozszerzenia pakietu Office dla .NET Framework 3,5 oraz rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego. Po zainstalowaniu środowiska uruchomieniowego program ładujący rozwiązanie pakietu Office jest zawsze instalowany. Instalacja rozszerzeń pakietu Office dla .NET Framework zależy od konfiguracji komputera i scenariusza instalacji. Jeśli jeden z rozszerzeń pakietu Office nie może zostać zainstalowany podczas pierwszej instalacji środowiska uruchomieniowego, środowisko uruchomieniowe automatycznie zainstaluje brakujące rozszerzenia pakietu Office w późniejszym czasie, gdy zostaną spełnione określone wymagania. Ta funkcja środowiska uruchomieniowego jest nazywana *instalacją na żądanie*.

 W poniższej tabeli przedstawiono, które składniki środowiska uruchomieniowego są instalowane domyślnie w każdym scenariuszu instalacji środowiska uruchomieniowego. Więcej informacji o każdym scenariuszu pojawia się później.

|Scenariusz instalacji środowiska uruchomieniowego|Moduł ładujący rozwiązanie pakietu Office|Rozszerzenia pakietu Office dla .NET Framework 3,5|Rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Rozszerzenia pakietu Office dla [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|Z [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] i nowszymi|Tak|Tak, jeśli .NET Framework 3,5 jest już zainstalowany.|Tak|Tak|
|Się [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Tak|Tak, jeśli .NET Framework 3,5 jest już zainstalowany.|Nie|Nie|
|Z pakietem Office 2010 z dodatkiem Service Pack 1 (SP1) lub nowszym|Tak|Tak, jeśli .NET Framework 3,5 jest już zainstalowany.|Tak, jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jest już zainstalowany.|Nie|
|Z pakietem redystrybucyjnym środowiska uruchomieniowego|Tak|Tak, jeśli .NET Framework 3,5 jest już zainstalowany|Tak, jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jest już zainstalowany.|Tak, jeśli [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] jest już zainstalowany.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Zainstaluj środowisko uruchomieniowe w programie Visual Studio lub Microsoft Office Developer Tools for Visual Studio
 Po zainstalowaniu narzędzi programistycznych pakietu Office w programie Visual Studio rozszerzenia pakietu Office dla programu [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] i programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] są zawsze zainstalowane na komputerze deweloperskim. Rozszerzenia pakietu Office dla .NET Framework 3,5 są instalowane tylko wtedy, gdy .NET Framework 3,5 jest już obecny na komputerze deweloperskim. W przypadku zainstalowania .NET Framework 3,5 po zainstalowaniu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] programu środowisko uruchomieniowe automatycznie zainstaluje rozszerzenia pakietu Office dla .NET Framework 3,5 przy pierwszym utworzeniu projektu pakietu Office, który jest przeznaczony dla .NET Framework 3,5.

> [!WARNING]
> Nie można utworzyć projektu pakietu Office, który jest przeznaczony dla .NET Framework 3,5 przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] lub w późniejszym czasie.

 Aby uzyskać więcej informacji na temat sposobu instalowania narzędzi deweloperskich pakietu Office, zobacz [jak to zrobić: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

### <a name="install-the-runtime-with-office"></a>Instalowanie środowiska uruchomieniowego z pakietem Office
 Podczas instalacji pakietu Office rozszerzenia pakietu Office dla .NET Framework 3,5 są instalowane, jeśli .NET Framework 3,5 jest już obecny na komputerze. W przypadku zainstalowania .NET Framework 3,5 po pakiecie Office środowisko uruchomieniowe automatycznie zainstaluje rozszerzenia pakietu Office dla .NET Framework 3,5 przy pierwszym próbie załadowania rozwiązania, które jest przeznaczone dla .NET Framework 3,5.

 Rozszerzenia pakietu Office dla programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego nie są instalowane razem z pakietem Office, nawet jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] program lub nowszy jest już obecny podczas instalowania pakietu Office.

 Rozszerzenia pakietu Office dla programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] są instalowane z pakietem Office. Użytkownicy końcowi mogą uzyskać rozszerzenia pakietu Office dla programu [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , instalując aktualizację Windows Update.

 Aby upewnić się, że użytkownicy mają rozszerzenia niezbędne do korzystania z aplikacji, należy uwzględnić najnowszą wersję pakietu redystrybucyjnego programu Visual Studio 2010 Tools for Office Runtime jako warunek wstępny dla Twojego rozwiązania. Aby uzyskać więcej informacji na temat wymagań wstępnych, zobacz [wymagania wstępne dotyczące wdrażania pakietu Office](/previous-versions/bb608617(v=vs.110)).

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Instalowanie środowiska uruchomieniowego przy użyciu pakietu redystrybucyjnego środowiska uruchomieniowego
 Środowisko uruchomieniowe można zainstalować, uruchamiając pakiet redystrybucyjny programu Visual Studio 2010 Tools dla pakietu Office Runtime ręcznie lub dołączając pakiet redystrybucyjny jako warunek wstępny podczas wdrażania rozwiązania pakietu Office.

 Po zainstalowaniu środowiska uruchomieniowego przy użyciu pakietu redystrybucyjnego programu Visual Studio 2010 Tools for Office Runtime rozszerzenia pakietu Office dla .NET Framework 3,5 i rozszerzeń pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych są instalowane, jeśli odpowiednie wersje .NET Framework już istnieją na komputerze. Jeśli na komputerze nie ma żadnej z tych wersji .NET Framework podczas instalowania środowiska uruchomieniowego, rozszerzenia pakietu Office dla brakującej wersji .NET Framework nie są zainstalowane w tym czasie. W przypadku zainstalowania brakującej wersji .NET Framework nowszej, środowisko uruchomieniowe automatycznie zainstaluje odpowiednie rozszerzenia pakietu Office przy następnym zainstalowaniu rozwiązania wymagającego rozszerzeń (Jeśli środowisko uruchomieniowe zostało zainstalowane z rozwiązaniem wdrożonym przy użyciu technologii ClickOnce) lub załadowane (Jeśli środowisko uruchomieniowe zostało zainstalowane z rozwiązaniem, które zostało wdrożone przy użyciu Instalator Windows).

 Aby uzyskać więcej informacji na temat dołączania wymagań wstępnych w rozwiązaniu ClickOnce, zobacz [jak: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych w celu uruchamiania rozwiązań pakietu Office](/previous-versions/bb608608(v=vs.110)). Aby uzyskać więcej informacji na temat ręcznego instalowania środowiska uruchomieniowego z pakietu redystrybucyjnego, zobacz [How to: Install the Visual Studio Tools for Office Runtime redystrybucyjny](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).

## <a name="see-also"></a>Zobacz też
- [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office — omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Zestawy w Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)