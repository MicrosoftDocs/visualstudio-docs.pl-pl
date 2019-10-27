---
title: Debugowanie zdalne a C# lub projekt VB | Microsoft Docs
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
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730260"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Debugowanie zdalne a C# lub Visual Basic projektu w programie Visual Studio
Aby debugować aplikację programu Visual Studio, która została wdrożona na innym komputerze, zainstaluj i Uruchom narzędzia zdalne na komputerze, na którym została wdrożona aplikacja, skonfiguruj projekt w celu nawiązania połączenia z komputerem zdalnym z programu Visual Studio, a następnie uruchom aplikację.

![Składniki debugera zdalnego](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Aby uzyskać informacje o zdalnym debugowaniu aplikacji systemu Windows (platformy UWP), zobacz [debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md).

## <a name="requirements"></a>Wymagania

Zdalny debuger jest obsługiwany w systemie Windows 7 i nowszych (nie Phone) oraz wersjach systemu Windows Server począwszy od systemu Windows Server 2008 z dodatkiem Service Pack 2. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debugowanie między dwoma komputerami połączonymi za pomocą serwera proxy nie jest obsługiwane. Debugowanie w przypadku dużych opóźnień lub połączeń o niskiej przepustowości, takich jak Internet telefoniczny lub przez Internet w różnych krajach, nie jest zalecane i może się nie powieść.

## <a name="download-and-install-the-remote-tools"></a>Pobieranie i Instalowanie narzędzi zdalnych

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> W niektórych scenariuszach może być najbardziej wydajne uruchamianie zdalnego debugera z udziału plików. Aby uzyskać więcej informacji, zobacz [Uruchamianie zdalnego debugera z udziału plików](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli musisz dodać uprawnienia dla dodatkowych użytkowników, zmienić tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie zdalnego debugera](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_csharp"></a>Debugowanie zdalne projektu
Debuger nie może wdrożyć aplikacji C# wizualnych lub Visual Basic na komputerze zdalnym, ale nadal można debugować je zdalnie w następujący sposób. W poniższej procedurze przyjęto założenie, że chcesz debugować ją na komputerze o nazwie **MJO-DL**, jak pokazano na poniższej ilustracji.

1. Utwórz projekt WPF o nazwie **MyWpf**.

2. Ustaw punkt przerwania w miejscu w kodzie, który jest łatwo osiągalny.

    Na przykład można ustawić punkt przerwania w obsłudze przycisku. Aby to zrobić, Otwórz MainWindow. XAML i Dodaj kontrolkę Button z przybornika, a następnie kliknij dwukrotnie przycisk, aby otworzyć jego program obsługi.

3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

4. Na stronie **Właściwości** wybierz kartę **debugowanie** .

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. Upewnij się, że pole tekstowe **katalog roboczy** jest puste.

6. Wybierz opcję **Użyj maszyny zdalnej**i wpisz **yourmachinename: Port** w polu tekstowym. (Numer portu jest wyświetlany w oknie debugera zdalnego. Numer portu jest zwiększany 2 w każdej wersji programu Visual Studio).

    W tym przykładzie Użyj:
    ::: moniker range=">=vs-2019"
    **MJO-DL: 4024** w programie Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL: 4022** w programie Visual Studio 2017
    ::: moniker-end

7. Upewnij się, że nie wybrano **debugowania kodu natywnego** .

8. Skompiluj projekt.

9. Utwórz folder na komputerze zdalnym, który jest tą samą ścieżką jak folder **debugowania** na komputerze programu Visual Studio: **\<ścieżka źródłowa > \MyWPF\MyWPF\bin\Debug**.

10. Skopiuj plik wykonywalny, który został utworzony z komputera programu Visual Studio, do nowo utworzonego folderu na komputerze zdalnym.

    > [!CAUTION]
    > Nie wprowadzaj zmian w kodzie ani nie Kompiluj ponownie (lub musisz powtórzyć ten krok). Plik wykonywalny skopiowany na komputer zdalny musi dokładnie pasować do lokalnego źródła i symboli.

    Projekt można skopiować ręcznie, użyć polecenia xcopy, Robocopy, PowerShell lub innych opcji.

11. Upewnij się, że zdalny debuger jest uruchomiony na maszynie docelowej (jeśli nie, Wyszukaj **zdalny debuger** w menu **Start** ). Okno debugera zdalnego wygląda następująco.

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. W programie Visual Studio Rozpocznij debugowanie (**debuguj > Rozpocznij debugowanie**lub **F5**).

13. Jeśli zostanie wyświetlony monit, wprowadź poświadczenia sieciowe, aby nawiązać połączenie z maszyną zdalną.

     Wymagane poświadczenia różnią się w zależności od konfiguracji zabezpieczeń sieci. Na przykład na komputerze domeny można wprowadzić nazwę domeny i hasło. Na komputerze niebędącym domeną możesz wprowadzić nazwę komputera i prawidłową nazwę konta użytkownika, taką jak <strong>MJO-DL\name@something.com</strong>, wraz z prawidłowym hasłem.

     Powinno zostać wyświetlone okno główne aplikacji WPF na komputerze zdalnym.

14. W razie potrzeby podejmij działanie, aby trafić w punkt przerwania. Powinieneś zobaczyć, że punkt przerwania jest aktywny. Jeśli tak nie jest, nie załadowano symboli aplikacji. Ponów próbę, a jeśli to nie zadziała, Uzyskaj informacje o ładowaniu symboli i sposobach ich rozwiązywania przy [zrozumieniu plików symboli i ustawień symboli programu Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. Na maszynie programu Visual Studio powinno być widoczne, że wykonywanie zostało zatrzymane w punkcie przerwania.

    Jeśli masz jakiekolwiek pliki niebędące kodem, które muszą być używane przez aplikację, musisz je uwzględnić w projekcie programu Visual Studio. Utwórz folder projektu dla dodatkowych plików (w **Eksplorator rozwiązań**kliknij pozycję **Dodaj > nowy folder**). Następnie Dodaj pliki do folderu (w **Eksplorator rozwiązań**kliknij pozycję **Dodaj > istniejący element**, a następnie wybierz pliki). Na stronie **Właściwości** każdego pliku ustaw opcję **Kopiuj do katalogu wyjściowego** na wartość **Kopiuj zawsze**.

## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania ze zdalnymi symbolami

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Zobacz także
- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Przypisania portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md)
- [Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)