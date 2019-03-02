---
title: Uruchom jako administrator
ms.date: 06/05/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 229b1606a8a7de18da7354852e3e5adb9123f5b5
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222862"
---
# <a name="user-permissions-and-visual-studio"></a>Uprawnienia użytkownika i program Visual Studio

Ze względów bezpieczeństwa należy uruchomić program Visual Studio jako zwykły użytkownik zawsze, gdy jest to możliwe.

> [!WARNING]
> Należy również pamiętać, aby nie kompilować, uruchamiać lub debugować żadnego rozwiązania Visual Studio, które nie pochodzi od zaufanej osoby lub z zaufanej lokalizacji.

Możesz tworzyć prawie wszystko w środowisku IDE programu Visual Studio jako zwykły użytkownik. Musisz mieć uprawnienia administratora w celu wykonania następujących zadań:

|Obszar|Zadanie|Więcej informacji|
|----------|----------| - |
|Instalacja|Zainstaluj program Visual Studio.|[Instalowanie programu Visual Studio](../install/install-visual-studio.md)|
||Instalowanie, aktualizowanie lub usuwanie lokalnej zawartości pomocy.|[Instalowanie i zarządzania lokalną zawartością Pomocy](../help-viewer/install-manage-local-content.md)|
|Przybornik|Dodawanie klasycznych formantów COM do **przybornika**.|[Przybornik](../ide/reference/toolbox.md)|
|Kompilowanie|Użyj zdarzenia mające miejsce po kompilacji, które rejestrują składnik.|[Omówienie niestandardowych kroków kompilacji i zdarzenia kompilacji](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||Obejmują etapu rejestracji podczas kompilowania projektów języka C++.||
|Debugowanie|Debugowanie aplikacji, które działają z podwyższonymi uprawnieniami.|[Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)|
||Debugowanie aplikacji, które działają innego użytkownika konta, takich jak witryny sieci Web platformy ASP.NET.|[Debugowanie aplikacji ASP.NET i AJAX](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||Debugowanie w strefie dla aplikacji przeglądarki XAML (XBAP).|[Host WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Korzystanie z emulatora do debugowania projektów usług w chmurze dla systemu Microsoft Azure.|[Debugowanie usługi w chmurze w programie Visual Studio](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Konfigurowanie zapory dla zdalnego debugowania.|[Debugowanie zdalne](../debugger/remote-debugging.md)|
|Narzędzia wydajności|Profilowanie aplikacji.|[Profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md)|
|wdrażania|Wdrażanie aplikacji sieci web do programu Internet Information Services (IIS) na komputerze lokalnym.|[Wdrażanie aplikacji sieci web ASP.NET przy użyciu programu Visual Studio](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Uruchom program Visual Studio jako administrator

Jeśli musisz uruchomić program Visual Studio jako administrator, wykonaj następujące kroki, aby otworzyć środowiska IDE:

> [!NOTE]
> Te instrukcje dotyczą systemu Windows 10. Są one podobne do innych wersji systemu Windows.

::: moniker range="vs-2017"

1. Otwórz **Start** menu, a następnie przewiń do programu Visual Studio 2017.

1. Z menu kliknij prawym przyciskiem myszy lub kontekst **programu Visual Studio 2017**, wybierz opcję **więcej** > **Uruchom jako administrator**.

   Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz **Start** menu, a następnie przewiń do programu Visual Studio 2019 r.

1. Z menu kliknij prawym przyciskiem myszy lub kontekst **Visual Studio 2019**, wybierz opcję **więcej** > **Uruchom jako administrator**.

   Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

::: moniker-end

Możesz również zmodyfikować skrót aplikacji, aby zawsze uruchamiane z uprawnieniami administracyjnymi.

## <a name="see-also"></a>Zobacz także

- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Instalowanie programu Visual Studio](../install/install-visual-studio.md)