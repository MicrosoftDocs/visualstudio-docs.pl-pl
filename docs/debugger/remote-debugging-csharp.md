---
title: Zdalne debugowanie projektu C# lub VB | Dokumenty firmy Microsoft
ms.custom:
- remotedebugging"=
- seodec18
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f147acae956ad380c6e85984de29d5316394c0a
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302099"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Zdalne debugowanie projektu języka C# lub Visual Basic w programie Visual Studio
Aby debugować aplikację programu Visual Studio, która została wdrożona na innym komputerze, zainstaluj i uruchom narzędzia zdalne na komputerze, na którym wdrożono aplikację, skonfiguruj projekt tak, aby łączył się z komputerem zdalnym z programu Visual Studio, a następnie uruchom aplikację.

![Składniki zdalnego debugera](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Aby uzyskać informacje dotyczące zdalnego debugowania uniwersalnych aplikacji systemu Windows (UWP), zobacz [Debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md).

## <a name="requirements"></a>Wymagania

Debuger zdalny jest obsługiwany w systemie Windows 7 i nowszym (nie telefon) oraz wersjach systemu Windows Server, począwszy od systemu Windows Server 2008 z dodatkiem Service Pack 2. Aby uzyskać pełną listę wymagań, zobacz [Wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debugowanie między dwoma komputerami podłączonymi za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem połączenia o dużej masie lub niskiej przepustowości, takiego jak dialup Internet lub przez Internet w różnych krajach, nie jest zalecane i może zakończyć się niepowodzeniem lub być niedopuszczalnie powolne.

## <a name="download-and-install-the-remote-tools"></a>Pobieranie i instalowanie narzędzi zdalnych

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> W niektórych scenariuszach może być najbardziej efektywne uruchomienie zdalnego debugera z udziału plików. Aby uzyskać więcej informacji, zobacz [Uruchamianie zdalnego debugera z udziału plików](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli chcesz dodać uprawnienia dla dodatkowych użytkowników, zmień tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a>Zdalne debugowanie projektu
Debuger nie może wdrożyć aplikacji pulpitu Visual C# lub Visual Basic na komputerze zdalnym, ale nadal można je debugować zdalnie w następujący sposób. Poniższa procedura zakłada, że chcesz debugować go na komputerze o nazwie **MJO-DL**, jak pokazano na poniższej ilustracji.

1. Utwórz projekt WPF o nazwie **MyWpf**.

2. Ustaw punkt przerwania gdzieś w kodzie, który jest łatwo dostępny.

    Na przykład można ustawić punkt przerwania w programie obsługi przycisków. Aby to zrobić, otwórz mainwindow.xaml i dodaj button kontrolki z przybornika, a następnie kliknij dwukrotnie przycisk, aby otworzyć go obsługi.

3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

4. Na stronie **Właściwości** wybierz kartę **Debugowanie.**

    ![RemoteDebuggerCSharp (RemoteDebuggerCSharp)](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp (RemoteDebuggerCSharp)")

5. Upewnij się, że pole **tekstowe katalogu roboczego** jest puste.

6. Wybierz **pozycję Użyj komputera zdalnego**i wpisz **swójnazyna nazwa:port** w polu tekstowym. (Numer portu jest wyświetlany w oknie zdalnego debugera. Numer portu zwiększa się o 2 w każdej wersji programu Visual Studio).

    W tym przykładzie użyj:
    ::: moniker range=">=vs-2019"
    **MJO-DL:4024** w programie Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL:4022** w programie Visual Studio 2017
    ::: moniker-end

7. Upewnij się, że **włącz debugowanie kodu macierzystego** nie jest zaznaczona.

8. Skompiluj projekt.

9. Utwórz folder na komputerze zdalnym, który jest tą samą ścieżką co folder **Debugowania** na komputerze programu Visual Studio: ** \<ścieżka źródłowa>\MyWPF\MyWPF\bin\Debug**.

10. Skopiuj plik wykonywalny utworzony z komputera programu Visual Studio do nowo utworzonego folderu na komputerze zdalnym.

    > [!CAUTION]
    > Nie należy wprowadzać zmian w kodzie lub przebudować (lub należy powtórzyć ten krok). Plik wykonywalny skopiowany na komputer zdalny musi dokładnie odpowiadać lokalnemu źródłu i symbolom.

    Projekt można skopiować ręcznie, użyć xcopy, robocopy, powershell lub innych opcji.

11. Upewnij się, że zdalny debuger jest uruchomiony na komputerze docelowym (Jeśli tak nie jest, wyszukaj **debuger zdalny** w menu **Start).** Okno zdalnego debugera wygląda następująco.

     ![Funkcja RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "Funkcja RemoteDebuggerWindow")

12. W programie Visual Studio rozpocznij debugowanie (**Debug > Rozpocznij debugowanie**lub **F5**).

13. Jeśli zostanie wyświetlony monit, wprowadź poświadczenia sieci, aby połączyć się z komputerem zdalnym.

     Wymagane poświadczenia różnią się w zależności od konfiguracji zabezpieczeń sieci. Na przykład na komputerze domeny można wprowadzić nazwę domeny i hasło. Na komputerze spoza domeny można wprowadzić nazwę komputera i prawidłową <strong>MJO-DL\name@something.com</strong>nazwę konta użytkownika, na przykład , wraz z poprawnym hasłem.

     Należy zobaczyć, że główne okno aplikacji WPF jest otwarte na komputerze zdalnym.

14. Jeśli to konieczne, podjąć działania, aby trafić punkt przerwania. Powinien zostać wyświetlony, że punkt przerwania jest aktywny. Jeśli tak nie jest, symbole aplikacji nie zostały załadowane. Ponów próbę, a jeśli to nie zadziała, uzyskaj informacje o ładowaniu symboli i sposobie rozwiązywania problemów z nimi w [sekcji Opis plików symboli i ustawień symboli programu Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. Na komputerze visual studio, powinien zostać wyświetlony, że wykonanie zostało zatrzymane w punkcie przerwania.

    Jeśli masz żadnych plików innych niż kod, które muszą być używane przez aplikację, należy dołączyć je w projekcie programu Visual Studio. Utwórz folder projektu dla dodatkowych plików (w **Eksploratorze rozwiązań**kliknij pozycję **Dodaj > Nowy folder**). Następnie dodaj pliki do folderu (w **Eksploratorze rozwiązań**kliknij pozycję **Dodaj > istniejący element**, a następnie zaznacz pliki). Na stronie **Właściwości** dla każdego pliku ustaw **opcję Kopiuj do katalogu wyjściowego,** aby **zawsze kopiować**.

## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania za pomocą symboli zdalnych

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Zobacz też
- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Konfigurowanie Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remote Debugger Port Assignments (Przypisania portów zdalnego debugera)](../debugger/remote-debugger-port-assignments.md)
- [Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)