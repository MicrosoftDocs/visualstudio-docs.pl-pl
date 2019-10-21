---
title: Uruchom jako administrator
ms.date: 06/05/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6086485ef20330de7971297f52a112d5183ee4a2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647346"
---
# <a name="user-permissions-and-visual-studio"></a>Uprawnienia użytkownika i program Visual Studio

Ze względów bezpieczeństwa należy uruchomić program Visual Studio jako zwykły użytkownik, jeśli jest to możliwe.

> [!WARNING]
> Należy również pamiętać, aby nie kompilować, uruchamiać lub debugować żadnego rozwiązania Visual Studio, które nie pochodzi od zaufanej osoby lub z zaufanej lokalizacji.

Niemal wszystko to można zrobić w środowisku IDE programu Visual Studio jako zwykły użytkownik. Musisz mieć uprawnienia administratora, aby wykonać następujące zadania:

|Obszar|Zadanie|Więcej informacji|
|----------|----------| - |
|Instalacja|Zainstaluj program Visual Studio.|[Instalowanie programu Visual Studio](../install/install-visual-studio.md)|
||Instalowanie, aktualizowanie lub usuwanie lokalnej zawartości pomocy.|[Instalowanie zawartości pomocy lokalnej i zarządzanie nią](../help-viewer/install-manage-local-content.md)|
|Przybornik|Dodawanie klasycznych kontrolek COM do **przybornika**.|[Przybornik](../ide/reference/toolbox.md)|
|Kompilowanie|Użyj zdarzeń po kompilacji, które rejestrują składnik.|[Zrozumienie niestandardowych kroków kompilacji i zdarzeń kompilacji](/cpp/build/understanding-custom-build-steps-and-build-events)|
||Uwzględnij etap rejestracji podczas kompilowania C++ projektów.||
|Debugowanie|Debuguj aplikacje, które działają z podniesionymi uprawnieniami.|[Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)|
||Debuguj aplikacje, które działają na innym koncie użytkownika, takich jak ASP.NET websites.|[Debuguj aplikacje ASP.NET i AJAX](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||Debugowanie w strefie dla aplikacji przeglądarki XAML (XBAP).|[Host WPF (PresentationHost. exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Użyj emulatora do debugowania projektów usług w chmurze dla Microsoft Azure.|[Debugowanie usługi w chmurze w programie Visual Studio](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Skonfiguruj zaporę do zdalnego debugowania.|[Debugowanie zdalne](../debugger/remote-debugging.md)|
|Narzędzia wydajności|Dołączanie do aplikacji z podwyższonym poziomem uprawnień.|[Początkujący Przewodnik dotyczący profilowania wydajności](../profiling/beginners-guide-to-performance-profiling.md)|
||Użyj profilera procesora GPU.|[Profilowanie procesora GPU](../profiling/gpu-usage.md)|
|wdrażania|Wdróż aplikację sieci Web do Internet Information Services (IIS) na komputerze lokalnym.|[Wdrażanie aplikacji sieci Web ASP.NET przy użyciu programu Visual Studio](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Uruchom program Visual Studio jako administrator

Jeśli musisz uruchomić program Visual Studio jako administrator, wykonaj następujące kroki, aby otworzyć środowisko IDE:

> [!NOTE]
> Te instrukcje dotyczą systemu Windows 10. Są one podobne do innych wersji systemu Windows.

::: moniker range="vs-2017"

1. Otwórz menu **Start** i przewiń do programu Visual Studio 2017.

1. W menu kontekstowym kliknij prawym przyciskiem myszy lub w **programie Visual Studio 2017**wybierz polecenie **więcej** > **Uruchom jako administrator**.

   Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz menu **Start** i przewiń do programu Visual Studio 2019.

1. W menu kontekstowym kliknij prawym przyciskiem myszy lub w **programie Visual Studio 2019**wybierz polecenie **więcej** > **Uruchom jako administrator**.

   Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

::: moniker-end

Możesz również zmodyfikować skrót aplikacji, aby zawsze był uruchamiany z uprawnieniami administracyjnymi.

## <a name="see-also"></a>Zobacz także

- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Instalowanie programu Visual Studio](../install/install-visual-studio.md)