---
title: Rozwiązywanie problemów i znane problemy (VS Tools for Unity)
description: Przeczytaj o rozwiązywaniu problemów w Visual Studio Tools for Unity. Zapoznaj się z opisami znanych problemów i dowiedz się więcej o rozwiązaniach tych problemów.
ms.custom: ''
ms.date: 04/15/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 37ee35fa66d37f9b85af01f5012e8ede76e877de
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879372"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Rozwiązywanie problemów i znane problemy (Visual Studio Tools for Unity)

W tej sekcji znajdziesz rozwiązania typowych problemów z usługą Visual Studio Tools for Unity, opisy znanych problemów i dowiesz się, jak można ulepszyć rozwiązania Visual Studio Tools for Unity zgłaszając błędy.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Rozwiązywanie problemów z połączeniem między unity i Visual Studio

### <a name="confirm-editor-attaching-is-enabled-or-code-optimization-on-startup-is-set-to-debug"></a>`Editor Attaching`Potwierdź, że `Code Optimization On Startup` jest włączona lub ustawiona na`Debug`

W menu aparatu Unity wybierz pozycję `Edit / Preferences` .

W zależności od używanej wersji aparatu Unity:
- Upewnij się, `Code Optimization On Startup` że ustawiono wartość `Debug` .
- Lub wybierz `External Tools` kartę. Potwierdź, że `Editor Attaching` pole wyboru jest włączone. 

Aby uzyskać więcej informacji, zobacz [dokumentację preferencji aparatu Unity](https://docs.unity3d.com/Manual/Preferences.html).

### <a name="unable-to-attach"></a>Nie można dołączyć

- Spróbuj tymczasowo wyłączyć program antywirusowy lub utworzyć reguły wykluczania dla programu VS i aparatu Unity.
- Spróbuj tymczasowo wyłączyć zaporę lub utworzyć reguły zezwalania na połączenia sieciowe TCP/UDP między programem VS i unity.
- Niektóre programy, takie jak Team Viewer, mogą zakłócać wykrywanie procesów. Możesz spróbować tymczasowo zatrzymać dodatkowe oprogramowanie, aby sprawdzić, czy coś się zmienia.
- Nie zmieniaj nazwy głównego pliku wykonywalnego aparatu Unity, ponieważ vstu monitoruje tylko procesy "Unity.exe".

## <a name="visual-studio-crashes"></a>Visual Studio awarie

Ten problem może być spowodowany uszkodzeniem Visual Studio MEF.

Spróbuj usunąć następujący folder, aby zresetować pamięć podręczną MEF (zamknij Visual Studio przed wykonaniem tej czynności):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Powinno to rozwiązać problem. Jeśli problem nadal występuje, uruchom wiersz polecenia dla deweloperów dla Visual Studio jako administrator i użyj następującego polecenia:

```batch
 devenv /setup
```

## <a name="visual-studio-stops-responding"></a>Visual Studio przestaje odpowiadać

Kilka wtyczek aparatu Unity, takich jak Parse, FMOD, UMP (Universal Media Player), ZFBrowser lub Embedded Browser, używa wątków natywnych. Jest to problem, gdy wtyczka kończy się dołączanie wątku natywnego do środowiska uruchomieniowego, które następnie blokuje wywołania do systemu operacyjnego. Oznacza to, że aparat Unity nie może przerwać tego wątku dla debugera (lub ponownego załadowania domeny) i przestać odpowiadać.

W przypadku funkcji FMOD istnieje obejście. Można przekazać flagę inicjowania, aby wyłączyć przetwarzanie asynchroniczne i wykonać wszystkie operacje przetwarzania `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` w wątku głównym. [](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags)

## <a name="incompatible-project-in-visual-studio"></a>Niezgodny projekt w programie Visual Studio

Bardzo ważne jest, aby wiedzieć, że Visual Studio jest zapisywanie stanu "Niezgodne" w ustawieniach projektu i nie będzie próbować ponownie załadować projektu, dopóki jawnie nie użyjesz . `Reload Project` Dlatego po każdym kroku rozwiązywania problemów upewnij się, że próbujesz ponownie otworzyć rozwiązanie, a następnie kliknij prawym przyciskiem myszy wszystkie niezgodne projekty i wybierz polecenie `Reload Project` .

1. Sprawdź, Visual Studio jest ustawiony jako zewnętrzny edytor skryptów w a aparatu Unity przy użyciu polecenia `Edit / Preferences / External Tools` .
2. W zależności od wersji aparatu Unity:
   - Sprawdź, czy wtyczka Visual Studio jest zainstalowana w a aparatu Unity. `Help / About` powinien wyświetlić komunikat, taki jak Microsoft Visual Studio narzędzia dla aparatu Unity są włączone w dolnej części.
   - Unity 2020.x+: sprawdź, czy używasz najnowszego pakietu edytora Visual Studio w programie `Window / Package Manager` .
3. Spróbuj usunąć wszystkie pliki projektów/rozwiązań `.vs` i folder w projekcie.
4. Spróbuj ponownie skonkretyzować projekty/rozwiązanie przy użyciu `Open C# Project` narzędzia lub `Edit / Preferences / External tools / Regenerate Project files` .
5. Upewnij się, że obciążenie Game/Unity jest zainstalowane w Visual Studio.
6. Spróbuj wyczyścić pamięć podręczną MEF, jak wyjaśniono [tutaj.](#visual-studio-crashes)
7. Spróbuj ponownie zainstalować aplikację Visual Studio (przy użyciu obciążenia Game/Unity tylko na początku).
8. Spróbuj wyłączyć rozszerzenia innych firm w przypadku, gdy mogą one zakłócać rozszerzenie aparatu Unity w pliku `Tools / Extensions` .

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Dodatkowe ponowne załadowanie lub Visual Studio utraty wszystkich otwartych okien

Pamiętaj, aby nigdy nie dotykać plików projektu bezpośrednio z procesora zasobów lub innego narzędzia. Jeśli naprawdę musisz manipulować plikiem projektu, udostępnimy w tym celu interfejs API. Sprawdź sekcję [Problemy z odwołaniami do zestawu](#assembly-reference-or-project-property-issues).

Jeśli wystąpią dodatkowe ponowne załadowania lub jeśli Visual Studio wszystkie otwarte okna po ponownym załadowaniu, upewnij się, że masz zainstalowane odpowiednie pakiety przeznaczone dla programu .NET. Aby uzyskać więcej informacji, zapoznaj się z następującą sekcją o platformach.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Debuger nie przerwie pracy przy wyjątkach

W przypadku korzystania ze starszego środowiska uruchomieniowego aparatu Unity (odpowiednik programu .NET 3.5) debuger zawsze przerwie korzystanie, gdy wyjątek jest nieobsługiwany (=poza blokiem try/catch). Jeśli wyjątek jest obsługiwany, debuger użyje okna ustawień wyjątku, aby określić, czy przerwa jest wymagana, czy nie.

W nowym środowisku uruchomieniowym (odpowiednik dla programu .NET 4.6) środowisko Unity wprowadziło nowy sposób zarządzania wyjątkami użytkowników i w związku z tym wszystkie wyjątki są traktowane jako "obsługiwane przez użytkownika", nawet jeśli znajdują się poza blokiem try/catch. Dlatego należy je teraz jawnie sprawdzić w oknie ustawienia wyjątku, jeśli debuger ma przerwać ten błąd.

W oknie Ustawienia wyjątków > (Ustawienia wyjątku debugowania w systemie Windows >) rozwiń węzeł dla kategorii wyjątków (na przykład Wyjątki środowiska uruchomieniowego języka wspólnego, czyli wyjątki .NET), a następnie zaznacz pole wyboru dla konkretnego wyjątku, który chcesz przechwycić w ramach tej kategorii (na przykład System.NullReferenceException). Możesz również wybrać całą kategorię wyjątków.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>W systemie Windows Visual Studio pobranie docelowej struktury Aparatu Unity

W przypadku korzystania ze starszego środowiska uruchomieniowego aparatu Unity (odpowiednik programu .NET 3.5) program Visual Studio Tools for Unity wymaga programu .NET Framework 3.5, który nie jest instalowany domyślnie na platformie Windows 8 lub 10. Aby rozwiązać ten problem, postępuj zgodnie z instrukcjami, aby pobrać i zainstalować program .NET Framework 3.5.

W przypadku korzystania z nowego środowiska uruchomieniowego unity wymagane są również pakiety docelowe .NET w wersji 4.6 lub 4.7.1 w zależności od wersji aparatu Unity. Za pomocą instalatora programu Visual Studio można szybko je zainstalować (zmodyfikować instalację, poszczególne składniki, kategorię .NET, wybrać wszystkie pakiety docelowe 4.x).

## <a name="assembly-reference-or-project-property-issues"></a>Odwołanie do zestawu lub problemy z właściwościami projektu

Jeśli projekt jest złożony i obejmuje odwołania lub jeśli chcesz lepiej kontrolować ten krok generowania, możesz użyć naszego interfejsu [API](../extensibility/customize-project-files-created-by-vstu.md) do manipulowania wygenerowaną zawartością projektu lub rozwiązania. Możesz również użyć plików [odpowiedzi w](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) projekcie aparatu Unity i będziemy je przetwarzać.

W przypadku Visual Studio i unity najlepszym rozwiązaniem wydaje się użycie pliku niestandardowego `Directory.Build.props` wraz z wygenerowanych projektów. Następnie będzie można współtworzyć strukturę projektu bez zakłócania procesu generowania. Więcej informacji można znaleźć [tutaj](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build#directorybuildprops-and-directorybuildtargets).

## <a name="breakpoints-with-a-warning"></a>Punkty przerwania z ostrzeżeniem

Jeśli Visual Studio nie może znaleźć lokalizacji źródłowej dla określonego punktu przerwania, zostanie wyświetlony komunikat ostrzegawczy wokół punktu przerwania. Sprawdź, czy używany skrypt jest prawidłowo załadowany/używany w bieżącej scenie aparatu Unity.

## <a name="breakpoints-not-hit"></a>Punkty przerwania nie są trafione

Sprawdź, czy używany skrypt jest prawidłowo załadowany/używany w bieżącej scenie aparatu Unity. Zamknij obie Visual Studio i Unity, a następnie usuń wszystkie wygenerowane pliki \* (csproj, \* sln), folder i cały folder `.vs` Biblioteka. Więcej informacji na temat debugowania języka C# można znaleźć w witrynie [internetowej](https://docs.unity3d.com/Manual/ManagedCodeDebugging.html)aparatu Unity.

## <a name="unable-to-debug-android-players"></a>Nie można debugować odtwarzaczy systemu Android

Do wykrywania odtwarzacza używamy multiemisji (czyli domyślnego mechanizmu używanego przez aparat Unity), ale następnie dołączamy debuger za pomocą zwykłego połączenia TCP. Faza wykrywania jest głównym problemem dla urządzeń z systemem Android.

Sieć Wi-Fi jest uniwersalna, ale bardzo wolna w porównaniu z portem USB ze względu na opóźnienie. Widzieliśmy brak odpowiedniej obsługi multiemisji dla niektórych routerów lub urządzeń (seria Nexus jest z tego dobrze znana).

Port USB jest bardzo szybki w przypadku debugowania, Visual Studio Tools for Unity jest teraz w stanie wykrywać urządzenia USB i rozmawiać z serwerem adb, aby prawidłowo przesyłać dalej porty na potrzeby debugowania.

## <a name="issues-with-intellisense-or-code-coloration"></a>Problemy z funkcjami IntelliSense lub kolorowania kodu

Spróbuj uaktualnić Visual Studio do najnowszej wersji. Spróbuj wykonać te same kroki rozwiązywania problemów co w [przypadku niezgodnych projektów](#incompatible-project-in-visual-studio).

## <a name="known-issues"></a>Znane problemy

Istnieją znane problemy w Visual Studio Tools for Unity wynikające ze sposobu interakcji debugera ze starszą wersją kompilatora języka C# aparatu Unity. Pracujemy nad tym, aby rozwiązać te problemy, ale w międzyczasie mogą wystąpić następujące problemy:

- Podczas debugowania unity czasami ulega awarii.

- Podczas debugowania unity czasami zawiesza się.

- Przechodzenie do i z metod czasami działa nieprawidłowo, szczególnie w iteratorach lub w instrukcjach switch.

## <a name="report-errors"></a>Zgłaszanie błędów

Pomóż nam poprawić jakość raportów Visual Studio Tools for Unity wysyłając raporty o błędach w przypadku wystąpienia awarii, zablokowania lub innych błędów. Ułatwia to badanie i rozwiązywanie problemów w Visual Studio Tools for Unity. Dziękujemy!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak zgłosić błąd, gdy Visual Studio się

Istnieją raporty, Visual Studio czasami zawieszają się podczas debugowania za pomocą Visual Studio Tools for Unity, ale potrzebujemy więcej danych, aby zrozumieć ten problem. Możesz pomóc nam w zbadaniu, korzystając z poniższych kroków.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Aby zgłosić, że Visual Studio zawiesza się podczas debugowania przy użyciu Visual Studio Tools for Unity

*W systemie Windows:*

1. Otwórz nowe wystąpienie Visual Studio.

1. Otwórz okno dialogowe Dołączanie do procesu. W nowym wystąpieniu usługi Visual Studio w menu głównym wybierz pozycję **Debuguj,** **Dołącz do procesu.**

1. Dołącz debuger do zamrożonego wystąpienia Visual Studio. W **oknie dialogowym Dołączanie** do procesu wybierz zablokowane wystąpienie Visual Studio z tabeli **Dostępne procesy,** a następnie wybierz **przycisk** Dołącz.

1. Wstrzymaj debuger. W nowym wystąpieniu programu Visual Studio menu głównym wybierz pozycję Debuguj, Przerwij wszystko lub po prostu naciśnij klawisze **Ctrl+Alt+Break.**

1. Tworzenie zrzutu wątków. W okno Polecenie wprowadź następujące polecenie i naciśnij klawisz **Enter**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    W pierwszej kolejności może być **konieczne, aby okno** polecenia było widoczne. W Visual Studio menu głównym wybierz pozycję **Wyświetl,** **Inne okna,** **Okno poleceń.**

*Na komputerze Mac:*

1. Otwórz terminal i uzyskaj identyfikator PID Visual Studio dla komputerów Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Uruchom debuger lldb:

    ```shell
    lldb
    ```

1. Dołącz do wystąpienia Visual Studio dla komputerów Mac przy użyciu PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Pobierz stos dla wszystkich wątków:

    ```shell
    bt all
    ```

Na koniec wyślij zrzut wątku do lokalizacji wraz z opisem tego, co robisz, gdy Visual Studio [vstusp@microsoft.com](mailto:vstusp@microsoft.com) zamrożony.

## <a name="see-also"></a>Zobacz też

- [Visual Studio rozwiązywania problemów](/troubleshoot/visualstudio/welcome-visual-studio/)
