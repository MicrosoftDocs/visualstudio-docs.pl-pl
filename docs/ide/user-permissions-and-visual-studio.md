---
title: Uruchom jako administrator
description: Dowiedz się, jak uruchomić program Visual Studio jako administrator.
ms.date: 03/09/2021
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3d2a22533137bf2c1f2e7cfeb3802f5824c3926
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607252"
---
# <a name="user-permissions-and-visual-studio"></a>Uprawnienia użytkownika i program Visual Studio

Ze względów bezpieczeństwa należy uruchomić program Visual Studio jako typowy użytkownik, jeśli jest to możliwe.

> [!WARNING]
> Należy również pamiętać, aby nie kompilować, uruchamiać lub debugować żadnego rozwiązania Visual Studio, które nie pochodzi od zaufanej osoby lub z zaufanej lokalizacji.

Niemal wszystko w środowisku IDE programu Visual Studio można wykonać jako typowy użytkownik. Musisz mieć uprawnienia administratora, aby wykonać następujące zadania:

|Warstwowy|Zadanie|Więcej informacji|
|----------|----------| - |
|Instalacja|Zainstaluj lub zmodyfikuj program Visual Studio.|[Zainstaluj program Visual Studio](../install/install-visual-studio.md), [zmodyfikuj program Visual Studio](../install/modify-visual-studio.md)|
||Instalowanie, aktualizowanie lub usuwanie lokalnej zawartości pomocy.|[Instalowanie zawartości pomocy lokalnej i zarządzanie nią](../help-viewer/install-manage-local-content.md)|
|Przybornik|Dodawanie klasycznych kontrolek COM do **przybornika**.|[Przybornik](../ide/reference/toolbox.md)|
|Kompilowanie|Użyj zdarzeń po kompilacji, które rejestrują składnik.|[Zrozumienie niestandardowych kroków kompilacji i zdarzeń kompilacji](/cpp/build/understanding-custom-build-steps-and-build-events)|
||Uwzględnij etap rejestracji podczas kompilowania projektów języka C++.||
|Debugowanie|Debuguj aplikacje, które działają z podniesionymi uprawnieniami.|[Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)|
||Debuguj aplikacje, które działają na innym koncie użytkownika, takich jak ASP.NET websites.|[Debuguj aplikacje ASP.NET i AJAX](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||Debugowanie w strefie dla aplikacji przeglądarki XAML (XBAP).|[Host WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Użyj emulatora do debugowania projektów usług w chmurze dla Microsoft Azure.|[Debugowanie usługi w chmurze w programie Visual Studio](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Skonfiguruj zaporę do zdalnego debugowania.|[Debugowanie zdalne](../debugger/remote-debugging.md)|
|Narzędzia wydajności|Dołączanie do aplikacji z podwyższonym poziomem uprawnień.|[Początkujący Przewodnik dotyczący profilowania wydajności](../profiling/beginners-guide-to-performance-profiling.md)|
||Użyj profilera procesora GPU.|[Profilowanie procesora GPU](../profiling/gpu-usage.md)|
|Wdrożenie|Wdróż aplikację sieci Web do Internet Information Services (IIS) na komputerze lokalnym.|[Wdrażanie aplikacji sieci Web ASP.NET przy użyciu programu Visual Studio](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Uruchom program Visual Studio jako administrator

Jeśli musisz uruchomić program Visual Studio jako administrator, wykonaj następujące kroki, aby otworzyć środowisko IDE:

> [!NOTE]
> Te instrukcje dotyczą systemu Windows 10. Są one podobne do innych wersji systemu Windows.

::: moniker range="vs-2017"

1. Otwórz menu **Start** i przewiń do programu Visual Studio 2017.

1. Z menu kontekstowego kliknij prawym przyciskiem myszy lub w **programie Visual Studio 2017** wybierz polecenie **więcej** > **Uruchom jako administrator**.

   Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz menu **Start** i przewiń do programu Visual Studio 2019.

1. Z menu kontekstowego kliknij prawym przyciskiem myszy lub w **programie Visual Studio 2019** wybierz polecenie **więcej** > **Uruchom jako administrator**.

   Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

::: moniker-end

Możesz również zmodyfikować skrót aplikacji, aby zawsze był uruchamiany z uprawnieniami administracyjnymi:

1. Otwórz menu **Start** , przewiń do używanej wersji programu Visual Studio, a następnie wybierz polecenie **więcej**  >  **otwartej lokalizacji pliku**.

1. W **Eksploratorze plików** Znajdź skrót programu **Visual Studio** dla używanej wersji. Następnie kliknij prawym przyciskiem myszy skrót i wybierz polecenie **Wyślij do**  >  **pulpitu (Utwórz skrót)**.

1. Na pulpicie **systemu Windows** kliknij prawym przyciskiem myszy skrót **programu Visual Studio** , a następnie wybierz polecenie **Właściwości**.

1. Wybierz przycisk **Zaawansowane** , a następnie zaznacz pole wyboru **Uruchom jako administrator** .

1. Wybierz przycisk **OK**, a następnie ponownie wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz też

- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Instalowanie programu Visual Studio](../install/install-visual-studio.md)
