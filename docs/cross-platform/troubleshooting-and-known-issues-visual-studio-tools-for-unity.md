---
title: Rozwiązywanie problemów i znane problemy (Visual Studio Tools for Unity) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 57249507373199d217079a9b18c483fee9a51098
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62815589"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Rozwiązywanie problemów i znane problemy (Visual Studio Tools for Unity)

W tej sekcji możesz znaleźć rozwiązania typowych problemów z narzędziami Visual Studio Tools for Unity, opisy znanych problemów i Dowiedz się, jak możesz pomóc ulepszyć program Visual Studio Tools for Unity raportowanie błędów.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Rozwiązywanie problemów z połączenia między Unity i programu Visual Studio

### <a name="confirm-editor-attaching-is-enabled"></a>Upewnij się, że edytor dołączanie jest włączona

Wybierz z Menu Unity **Edytuj > Preferencje** , a następnie wybierz **zewnętrznych narzędzi** kartę. Upewnij się, że **dołączanie edytora** pole wyboru jest włączone. Aby uzyskać więcej informacji, zobacz [dokumentacji aparatu Unity preferencje](https://docs.unity3d.com/Manual/Preferences.html).

### <a name="unable-to-attach"></a>Nie można dołączyć

- Spróbuj tymczasowo wyłączyć programu antywirusowego lub utworzyć reguły wykluczania dla programu VS i platformy Unity.
- Spróbuj tymczasowo wyłączyć zapory lub tworzyć reguły umożliwiające sieci TCP/UDP między VS i Unity.
- Niektóre programy, takie jak Podgląd zespołu może zakłócać proces wykrywania. Możesz spróbować tymczasowo zatrzymać wszelkie dodatkowe oprogramowanie, aby zobaczyć, jeśli zmienia się coś.
- Nie należy zmieniać nazw głównego pliku wykonywalnego Unity, VSTU jest tylko monitorowanie procesów "Unity.exe".

## <a name="visual-studio-crashes"></a>Visual Studio ulega awarii

Ten problem może wynikać z pamięć podręczna MEF usługi Visual Studio jest uszkodzony.

Wypróbuj, usuwając następujący folder, aby zresetować pamięć podręczna MEF (Zamknij program Visual Studio przed wykonaniem tych):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

To powinno rozwiązać problem. W przypadku, gdy nadal występuje ten problem, uruchom wiersz polecenia dla deweloperów programu Visual Studio jako Administrator i użyj następującego polecenia:

```batch
 devenv /setup
```

## <a name="visual-studio-hangs"></a>Visual Studio zawiesza się

Kilka wtyczek platformy Unity, takich jak analizy, FMOD, STUDZIENKĘ (uniwersalny odtwarzacz), ZFBrowser lub przeglądarki Embedded korzystają z wątków natywnych. Jest to problem, gdy wtyczki kończy się dołączanie natywnych wątku do środowiska uruchomieniowego, które następnie wykonuje operację blokowania wywołań do systemu operacyjnego. Oznacza to, Unity nie można przerwać wątek debugera (lub Załaduj ponownie domeny) i zawieszeniu.

FMOD, istnieje obejście tego problemu, możesz przekazać `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` inicjowania [flagi](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) Wyłącz Przetwarzanie asynchroniczne i wykonywać całego procesu przetwarzania w wątku głównym.

## <a name="incompatible-project-in-visual-studio"></a>Niezgodne projektu w programie Visual Studio

Po pierwsze, upewnij się, że ustawiono programu Visual Studio jako edytora skryptu zewnętrznego na platformie Unity (narzędzia edycji/preferencje/zewnętrzną). Następnie sprawdź, czy wtyczka programu Visual Studio jest zainstalowany na platformie Unity (Pomoc/informacje muszą powoduje wyświetlenie komunikatu, takich jak Microsoft Visual Studio Tools for Unity jest włączony u dołu). Następnie sprawdź, czy rozszerzenie jest poprawnie zainstalowane w programie Visual Studio (Pomoc/informacje).

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Dodatkowe przeładowania lub Visual Studio utraty wszystkie otwarte okna

Pamiętaj nigdy nie touch pliki projektu bezpośrednio z procesora zasobów lub innego narzędzia. Gdy rzeczywiście potrzebujesz do manipulowania pliku projektu, możemy ujawnić dla tego interfejsu API. Sprawdź, czy [sekcji problemy odwołuje się zestaw](#assembly-reference-issues).

Jeśli masz dodatkowe ładuje ponownie, lub jeśli kierowcą programu Visual Studio wszystkich otwartych Windows na ponowne załadowanie, upewnij się, że masz właściwe .NET zainstalowane pakiety przeznaczone dla. Sprawdź następujące sekcję dotyczącą platform, aby uzyskać więcej informacji.

## <a name="the-debugger-does-not-break-on-exceptions"></a>Debuger nie przerwy na wyjątki

Przy użyciu starszej wersji środowiska uruchomieniowego aparatu Unity (odpowiednik .NET 3.5), debuger spowoduje przerwanie zawsze, gdy wyjątek jest nieobsługiwany (= spoza bloku try/catch). Jeśli wyjątek jest obsługiwany, debuger użyje okno ustawień wyjątków do określenia, czy podziału jest wymagany.

Za pomocą nowego środowiska uruchomieniowego (.NET 4.6 odpowiednik) Unity wprowadzono nowy sposób Zarządzanie wyjątkami użytkownika, i w rezultacie, wszystkie wyjątki są postrzegane jako "obsługiwane przez użytkownika", nawet jeśli znajdują się poza blokiem try/catch. Dlatego należy jawnie zaewidencjonować je w okno ustawień wyjątków, jeśli chcesz, aby debuger przerywa.

W oknie Ustawienia wyjątków (debugowanie > Windows > Ustawienia wyjątków), a następnie rozwiń węzeł kategorii wyjątków (na przykład typowe wyjątki środowiska uruchomieniowego języka, co oznacza wyjątki platformy .NET) i zaznacz pole wyboru dla określonego wyjątku, aby CATCH w ramach tej kategorii (na przykład wystąpienie wyjątku System.NullReferenceException). Możesz również wybrać całej kategorii wyjątków.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>W Windows Visual Studio Wyświetla prośbę można pobrać platformę docelową aparatu Unity

Visual Studio Tools for Unity wymaga programu .NET framework 3.5, który nie jest instalowany domyślnie w systemie Windows 8, 10. Aby rozwiązać ten problem, postępuj zgodnie z instrukcjami, aby pobrać i zainstalować program .NET framework 3.5.

Korzystając z nowego środowiska uruchomieniowego Unity, określania wartości docelowej pakiety wersji .NET 4.6 i 4.7.1 wymagane są również. Istnieje możliwość szybko zainstalować je w (modyfikacja w Twojej instalacją programu VS 2017, poszczególne składniki, .NET, Kategoria wybierz 4.x wszystkie pakiety przeznaczone dla) przy użyciu Instalatora programu VS 2017.

## <a name="assembly-reference-issues"></a>Problemy z odwołania zestawu

Jeśli projekt jest złożony reference-wise lub jeśli chcesz lepiej kontrolować ten krok generowania, możesz użyć naszych [API](../cross-platform/customize-project-files-created-by-vstu.md) do manipulowania wygenerowanego zawartości projektu lub rozwiązania. Można również użyć [pliki odpowiedzi](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) w użyciu technologii Unity projektu i firma Microsoft będzie przetwarzać je.

## <a name="breakpoints-with-a-warning"></a>Punkty przerwania z ostrzeżeniem

Jeśli program Visual Studio nie może znaleźć lokalizację źródła dla określonego punktu przerwania w całym punkt przerwania zostanie wyświetlone ostrzeżenie. Sprawdzić, czy skrypt, którego używasz poprawnie załadowany lub używanych w bieżącej sceny aparatu Unity.

## <a name="breakpoints-not-hit"></a>Punkty przerwania nie trafień.

Sprawdzić, czy skrypt, którego używasz poprawnie załadowany lub używanych w bieżącej sceny aparatu Unity. Zamknij Visual Studio i Unity, a następnie usuń wszystkich wygenerowanych plików (\*.csproj, \*sln) i cały folder biblioteki.

## <a name="unable-to-debug-android-players"></a>Nie można debugować graczy systemu Android

Używamy multiemisji wykrywania odtwarzacza, (która jest używana przez środowisko Unity domyślnego mechanizmu), ale po tym używamy regularne połączenia protokołu TCP, aby dołączyć debuger. Faza wykrywania jest główny problem w przypadku urządzeń z systemem Android.

Sieci Wi-Fi jest uniwersalny, ale bardzo wolno z powodu opóźnienia w porównaniu do USB. Brak prawidłowego multiemisji obsługi niektóre routery lub urządzenia (seria Nexus są dobrze znane w tym) był widoczny.

USB jest niezwykle szybkie debugowanie i Visual Studio Tools for Unity jest teraz możliwość wykrycia urządzeń USB i komunikować się z serwera adb można poprawnie przekierować portów do debugowania.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Problemy związane z programu Visual Studio 2015 i technologii IntelliSense lub kod barwy

Spróbuj uaktualnić usługi Visual Studio 2015 z aktualizacją 3.

## <a name="known-issues"></a>Znane problemy

 Są to znane problemy w Visual Studio Tools for Unity, wynikiem sposobu interakcji debuger aparatu Unity w starszej wersji kompilatora języka C#. Pracujemy nad pomóc w rozwiązaniu tych problemów, ale mogą wystąpić następujące problemy, w tym czasie:

- Podczas debugowania, ulega awarii czasem platformy Unity.

- Podczas debugowania, czasami zawiesza się Unity.

- Przechodzenie krok po kroku do i z metody czasami zachowuje się nieprawidłowo, szczególnie w Iteratory lub wewnątrz instrukcji switch.

## <a name="report-errors"></a>Raportowanie błędów

 Pomóż nam ulepszyć jakość programu Visual Studio Tools for Unity przez wysyłanie raportów o błędach, gdy wystąpią uległa awarii, zawiesza się lub inne błędy. Ułatwia to nam Badaj i rozwiązuj problemy w programie Visual Studio Tools for Unity. Dziękuję!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak zgłosić błąd, gdy program Visual Studio zawiesza się

 Brak raportów, które program Visual Studio z czasami zawiesza się podczas debugowania za pomocą programu Visual Studio Tools for Unity, ale musimy większej ilości danych, aby zrozumieć ten problem. Możesz pomóc nam przeanalizować problem przez następujące kroki.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Aby zgłosić, że program Visual Studio zawiesza się podczas debugowania przy użyciu programu Visual Studio Tools for Unity

*Na Windows:*

1. Otwórz nowe wystąpienie programu Visual Studio.

1. Otwórz dialogowym Dołącz do procesu. W wystąpieniu programu Visual Studio, w menu głównym wybierz **debugowania**, **dołączyć do procesu**.

1. Dołącz debuger do zamrożone wystąpieniu programu Visual Studio. W **dołączyć do procesu** okno dialogowe, wybierz zamrożone wystąpienie programu Visual Studio z **dostępne procesy** tabeli, a następnie wybierz **Dołącz** przycisku.

1. Zatrzymaj debuger. W wystąpieniu programu Visual Studio, w menu głównym wybierz **debugowania**, **Przerwij wszystko**, lub po prostu naciśnij **Ctrl + Alt + Break**.

1. Utwórz zrzutu wątku. W oknie wiersza polecenia wprowadź następujące polecenie i naciśnij klawisz **Enter**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Konieczne może być **polecenia** okna pierwszy widoczne. W programie Visual Studio, w menu głównym wybierz **widoku**, **Windows inne**, **okna polecenia**.

*Na komputerze Mac:*

1. Otwórz terminal i Pobierz identyfikator PID programu Visual Studio dla komputerów Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Uruchom debuger lldb:

    ```shell
    lldb
    ```

1. Dołącz do programu Visual Studio dla komputerów Mac wystąpienia używający identyfikatora PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Pobierz ślad stosu dla wszystkich wątków:

    ```shell
    bt all
    ```

Na koniec Wyślij zrzutu wątku do [ vstusp@microsoft.com ](mailto:vstusp@microsoft.com), wraz z opisem czynności wykonywanych podczas zamrożone stało się programu Visual Studio.
