---
title: Rozwiązywanie problemów i znane problemy (VS Tools for Unity)
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d6856ff73f9aab2325a31e164e7983a919097d46
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "66261116"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Rozwiązywanie problemów i znane problemy (Visual Studio Tools for Unity)

W tej sekcji znajdziesz rozwiązania typowych problemów z Visual Studio Tools for Unity, opisy znanych problemów i dowiedzieć się, jak można pomóc w ulepszaniu narzędzi programu Visual Studio tools dla unity, zgłaszając błędy.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Rozwiązywanie problemów z połączeniem między unity i visual studio

### <a name="confirm-editor-attaching-is-enabled"></a>Potwierdzanie dołączania do edytora jest włączone

W menu Jedność wybierz polecenie **Edytuj > preferencje,** a następnie wybierz **Editor Attaching** kartę **Narzędzia zewnętrzne.** Aby uzyskać więcej informacji, zobacz [dokumentację Preferencji jedności](https://docs.unity3d.com/Manual/Preferences.html).

### <a name="unable-to-attach"></a>Nie można dołączyć

- Spróbuj tymczasowo wyłączyć program antywirusowy lub utworzyć reguły wykluczeń dla formatu VS i Unity.
- Spróbuj tymczasowo wyłączyć zaporę lub utworzyć reguły zezwalające na sieci TCP/UDP między vs i unity.
- Niektóre programy, takie jak Team Viewer, mogą zakłócać wykrywanie procesów. Możesz spróbować tymczasowo zatrzymać dodatkowe oprogramowanie, aby sprawdzić, czy coś się zmienia.
- Nie należy zmieniać nazwy głównego pliku wykonywalnego Unity, ponieważ vstu jest tylko monitorowanie "Unity.exe" procesów.

## <a name="visual-studio-crashes"></a>Awaria programu Visual Studio

Ten problem może być spowodowane pamięci podręcznej MEF programu Visual Studio jest uszkodzony.

Spróbuj usunąć następujący folder, aby zresetować pamięć podręczną MEF (zamknij program Visual Studio przed wykonaniem tej czynności):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Powinno to rozwiązać problem. Jeśli problem nadal występuje, uruchom wiersz polecenia dewelopera dla programu Visual Studio jako administrator i użyj następującego polecenia:

```batch
 devenv /setup
```

## <a name="visual-studio-hangs"></a>Program Visual Studio zawiesza się

Kilka wtyczek Unity, takich jak Parse, FMOD, UMP (Universal Media Player), ZFBrowser lub Embedded Browser, używa wątków natywnych. Jest to problem, gdy wtyczka kończy się dołączanie wątku macierzystego do środowiska wykonawczego, który następnie blokuje wywołania systemu operacyjnego. Oznacza to, że Unity nie może przerwać tego wątku debugera (lub domeny ponownie załadować) i zawiesić.

Dla FMOD istnieje obejście, można przekazać `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` [flagę](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags) inicjowania, aby wyłączyć przetwarzanie asynchroniczne i wykonać wszystkie przetwarzanie w wątku głównym.

## <a name="incompatible-project-in-visual-studio"></a>Niezgodny projekt w programie Visual Studio

Najpierw sprawdź, czy program Visual Studio jest ustawiony jako edytor skryptów zewnętrznych w Unity (Edit/Preferences/External Tools). Następnie sprawdź, czy wtyczka programu Visual Studio jest zainstalowana w unity (Pomoc/Informacje musi wyświetlać komunikat, taki jak Microsoft Visual Studio Tools for Unity jest włączony na dole). Następnie sprawdź, czy rozszerzenie jest poprawnie zainstalowane w programie Visual Studio (Pomoc/Informacje).

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Dodatkowe przeładowania lub visual studio utraty wszystkich otwartych okien

Pamiętaj, aby nigdy nie dotykać plików projektu bezpośrednio z procesora zasobów lub innego narzędzia. Jeśli naprawdę trzeba manipulować plikiem projektu, możemy udostępnić interfejsu API do tego. Sprawdź [sekcję Problemy z odwołaniami do zestawu](#assembly-reference-issues).

Jeśli wystąpią dodatkowe przeładowania lub jeśli program Visual Studio traci wszystkie otwarte systemu Windows podczas ponownego ładowania, upewnij się, że masz zainstalowane odpowiednie pakiety docelowe .NET. Aby uzyskać więcej informacji, zapoznaj się z poniższą sekcją dotyczącą struktur.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Debuger nie przerywa wyjątków

Podczas korzystania ze starszego środowiska wykonawczego Unity (.NET 3.5 odpowiednik), debuger zawsze przerwy, gdy wyjątek jest nieobsługiwał (=poza try/catch bloku). Jeśli wyjątek jest obsługiwany, debuger użyje okna ustawień wyjątków, aby ustalić, czy przerwa jest wymagana, czy nie.

Z nowym środowisko uruchomieniowe (.NET 4.6 odpowiednik), Unity wprowadzono nowy sposób zarządzania wyjątkami użytkowników i w rezultacie wszystkie wyjątki są postrzegane jako "obsługi użytkownika", nawet jeśli są one poza try/catch bloku. Dlatego teraz trzeba jawnie sprawdzić je w oknie Ustawienia wyjątków, jeśli chcesz debugera do przerwania.

W oknie Ustawienia wyjątków (Debug > ustawienia wyjątków systemu Windows >) rozwiń węzeł dla kategorii wyjątków (na przykład wyjątki czasu wykonywania języka wspólnego, co oznacza wyjątki .NET) i zaznacz pole wyboru dla określonego wyjątku, który chcesz złapać w tej kategorii (na przykład System.NullReferenceException). Można również wybrać całą kategorię wyjątków.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>W systemie Windows program Visual Studio prosi o pobranie struktury docelowej Unity

Narzędzia programu Visual Studio dla unity wymaga .NET framework 3.5, który nie jest zainstalowany domyślnie w systemie Windows 8 lub 10. Aby rozwiązać ten problem, postępuj zgodnie z instrukcjami, aby pobrać i zainstalować program .NET framework 3.5.

Podczas korzystania z nowego środowiska wykonawczego Unity. Istnieje możliwość użycia instalatora VS2017, aby szybko je zainstalować (zmodyfikuj instalację VS2017, poszczególne składniki, kategorię .NET, wybierz wszystkie pakiety docelowe 4.x).

## <a name="assembly-reference-issues"></a>Problemy z odwołaniem do zestawu

Jeśli projekt jest złożony odniesienia mądry lub jeśli chcesz lepiej kontrolować ten krok generowania, można użyć naszego [interfejsu API](../cross-platform/customize-project-files-created-by-vstu.md) do manipulowania wygenerowany projekt lub zawartość rozwiązania. Można również użyć [plików odpowiedzi](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) w projekcie Unity, a my je przetworzymy.

## <a name="breakpoints-with-a-warning"></a>Punkty przerwania z ostrzeżeniem

Jeśli visual studio nie może znaleźć lokalizacji źródłowej dla określonego punktu przerwania zostanie wyświetlone ostrzeżenie wokół punktu przerwania. Sprawdź, czy używany skrypt jest poprawnie załadowany/używany w bieżącej scenie Unity.

## <a name="breakpoints-not-hit"></a>Punkty przerwania nie trafione

Sprawdź, czy używany skrypt jest poprawnie załadowany/używany w bieżącej scenie Unity. Zamknij program Visual Studio i Unity,\*a następnie \*usuń wszystkie wygenerowane pliki ( .csproj, .sln) i cały folder Biblioteka.

## <a name="unable-to-debug-android-players"></a>Nie można debugować graczy z Androida

Używamy multiemisji do wykrywania odtwarzacza (który jest domyślnym mechanizmem używanym przez Unity), ale po tym używamy zwykłego połączenia TCP do dołączenia debugera. Faza wykrywania jest głównym problemem dla urządzeń z systemem Android.

Wifi jest wszechstronny, ale bardzo powolny w porównaniu do USB z powodu opóźnienia. Widzieliśmy brak odpowiedniej obsługi multiemisji dla niektórych routerów lub urządzeń (seria Nexus jest dobrze znana z tego).

USB jest bardzo szybki do debugowania, a Visual Studio Tools for Unity jest teraz w stanie wykryć urządzenia USB i porozmawiać z serwerem adb, aby prawidłowo przesłać porty do debugowania.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Problemy z programami Visual Studio 2015 i IntelliSense lub kolorowaniem kodu

Spróbuj uaktualnić program Visual Studio 2015 do aktualizacji 3.

## <a name="known-issues"></a>Znane problemy

 Istnieją znane problemy w narzędziach programu Visual Studio dla unity, które wynikają z jak debuger współdziała ze starszą wersją unity kompilatora Języka C#. Pracujemy nad rozwiązaniem tych problemów, ale w międzyczasie mogą wystąpić następujące problemy:

- Podczas debugowania Unity czasami ulega awarii.

- Podczas debugowania Unity czasami zawiesza się.

- Przechodzenie do i obecnie metody czasami zachowuje się niepoprawnie, zwłaszcza w iteratorów lub w instrukcji switch.

## <a name="report-errors"></a>Zgłaszanie błędów

 Pomóż nam poprawić jakość programu Visual Studio Tools for Unity, wysyłając raporty o błędach, gdy wystąpi awaria, zawiesza się lub inne błędy. Pomaga nam to badać i rozwiązywać problemy w programie Visual Studio Tools for Unity. Dziękujemy!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak zgłosić błąd, gdy program Visual Studio zawiesza się

 Istnieją raporty, że visual studio czasami zawiesza się podczas debugowania za pomocą programu Visual Studio Tools dla unity, ale potrzebujemy więcej danych, aby zrozumieć ten problem. Możesz pomóc nam zbadać, wykonując poniższe czynności.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Aby zgłosić, że program Visual Studio zawiesza się podczas debugowania za pomocą programu Visual Studio Tools for Unity

*W systemie Windows:*

1. Otwórz nowe wystąpienie programu Visual Studio.

1. Otwórz okno dialogowe Dołącz do procesu. W nowym wystąpieniu programu Visual Studio w menu głównym wybierz polecenie **Debugowanie**, **Dołącz do procesu**.

1. Dołącz debuger do zamrożonego wystąpienia programu Visual Studio. W oknie dialogowym **Dołącz do procesu** wybierz zamrożone wystąpienie programu Visual Studio z tabeli Dostępne **procesy,** a następnie wybierz przycisk **Dołącz.**

1. Wstrzymaj debuger. W nowym wystąpieniu programu Visual Studio w menu głównym wybierz polecenie **Debug**, **Przerwij wszystko**lub po prostu naciśnij **klawisze Ctrl+Alt+Break**.

1. Utwórz zrzut wątku. W oknie Polecenia wprowadź następujące polecenie i naciśnij klawisz **Enter**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Może być konieczne, aby okno **polecenia** było najpierw widoczne. W programie Visual Studio w menu głównym wybierz polecenie **Widok**, **Inne okna ,** Okno **poleceń**.

*Na komputerze Mac:*

1. Otwórz terminal i pobierz identyfikator PID programu Visual Studio dla komputerów Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Uruchom debuger lldb:

    ```shell
    lldb
    ```

1. Dołącz do programu Visual Studio dla komputerów Mac wystąpienie przy użyciu PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Pobierz stacktrace dla wszystkich wątków:

    ```shell
    bt all
    ```

Na koniec wyślij wątek [vstusp@microsoft.com](mailto:vstusp@microsoft.com)zrzutu do , wraz z opisem, co robisz, gdy visual studio został zamrożony.
