---
title: Uruchom jako administrator
ms.date: 01/06/2020
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 927031b4755644aeac553367a4f8a08faa0c0992
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75718639"
---
# <a name="user-permissions-and-visual-studio"></a>Uprawnienia użytkownika i program Visual Studio

Ze względów bezpieczeństwa należy uruchomić program Visual Studio jako typowego użytkownika, gdy tylko jest to możliwe.

> [!WARNING]
> Należy również pamiętać, aby nie kompilować, uruchamiać lub debugować żadnego rozwiązania Visual Studio, które nie pochodzi od zaufanej osoby lub z zaufanej lokalizacji.

Można zrobić prawie wszystko w visual studio IDE jako typowego użytkownika. Do wykonania następujących zadań potrzebne są uprawnienia administratora:

|Obszar|Zadanie|Więcej informacji|
|----------|----------| - |
|Instalacja|Instalowanie lub modyfikowanie programu Visual Studio.|[Instalowanie programu Visual Studio](../install/install-visual-studio.md), [Modyfikowanie programu Visual Studio](../install/modify-visual-studio.md)|
||Zainstaluj, zaktualizuj lub usuń lokalną zawartość Pomocy.|[Instalowanie lokalnej zawartości Pomocy i zarządzanie nią](../help-viewer/install-manage-local-content.md)|
|Przybornik|Dodaj klasyczne kontrolki COM do **przybornika**.|[Przybornik](../ide/reference/toolbox.md)|
|Kompilowanie|Użyj zdarzeń po kompilacji, które rejestrują składnik.|[Opis niestandardowych kroków kompilacji i tworzenia zdarzeń](/cpp/build/understanding-custom-build-steps-and-build-events)|
||Dołącz krok rejestracji podczas tworzenia projektów języka C++.||
|Debugging|Debugowanie aplikacji, które są uruchamiane z podwyższonym poziomem uprawnień.|[Ustawienia i przygotowanie debugera](../debugger/debugger-settings-and-preparation.md)|
||Debugowanie aplikacji uruchamianych przy różnych kontach użytkownika, takich jak ASP.NET witrynach sieci Web.|[Aplikacje ASP.NET debugowania i AJAX](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||Debugowanie w strefie dla aplikacji przeglądarki XAML (XBAP).|[Host WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Użyj emulatora do debugowania projektów usług w chmurze dla platformy Microsoft Azure.|[Debugowanie usługi w chmurze w programie Visual Studio](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Konfigurowanie zapory do zdalnego debugowania.|[Debugowanie zdalne](../debugger/remote-debugging.md)|
|Narzędzia wydajności|Dołączanie do aplikacji z podwyższonym poziomem uprawnień.|[Przewodnik dla początkujących do profilowania wydajności](../profiling/beginners-guide-to-performance-profiling.md)|
||Użyj profilera GPU.|[Profilowanie gpu](../profiling/gpu-usage.md)|
|Wdrożenie|Wdrażanie aplikacji sieci web w internetowych usługach informacyjnych (IIS) na komputerze lokalnym.|[Wdrażanie ASP.NET aplikacji sieci Web przy użyciu programu Visual Studio](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Uruchamianie programu Visual Studio jako administrator

Jeśli chcesz uruchomić program Visual Studio jako administrator, wykonaj następujące kroki, aby otworzyć IDE:

> [!NOTE]
> Te instrukcje są dla systemu Windows 10. Są one podobne dla innych wersji systemu Windows.

::: moniker range="vs-2017"

1. Otwórz menu **Start** i przewiń do programu Visual Studio 2017.

1. Z menu po kliknięciu prawym przyciskiem myszy lub menu kontekstowego **programu Visual Studio 2017**wybierz pozycję **Więcej** > **uruchom jako administrator**.

   Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz menu **Start** i przewiń do programu Visual Studio 2019.

1. Z menu po kliknięciu prawym przyciskiem myszy lub menu kontekstowego **programu Visual Studio 2019**wybierz pozycję **Więcej** > **uruchom jako administrator**.

   Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

::: moniker-end

Można również zmodyfikować skrót aplikacji, aby zawsze działać z uprawnieniami administracyjnymi.

## <a name="see-also"></a>Zobacz też

- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Instalacja programu Visual Studio](../install/install-visual-studio.md)
