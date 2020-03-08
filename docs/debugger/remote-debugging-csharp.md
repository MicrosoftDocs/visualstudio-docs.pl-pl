---
title: Zdalne debugowanie C# lub projektu VB | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409385"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Zdalne debugowanie projektu C# lub Visual Basic w programie Visual Studio
Aby debugować aplikację programu Visual Studio, która została wdrożona na innym komputerze, zainstalować i uruchomić narzędzia zdalne na komputerze, w której została wdrożona aplikacja, skonfiguruj projekt, aby nawiązać połączenie z komputerem zdalnym z programu Visual Studio, a następnie uruchom aplikację.

![Składniki debugera zdalnego](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Aby uzyskać informacje o zdalnym debugowaniu aplikacji systemu Windows (platformy UWP), zobacz [debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md).

## <a name="requirements"></a>Wymagania

Zdalny debuger jest obsługiwane w systemie Windows 7 lub nowszej (nie phone) i wersji systemu Windows Server, począwszy od systemu Windows Server 2008 Service Pack 2. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debugowanie między dwoma komputerami połączonymi za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem duże opóźnienie lub połączenia o niskiej przepustowości, takich jak Internet, połączenia telefonicznego lub przez Internet między krajów nie jest zalecane i może zakończyć się niepowodzeniem lub zbyt wolno.

## <a name="download-and-install-the-remote-tools"></a>Pobieranie i instalowanie narzędzi zdalnych

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> W niektórych scenariuszach może być najbardziej efektywny, aby uruchomić zdalny debuger z udziału plików. Aby uzyskać więcej informacji, zobacz [Uruchamianie zdalnego debugera z udziału plików](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli musisz dodać uprawnienia dla dodatkowych użytkowników, zmienić tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie zdalnego debugera](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_csharp"></a>Debugowanie zdalne projektu
Debuger nie można wdrożyć aplikacje klasyczne Visual C# lub Visual Basic do maszyny zdalnej, ale możesz nadal możesz debugować je zdalnie, w następujący sposób. W poniższej procedurze przyjęto założenie, że chcesz debugować ją na komputerze o nazwie **MJO-DL**, jak pokazano na poniższej ilustracji.

1. Utwórz projekt WPF o nazwie **MyWpf**.

2. Ustaw punkt przerwania w jakimś miejscu w kodzie, który łatwo zostanie osiągnięty.

    Na przykład można ustawić punkt przerwania w obsłudze przycisku. Aby to zrobić, otwórz MainWindow.xaml, Dodaj kontrolkę przycisk z przybornika, a następnie kliknij dwukrotnie przycisk aby otworzyć jego obsługi.

3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

4. Na stronie **Właściwości** wybierz kartę **debugowanie** .

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. Upewnij się, że pole tekstowe **katalog roboczy** jest puste.

6. Wybierz opcję **Użyj maszyny zdalnej**i wpisz **yourmachinename: Port** w polu tekstowym. (Numer portu jest wyświetlany w oknie debugera zdalnego. Numer portu zwiększa wartość 2, w każdej wersji programu Visual Studio).

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

10. Skopiuj plik wykonywalny, który właśnie zbudowany z komputera programu Visual Studio do nowo utworzonego folderu na komputerze zdalnym.

    > [!CAUTION]
    > Nie należy wprowadzać zmian w kodzie lub ponownej kompilacji lub należy powtórzyć ten krok. Plik wykonywalny, który został skopiowany na komputerze zdalnym musi dokładnie odpowiadać, lokalne źródła i symboli.

    Można ręcznie skopiować projektu, użyj polecenia Xcopy, Robocopy, programu Powershell lub innych opcji.

11. Upewnij się, że zdalny debuger jest uruchomiony na maszynie docelowej (jeśli nie, Wyszukaj **zdalny debuger** w menu **Start** ). W oknie debugera zdalnego wygląda następująco.

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. W programie Visual Studio Rozpocznij debugowanie (**debuguj > Rozpocznij debugowanie**lub **F5**).

13. Po wyświetleniu monitu wprowadź poświadczenia sieci, aby nawiązać połączenie z komputerem zdalnym.

     Wymagane poświadczenia różnią się w zależności od konfiguracji zabezpieczeń w sieci. Na przykład na komputerze domeny można wprowadzić nazwę domeny i hasła. Na komputerze niebędącym domeną możesz wprowadzić nazwę komputera i prawidłową nazwę konta użytkownika, taką jak <strong>MJO-DL\name@something.com</strong>, wraz z prawidłowym hasłem.

     Powinieneś zobaczyć, że okna głównego aplikacji WPF jest otwarty na komputerze zdalnym.

14. Jeśli to konieczne, należy podjąć działania w celu trafiony punkt przerwania. Powinieneś zobaczyć, czy punkt przerwania jest aktywny. Jeśli nie, nie zostały załadowane symbole dla aplikacji. Ponów próbę, a jeśli to nie zadziała, Uzyskaj informacje o ładowaniu symboli i sposobach ich rozwiązywania przy [zrozumieniu plików symboli i ustawień symboli programu Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. Na komputerze programu Visual Studio powinien zostać wyświetlony, że wykonywanie zostało zatrzymane w punkcie przerwania.

    Jeśli masz wszystkie pliki niezawierające kodu, które będzie używane przez aplikację, należy je uwzględnić w projekcie programu Visual Studio. Utwórz folder projektu dla dodatkowych plików (w **Eksplorator rozwiązań**kliknij pozycję **Dodaj > nowy folder**). Następnie Dodaj pliki do folderu (w **Eksplorator rozwiązań**kliknij pozycję **Dodaj > istniejący element**, a następnie wybierz pliki). Na stronie **Właściwości** każdego pliku ustaw opcję **Kopiuj do katalogu wyjściowego** na wartość **Kopiuj zawsze**.

## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania przy użyciu zdalnego symboli

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Zobacz też
- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remote Debugger Port Assignments (Przypisania portów zdalnego debugera)](../debugger/remote-debugger-port-assignments.md)
- [Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)