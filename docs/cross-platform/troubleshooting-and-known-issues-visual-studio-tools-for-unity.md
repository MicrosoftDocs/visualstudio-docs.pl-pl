---
title: Rozwiązywanie problemów i znane problemy (narzędzia VS Tools for Unity)
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 7858846585467de3b5b820902938d6019b0d09ff
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386267"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Rozwiązywanie problemów i znane problemy (Visual Studio Tools for Unity)

W tej sekcji znajdziesz rozwiązania typowych problemów dotyczących Visual Studio Tools for Unity, opisy znanych problemów i informacje ułatwiające ulepszanie Visual Studio Tools for Unity przez raportowanie błędów.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Rozwiązywanie problemów z połączeniem między programem Unity i programem Visual Studio

### <a name="confirm-editor-attaching-is-enabled"></a>Potwierdzenie dołączenia edytora jest włączone

W menu aparatu Unity wybierz pozycję **edytuj > preferencje** , a następnie wybierz kartę **narzędzia zewnętrzne** . Upewnij się, że pole wyboru **dołączania edytora** jest włączone. Aby uzyskać więcej informacji, zobacz [dokumentację preferencji aparatu Unity](https://docs.unity3d.com/Manual/Preferences.html).

### <a name="unable-to-attach"></a>Nie można dołączyć

- Spróbuj tymczasowo wyłączyć program antywirusowy lub utworzyć reguły wykluczania dla programów VS i Unity.
- Spróbuj tymczasowo wyłączyć zaporę lub utworzyć reguły zezwalające na obsługę sieci TCP/UDP między programami VS i Unity.
- Niektóre programy, takie jak Team Viewer, mogą zakłócać wykrywanie procesów. Możesz spróbować tymczasowo zatrzymać każde dodatkowe oprogramowanie, aby zobaczyć, czy zmienia coś.
- Nie zmieniaj nazwy głównego pliku wykonywalnego Unity, ponieważ rozszerzenia VSTU tylko monitorowanie procesów "Unity.exe".

## <a name="visual-studio-crashes"></a>Awarie programu Visual Studio

Przyczyną tego problemu może być uszkodzenie pamięci podręcznej programu Visual Studio MEF.

Spróbuj usunąć następujący folder w celu zresetowania pamięci podręcznej MEF (Zamknij program Visual Studio przed wykonaniem tej czynności):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Powinno to rozwiązać problem. Jeśli problem nadal występuje, Uruchom wiersz polecenia dla deweloperów dla programu Visual Studio jako administrator i użyj następującego polecenia:

```batch
 devenv /setup
```

## <a name="visual-studio-stops-responding"></a>Program Visual Studio przestaje odpowiadać

Kilka wtyczek Unity, takich jak Parse, FMOD —, UMP (Universal Media Player), ZFBrowser lub Embedded Browser, korzysta z natywnych wątków. Jest to problem, gdy wtyczka zakończyła się dołączeniem wątku natywnego do środowiska uruchomieniowego, które następnie blokuje wywołania systemu operacyjnego. Oznacza to, że aparat Unity nie może przerwać tego wątku dla debugera (lub ponownego załadowania domeny) i przestać odpowiadać.

W przypadku FMOD — istnieje obejście, można przekazać `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` [flagę](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags) inicjowania, aby wyłączyć asynchroniczne przetwarzanie i wykonać wszystkie operacje przetwarzania na głównym wątku.

## <a name="incompatible-project-in-visual-studio"></a>Niezgodny projekt w programie Visual Studio

Najpierw sprawdź, czy program Visual Studio jest ustawiony jako zewnętrzny edytor skryptów w aparacie Unity (Edytuj/preferencje/narzędzia zewnętrzne). Następnie sprawdź, czy wtyczka programu Visual Studio jest zainstalowana w aparacie Unity (w oknie Pomoc/informacje musi zostać wyświetlony komunikat o błędzie, np. Microsoft Visual Studio Tools for Unity jest włączona u dołu). Następnie sprawdź, czy rozszerzenie jest poprawnie zainstalowane w programie Visual Studio (pomoc/informacje).

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Dodatkowe ponowne ładowania lub program Visual Studio utraci wszystkie otwarte okna

Pamiętaj, aby nigdy nie dotykać plików projektu bezpośrednio z poziomu procesora zasobów lub innego narzędzia. Jeśli naprawdę potrzebujesz manipulować plikiem projektu, udostępniamy interfejs API dla tego programu. Sprawdź [sekcję problemy z odwołaniami zestawu](#assembly-reference-issues).

W przypadku wystąpienia dodatkowych ponownych prób lub jeśli program Visual Studio utraci wszystkie otwarte okna przy ponownym załadowaniu, upewnij się, że są zainstalowane odpowiednie pakiety docelowe platformy .NET. Aby uzyskać więcej informacji, zapoznaj się z poniższą sekcją dotyczącą platform.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Debuger nie przerywa włączania wyjątków

W przypadku korzystania ze starszego środowiska uruchomieniowego aparatu Unity (odpowiednik w programie .NET 3,5) debuger będzie zawsze przerywał działanie, gdy wyjątek jest nieobsługiwany (= poza blokiem try/catch). Jeśli wyjątek jest obsługiwany, debuger użyje okna Ustawienia wyjątku, aby określić, czy przerwanie jest wymagane, czy nie.

Przy użyciu nowego środowiska uruchomieniowego (.NET 4,6 odpowiednik) środowisko Unity wprowadziło nowy sposób zarządzania wyjątkami użytkownika, a w związku z tym wszystkie wyjątki są uznawane za "obsłużone przez użytkownika", nawet jeśli znajdują się poza blokiem try/catch. Dlatego teraz musisz jawnie sprawdzić je w oknie Ustawienia wyjątku, jeśli chcesz, aby debuger mógł się przerwać.

W oknie Ustawienia wyjątku (Debuguj > ustawienia wyjątku > systemu Windows) rozwiń węzeł kategorii wyjątków (na przykład wyjątki środowiska uruchomieniowego języka wspólnego, oznaczanie wyjątków platformy .NET), a następnie zaznacz pole wyboru dla konkretnego wyjątku, który ma być przechwytywany w tej kategorii (na przykład system. NullReferenceException). Można również wybrać całą kategorię wyjątków.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>W systemie Windows program Visual Studio prosi o pobranie platformy docelowej aparatu Unity

Visual Studio Tools for Unity wymaga programu .NET Framework 3,5, który nie jest instalowany domyślnie w systemie Windows 8 lub 10. Aby rozwiązać ten problem, postępuj zgodnie z instrukcjami w celu pobrania i zainstalowania programu .NET Framework 3,5.

W przypadku korzystania z nowego środowiska uruchomieniowego aparatu Unity wymagane są również pakiety programu .NET w wersji 4,6 i 4.7.1. Można użyć Instalatora program VS2017, aby szybko zainstalować je (zmodyfikować instalację program VS2017, poszczególne składniki, kategorię .NET, wybrać wszystkie 4. x pakiety docelowe).

## <a name="assembly-reference-issues"></a>Problemy z odwołaniem do zestawu

Jeśli projekt jest złożoną referencją lub jeśli chcesz lepiej kontrolować ten krok generacji, możesz użyć naszego [interfejsu API](../cross-platform/customize-project-files-created-by-vstu.md) do manipulowania wygenerowanego projektu lub zawartości rozwiązania. Możesz również używać [plików odpowiedzi](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) w projekcie aparatu Unity i przetwarzać je.

## <a name="breakpoints-with-a-warning"></a>Punkty przerwania z ostrzeżeniem

Jeśli program Visual Studio nie może znaleźć lokalizacji źródłowej dla określonego punktu przerwania, zobaczysz ostrzeżenie wokół punktu przerwania. Sprawdź, czy skrypt, którego używasz, jest prawidłowo załadowany/używany w bieżącej scenie środowiska Unity.

## <a name="breakpoints-not-hit"></a>Punkty przerwania nie trafią

Sprawdź, czy skrypt, którego używasz, jest prawidłowo załadowany/używany w bieżącej scenie środowiska Unity. Zamknij zarówno program Visual Studio, jak i środowisko Unity, a następnie usuń wszystkie pliki wygenerowane ( \* . csproj, \* . sln) i folder biblioteki.

## <a name="unable-to-debug-android-players"></a>Nie można debugować odtwarzaczy systemu Android

Korzystamy z multiemisji na potrzeby wykrywania odtwarzacza (który jest domyślnym mechanizmem używanym przez aparat Unity), ale po tym, gdy korzystamy z zwykłego połączenia TCP w celu dołączenia debugera. Faza wykrywania jest głównym problemem dla urządzeń z systemem Android.

Sieć Wi-Fi jest uniwersalna, ale jest bardzo mała w porównaniu z portem USB z powodu opóźnienia. W przypadku niektórych routerów lub urządzeń wystąpił brak odpowiedniej obsługi multiemisji (seria Nexus jest dobrze znana dla tego).

Magistrala USB jest wyjątkowo szybka do debugowania, a Visual Studio Tools for Unity jest teraz w stanie wykryć urządzenia USB i skontaktować się z serwerem ADB w celu poprawnego przesyłania portów na potrzeby debugowania.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Problemy z programem Visual Studio 2015 i technologią IntelliSense lub zabarwieniem kodu

Spróbuj uaktualnić program Visual Studio 2015 do wersji Update 3.

## <a name="known-issues"></a>Znane problemy

 Istnieją znane problemy w Visual Studio Tools for Unity, które wynikają z tego, jak debuger współdziała z starszą wersją kompilatora języka C#. Pracujemy nad tym, aby pomóc w rozwiązaniu tych problemów, ale w międzyczasie mogą wystąpić następujące problemy:

- Podczas debugowania aparat Unity czasami ulega awarii.

- Podczas debugowania aparat Unity czasami zawiesza się.

- Przechodzenie do i z metod czasami zachowuje się nieprawidłowo, szczególnie w iteratorach lub wewnątrz instrukcji switch.

## <a name="report-errors"></a>Zgłoś błędy

 Pomóż nam ulepszyć jakość Visual Studio Tools for Unity przez wysyłanie raportów o błędach w przypadku wystąpienia awarii, zawieszania lub innych błędów. Pomaga nam zbadać i rozwiązać problemy w Visual Studio Tools for Unity. Dziękujemy!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak zgłosić błąd, gdy program Visual Studio zawiesza się

 Istnieją raporty, które program Visual Studio czasami zawiesza podczas debugowania przy użyciu Visual Studio Tools for Unity, ale potrzebujemy więcej danych, aby zrozumieć ten problem. Możesz pomóc nam zbadać, wykonując poniższe kroki.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Aby zgłosić, że program Visual Studio zawiesza się podczas debugowania za pomocą Visual Studio Tools for Unity

*W systemie Windows:*

1. Otwórz nowe wystąpienie programu Visual Studio.

1. Otwórz okno dialogowe Dołączanie do procesu. W nowym wystąpieniu programu Visual Studio, w menu głównym, wybierz **Debuguj**, **Dołącz do procesu**.

1. Dołącz debuger do zamrożonego wystąpienia programu Visual Studio. W oknie dialogowym **Dołącz do procesu** wybierz zamrożone wystąpienie programu Visual Studio z tabeli **dostępne procesy** , a następnie wybierz przycisk **Dołącz** .

1. Wstrzymaj debuger. W nowym wystąpieniu programu Visual Studio, w menu głównym, wybierz **Debuguj**, **Przerwij wszystko**lub po prostu naciśnij **kombinację klawiszy CTRL + ALT + BREAK**.

1. Utwórz zrzut wątku. W okno Polecenie wprowadź następujące polecenie i naciśnij klawisz **Enter**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Może być konieczne, aby okno **polecenia** było widoczne jako pierwsze. W programie Visual Studio, w menu głównym, wybierz **Widok**, **inne**okna, **okno poleceń**.

*Na komputerze Mac:*

1. Otwórz Terminal i uzyskaj Identyfikator PID Visual Studio dla komputerów Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Uruchom Debuger LLDB:

    ```shell
    lldb
    ```

1. Dołącz do wystąpienia Visual Studio dla komputerów Mac przy użyciu identyfikatora PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Pobierz ślad stosu dla wszystkich wątków:

    ```shell
    bt all
    ```

Na koniec Wyślij zrzut wątku do programu [vstusp@microsoft.com](mailto:vstusp@microsoft.com) wraz z opisem tego, co zostało wykonywane, gdy program Visual Studio został zablokowany.
