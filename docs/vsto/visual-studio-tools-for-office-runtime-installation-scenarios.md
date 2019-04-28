---
title: Visual Studio Tools dla pakietu Office Runtime ― scenariusze instalacji
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 507bce496405f615343a9c109ff71196d814af08
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438738"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools dla pakietu Office Runtime ― scenariusze instalacji
  Visual Studio 2010 Tools dla pakietu Office runtime można zainstalować na trzy sposoby:

- Po zainstalowaniu programu Visual Studio.

- Po zainstalowaniu programu Microsoft Office.

- Po zainstalowaniu programu Visual Studio 2010 Tools dla pakietu Office runtime pakiet redystrybucyjny.

  Składniki środowiska uruchomieniowego, które są instalowane są zależne od konfiguracji komputera i scenariusza instalacji.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Składniki środowiska uruchomieniowego, które są instalowane w każdym ze scenariuszy instalacji
 Visual Studio 2010 Tools dla pakietu Office runtime ma trzy składniki: modułu ładującego rozwiązanie Office, rozszerzeń pakietu Office dla programu .NET Framework 3.5 i rozszerzeń pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej. Podczas instalowania środowiska uruchomieniowego modułu ładującego rozwiązanie Office będzie zawsze instalowana. Instalacja rozszerzenia pakietu Office dla programu .NET Framework zależy od konfiguracji komputera i scenariusza instalacji. Jeśli jedno z rozszerzeń pakietu Office nie można zainstalować po zainstalowaniu środowiska uruchomieniowego, środowisko uruchomieniowe automatycznie zainstaluje brakujące rozszerzeń pakietu Office później, gdy są spełnione określone wymagania. Ta funkcja środowiska uruchomieniowego jest nazywana *zainstalować na żądanie*.

 W poniższej tabeli przedstawiono, które składniki środowiska uruchomieniowego są instalowane domyślnie w każdym ze scenariuszy instalacji środowiska uruchomieniowego. Więcej informacji na temat poszczególnych scenariuszy pojawi się później.

|Scenariusz instalacji środowiska uruchomieniowego|Modułu ładującego rozwiązania dla pakietu Office|Rozszerzenia pakietu Office dla programu .NET Framework 3.5|Rozszerzenia pakietu Office [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Rozszerzenia pakietu Office [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|Za pomocą [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] lub nowszy|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowany.|Tak|Yes|
|za pomocą [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowany.|Nie|Nie|
|Za pomocą dodatku Service Pack 1 (SP1) dla pakietu Office 2010 lub nowszy|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowany.|Tak, jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jest już zainstalowana.|Nie|
|Pakiet redystrybucyjny aparatu plików wykonywalnych|Yes|Tak, jeśli program .NET Framework 3.5 jest już zainstalowany.|Tak, jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jest już zainstalowana.|Tak, jeśli [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] jest już zainstalowana.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Instalowanie środowiska uruchomieniowego za pomocą programu Visual Studio lub Microsoft Office Developer Tools for Visual Studio
 Po zainstalowaniu narzędzia Office developer tools w programie Visual Studio i rozszerzeń pakietu Office dla [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] i [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] są zawsze instalowane na komputerze deweloperskim. Rozszerzenia pakietu Office dla programu .NET Framework 3.5 są instalowane tylko wtedy, gdy program .NET Framework 3.5 jest już obecny na komputerze deweloperskim. Jeśli program .NET Framework 3.5 należy zainstalować po zainstalowaniu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], środowisko uruchomieniowe automatycznie zainstaluje rozszerzenia pakietu Office dla programu .NET Framework 3.5 podczas pierwszego tworzenia projektu pakietu Office, który jest przeznaczony dla .NET Framework 3.5.

> [!WARNING]
> Nie można utworzyć projektu pakietu Office, który jest przeznaczony dla .NET Framework 3.5 przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] lub nowszej.

 Aby uzyskać więcej informacji o sposobie instalowania narzędzi Office developer tools, zobacz [jak: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

### <a name="install-the-runtime-with-office"></a>Instalowanie środowiska uruchomieniowego za pomocą pakietu Office
 Podczas instalowania pakietu Office rozszerzeń pakietu Office dla programu .NET Framework 3.5 są zainstalowane, jeśli program .NET Framework 3.5 jest już obecny na komputerze. Po zainstalowaniu programu .NET Framework 3.5 po pakietu Office, środowisko uruchomieniowe automatycznie zainstaluje rozszerzenia pakietu Office czas .NET Framework 3.5 w pierwszym, który próbuje załadować rozwiązanie przeznaczonego programu .NET Framework 3.5 aplikacji pakietu Office.

 Rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej nie są instalowane z pakietem Office, nawet jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej jest już obecny podczas instalowania pakietu Office.

 Rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] instalowanych z pakietu Office. Użytkownicy końcowi mogą uzyskać rozszerzeń pakietu Office dla [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] przez zainstalowanie aktualizacji Windows.

 Aby upewnić się, czy użytkownicy mają rozszerzeniami niezbędnymi do korzystania z aplikacji, należy uwzględnić najnowszą wersję programu Visual Studio 2010 Tools dla pakietu Office runtime pakiet redystrybucyjny jako warunek wstępny dla Twojego rozwiązania. Aby uzyskać więcej informacji na temat wymagań wstępnych, zobacz [wymagania wstępne rozwiązania pakietu Office wdrożenia](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e).

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Instalowanie środowiska uruchomieniowego przy użyciu środowiska uruchomieniowego do dystrybucji
 Można zainstalować środowisko uruchomieniowe, ręczne uruchomienie programu Visual Studio 2010 Tools dla pakietu Office runtime pakiet redystrybucyjny lub przez dołączenie do dystrybucji jako warunek wstępny, podczas wdrażania rozwiązania do pakietu Office.

 Po zainstalowaniu środowiska uruchomieniowego przy użyciu programu Visual Studio 2010 Tools for Office runtime pakiet redystrybucyjny, rozszerzeń pakietu Office dla programu .NET Framework 3.5 oraz rozszerzeń pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy jest zainstalowany, jeśli odpowiednie wersje programu .NET Framework jest już obecny na komputerze. Jeśli na komputerze brakuje jednej z tych wersji programu .NET Framework, po zainstalowaniu środowiska uruchomieniowego, w tym czasie nie są zainstalowane rozszerzenia pakietu Office dla brakującą wersję programu .NET Framework. Możesz zainstalować brakującą wersję programu .NET Framework później, środowisko uruchomieniowe automatycznie instaluje odpowiednie rozszerzeń pakietu Office przy następnym to rozwiązanie, które wymaga rozszerzeń zainstalowano (Jeśli środowisko wykonawcze został zainstalowany za pomocą rozwiązania, który został wdrożony przy użyciu technologii ClickOnce) lub załadować (Jeśli środowisko wykonawcze został zainstalowany za pomocą rozwiązania, który został wdrożony za pomocą Instalatora Windows).

 Aby uzyskać więcej informacji na temat wymagań wstępnych w tym w rozwiązaniu ClickOnce zobacz [jak: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98). Aby uzyskać więcej informacji o tym, jak ręcznie zainstalować środowisko uruchomieniowe z pakietu redystrybucyjnego, zobacz [jak: Zainstalować Visual Studio Tools for Office runtime pakiet redystrybucyjny](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).

## <a name="see-also"></a>Zobacz także
- [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Zestawy w Visual Studio Tools for Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
