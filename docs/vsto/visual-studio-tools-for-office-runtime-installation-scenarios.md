---
title: Visual Studio Tools scenariuszy instalacji środowiska uruchomieniowego pakietu Office
description: Dowiedz się, jak zainstalować środowisko uruchomieniowe Visual Studio 2010 Tools for Office. W tym artykule opisano trzy scenariusze instalacji.
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
ms.openlocfilehash: 671d8e929ebef1085f0bf2aedad2a3280c36514c
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448340"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools scenariuszy instalacji środowiska uruchomieniowego pakietu Office

  Środowisko uruchomieniowe narzędzi Visual Studio 2010 Tools for Office można zainstalować na trzy sposoby:

- Podczas instalowania Visual Studio.

- Podczas instalowania Microsoft Office.

- Podczas instalowania pakietu redystrybucyjnego narzędzia Visual Studio 2010 Tools for Office.

  Zainstalowane składniki środowiska uruchomieniowego zależą od konfiguracji komputera i scenariusza instalacji.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Składniki środowiska uruchomieniowego instalowane w poszczególnych scenariuszach instalacji

 Środowisko uruchomieniowe narzędzia Visual Studio 2010 Tools for Office ma trzy składniki: modułu ładującego rozwiązanie pakietu Office, rozszerzenia pakietu Office dla wersji .NET Framework 3.5 i rozszerzenia pakietu Office dla programu lub [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nowszego. Podczas instalowania środowiska uruchomieniowego jest zawsze instalowany program ładujący rozwiązania pakietu Office. Instalacja rozszerzeń pakietu Office dla pakietu .NET Framework zależy od konfiguracji komputera i scenariusza instalacji. Jeśli nie można zainstalować jednego z rozszerzeń pakietu Office podczas pierwszej instalacji środowiska uruchomieniowego, środowisko uruchomieniowe automatycznie zainstaluje brakujące rozszerzenia pakietu Office później, gdy zostaną spełnione określone wymagania. Ta funkcja środowiska uruchomieniowego jest nazywana *instalowaniem na żądanie.*

 W poniższej tabeli przedstawiono, które składniki środowiska uruchomieniowego są instalowane domyślnie w każdym scenariuszu instalacji środowiska uruchomieniowego. Więcej informacji na temat poszczególnych scenariuszy zostanie wyświetlonych później.

|Scenariusz instalacji środowiska uruchomieniowego|Modułu ładującego rozwiązanie pakietu Office|Rozszerzenia pakietu Office dla .NET Framework 3.5|Rozszerzenia pakietu Office dla programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Rozszerzenia pakietu Office dla programu [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|Z [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] i nowszymi|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowany.|Tak|Tak|
|Z [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowany.|Nie|Nie|
|Z pakietem Office 2010 z dodatkiem Service Pack 1 (SP1) lub nowszym|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowany.|Tak, jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] program jest już zainstalowany.|Nie|
|Pakiet Office 2013 i nowsze|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowany|Tak, jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] program jest już zainstalowany.|Tak, jeśli [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] program jest już zainstalowany.|
|Z redystrybucją środowiska uruchomieniowego|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowany|Tak, jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] program jest już zainstalowany.|Tak, jeśli [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] program jest już zainstalowany.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Zainstaluj środowisko uruchomieniowe przy użyciu Visual Studio lub Microsoft Office Developer Tools for Visual Studio

 Podczas instalowania narzędzi deweloperskie pakietu Office w Visual Studio rozszerzenia pakietu Office dla i są zawsze instalowane [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] na komputerze dewelopera. Rozszerzenia pakietu Office dla programu .NET Framework 3.5 są instalowane tylko wtedy, gdy .NET Framework 3.5 jest już obecny na komputerze dewelopera. Jeśli zainstalujesz program .NET Framework 3.5 po zainstalowaniu programu , środowisko uruchomieniowe automatycznie zainstaluje rozszerzenia pakietu Office dla programu .NET Framework 3.5 przy pierwszym tworzeniu projektu pakietu Office, który jest przeznaczony dla programu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .NET Framework 3.5.

> [!WARNING]
> Nie można utworzyć projektu pakietu Office, który jest przeznaczony dla .NET Framework 3.5 przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] programu lub nowszego.

 Aby uzyskać więcej informacji na temat sposobu instalowania narzędzi deweloperskie pakietu Office, zobacz [How to: Configure a computer to develop Office solutions](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)( Jak skonfigurować komputer do tworzenia rozwiązań pakietu Office).

### <a name="install-the-runtime-with-office"></a>Instalowanie środowiska uruchomieniowego przy użyciu pakietu Office

 Podczas instalowania pakietu Office rozszerzenia pakietu Office dla programu .NET Framework 3.5 są instalowane, jeśli program .NET Framework 3.5 jest już zainstalowany na komputerze. Jeśli zainstalujesz pakiet .NET Framework 3.5 po psłudze Office, środowisko uruchomieniowe automatycznie zainstaluje rozszerzenia pakietu Office dla wersji .NET Framework 3.5 przy pierwszej próbie załadowania przez aplikację pakietu Office rozwiązania, które jest .NET Framework 3.5.

 Rozszerzenia pakietu Office dla programu lub nowszego są również instalowane z pakietem Office, jeśli odpowiednie wersje pakietu .NET Framework już istnieją [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] na komputerze.

 Aby upewnić się, że użytkownicy mają rozszerzenia niezbędne do korzystania z aplikacji, dołącz jako wymaganie wstępne pakietu redystrybucyjnego narzędzia Visual Studio 2010 Tools for Office runtime. Aby uzyskać więcej informacji na temat wymagań wstępnych, zobacz [Wymagania wstępne rozwiązania pakietu Office dotyczące wdrażania](/previous-versions/bb608617(v=vs.110)).

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Instalowanie środowiska uruchomieniowego przy użyciu pakietu redystrybucyjnego środowiska uruchomieniowego

 Środowisko uruchomieniowe można zainstalować, uruchamiając pakiet redystrybucyjny narzędzi programu Visual Studio 2010 Tools for Office ręcznie lub włączając pakiet redystrybucyjny jako wymaganie wstępne podczas wdrażania rozwiązania pakietu Office.

 W przypadku instalowania środowiska uruchomieniowego przy użyciu pakietu redystrybucyjnego narzędzia Visual Studio 2010 Tools for Office rozszerzenia pakietu Office dla wersji .NET Framework 3.5 i rozszerzenia pakietu Office dla programu lub nowszego są zainstalowane, jeśli odpowiednie wersje pakietu .NET Framework są już zainstalowane na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] komputerze. Jeśli na komputerze brakuje jednej z tych wersji programu .NET Framework podczas instalacji środowiska uruchomieniowego, rozszerzenia pakietu Office dla brakującej wersji pakietu .NET Framework nie zostaną zainstalowane w tym czasie. Jeśli później zainstalujesz brakującą wersję programu .NET Framework, środowisko uruchomieniowe automatycznie zainstaluje odpowiednie rozszerzenia pakietu Office przy następnej instalacji rozwiązania wymagającego rozszerzeń (jeśli środowisko uruchomieniowe zostało zainstalowane z rozwiązaniem wdrożonym za pomocą technologii ClickOnce) lub załadowane (jeśli środowisko uruchomieniowe zostało zainstalowane z rozwiązaniem wdrożonym przy użyciu programu Instalator Windows).

 Aby uzyskać więcej informacji na temat uwzględnienia wymagań wstępnych w rozwiązaniu ClickOnce, zobacz How [to: Install prerequisites](/previous-versions/bb608608(v=vs.110))on end user computers to run Office solutions . Aby uzyskać więcej informacji na temat ręcznego instalowania środowiska uruchomieniowego z pakietu redystrybucyjnego, zobacz Instalowania pakietu redystrybucyjnego [pakietu Visual Studio Tools pakietu office.](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

## <a name="see-also"></a>Zobacz też

- [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office — omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Zestawy w środowisku Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
