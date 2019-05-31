---
title: Debugowanie just in time
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2814dffa75809a318dc7cebe7831b5ecec7d29
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690608"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Debugowanie just in time w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie Just In Time uruchamia Visual Studio automatycznie, gdy wystąpi wyjątek lub awaria wystąpi w aplikacji, która działa poza programem Visual Studio. Dzięki temu można przetestować aplikację, gdy nie jest uruchomiony program Visual Studio i rozpocząć debugowanie w programie Visual Studio, jeśli wystąpi problem.

Debugowanie Just In Time działa w przypadku aplikacji komputerowych Windows. Nie działa dla aplikacji Windows Universal, a nie działa dla kodu zarządzanego, który znajduje się w aplikacji macierzystej, jak na przykład Wizualizatory.

## <a name="BKMK_Scenario"></a> Czy Just-in-Time zostać wyświetlone okno dialogowe debuger, podczas próby uruchomienia aplikacji?

Działania należy podjąć, gdy pojawi się programu Visual Studio Just-in-Time okno dialogowe debuger zależą od tego, co chcesz zrobić:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Aby pozbyć się okno dialogowe i po prostu uruchomić aplikację normalnie

1. (Użytkownicy zaawansowani) Jeśli masz zainstalowany program Visual Studio (lub miała ona wcześniej zainstalowana i usunął ją), [Wyłącz Just-in-Time debugging](#BKMK_Enabling) , a następnie spróbuj ponownie uruchomić aplikację.

2. Jeśli korzystasz z aplikacji sieci web w programie Internet Explorer, Wyłącz debugowanie skryptu.

    Wyłącz debugowanie skryptu w oknie dialogowym Opcje internetowe. Możesz uzyskać dostęp z **Panelu sterowania** / **sieć i Internet** / **Opcje internetowe** (konkretne kroki zależą od używanej wersji programu Windows i Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Ponownie otworzyć stronę sieci web, gdzie znaleźć błąd. Jeśli to nie rozwiąże problemu, skontaktuj się z właścicielem aplikacji sieci web, aby rozwiązać ten problem.

4. Jeśli używasz innego typu aplikacji Windows, należy skontaktować się z właścicielem aplikacji, aby naprawić ten błąd, a następnie ponownie zainstaluj poprawionej wersji aplikacji.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Jeśli chcesz naprawić lub debugowania błędu (zaawansowanych użytkowników)

- Konieczne jest posiadanie [zainstalowanego programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) Aby wyświetlić szczegółowe informacje o błędzie i spróbuj go debugować. Zobacz [przy użyciu JIT](#BKMK_Using_JIT) szczegółowe informacje. Jeśli nie można naprawić błąd i napraw aplikację, skontaktuj się z właścicielem aplikacji, aby rozwiązać problem.

## <a name="BKMK_Enabling"></a> Włącz lub wyłącz Just-In-Time debugowania
 Można włączyć lub wyłączyć debugowanie w programie Visual Studio Just In Time **narzędzia / Opcje** okno dialogowe.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Aby włączyć lub wyłączyć Just-In-Time debugowanie

1. Otwórz program Visual Studio. Na **narzędzia** menu, kliknij przycisk **opcje**.

2. W **opcje** okno dialogowe, wybierz opcję **debugowanie** folderu.

3. W **debugowanie** folderu, wybierz **Just-In-Time** strony.

4. W **włączyć debugowanie just in Time tych rodzajów kodu** zaznacz lub wyczyść typy odpowiednich programów: **Zarządzane**, **natywnych**, lub **skryptu**.

    Aby wyłączyć debugowanie po jego włączeniu Just-In-Time, musi działać z uprawnieniami administratora. Włączanie Just-In-Time debugging Ustawia klucz rejestru, a wymagane są uprawnienia administratora, aby zmienić ten klucz.

5. Kliknij przycisk **OK**.

   Debugowanie Just In Time może być wciąż włączone, nawet jeśli program Visual Studio nie jest już zainstalowane na tym komputerze. Jeśli nie zainstalowano programu Visual Studio, nie można wyłączyć debugowanie w programie Visual Studio Just In Time **opcje** okno dialogowe. W takiej sytuacji można wyłączyć debugowanie, edytując Rejestr Windows Just In Time.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Aby wyłączyć debugowanie, edytując rejestr Just In Time

1. Na **Start** menu, wyszukaj i uruchom `regedit.exe`

2. W **Edytora rejestru** okna, zlokalizuj i Usuń wpisy rejestru wykonaj:

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\Software\Microsoft\\. NETFramework\DbgManagedDebugger

3. Jeśli komputer działa w 64-bitowym systemie operacyjnym, należy również usunąć następujące wpisy rejestru:

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger

4. Należy zadbać, aby nie przypadkowo usunąć lub zmienić żadnych kluczy rejestru.

5. Zamknij **Edytora rejestru** okna.

> [!NOTE]
> Jeśli próbujesz wyłączyć debugowanie po stronie serwera aplikacji Just-In-Time, a te kroki nie rozwiążą problemu, należy wyłączyć debugowanie po stronie serwera, w ustawieniach aplikacji usług IIS i spróbuj ponownie.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Aby włączyć Just-In-Time, debugowanie formularza Windows

1. Domyślnie aplikacje Windows Forms mają program obsługi wyjątków najwyższego poziomu, który umożliwia programowi kontynuowania działania, jeśli możliwe jest odzyskiwanie. Na przykład jeśli aplikacja Windows Forms zwraca nieobsługiwany wyjątek, zobaczysz okno dialogowe podobne do następującego:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Aby włączyć Just-In-Time debugowanie aplikacji Windows Forms, należy wykonać następujące dodatkowe czynności:

2. Ustaw `jitDebugging` wartość `true` w `system.windows.form` części pliku machine.config lub  *\<Nazwa aplikacji >* . exe.config pliku:

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. W aplikacji formularzy Windows w języku C++, należy także ustawić `DebuggableAttribute` w pliku .config lub w kodzie. Jeśli kompilujesz z opcją [/zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) i bez [/Og](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), kompilator ustawia ten atrybut. Jeśli chcesz debugować kompilację niezoptymalizowanego wydania, jednak należy ustawić to samodzielnie. Można to zrobić, dodając poniższą linię do one pliku AssemblyInfo.cpp aplikacji:

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Użyj debugowania Just In Time
 W tej sekcji przedstawiono, co się stanie, gdy plik wykonywalny zgłasza wyjątek.

 Konieczne jest posiadanie programu Visual Studio wykonaj następujące kroki. Jeśli nie masz programu Visual Studio, możesz pobrać bezpłatną [Visual Studio 2015 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/).

 Po zainstalowaniu programu Visual Studio, Just-In-Time debugging jest domyślnie włączona.

 Na potrzeby tej sekcji wprowadzimy aplikację konsoli C# w programie Visual Studio, które zgłasza <xref:System.NullReferenceException>.

 W programie Visual Studio, tworzenie aplikacji konsolowej C# (**plik / nowy / Project / Visual C# / Aplikacja konsoli**) o nazwie **ThrowsNullException**. Aby uzyskać więcej informacji dotyczących tworzeniu projektów w programie Visual Studio, zobacz [instruktażu: Tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Po otwarciu projektu w programie Visual Studio, otwórz plik Program.cs. Zastąp następujący kod, który wyświetla wiersz do konsoli i następnie zgłasza obiektu NullReferenceException metody Main():

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> W kolejności do wykonania tej procedury do pracy w [konfiguracji wydania](../debugger/how-to-set-debug-and-release-configurations.md), należy wyłączyć [tylko mój kod](../debugger/just-my-code.md). W programie Visual Studio, kliknij przycisk **narzędzia / Opcje**. W **opcje** okno dialogowe, wybierz opcję **debugowanie**. Usuń zaznaczenie z **Włącz tylko mój kod**.

 Skompiluj rozwiązanie (w programie Visual Studio, wybierz **kompilacji / Rebuild rozwiązania**). Można wybrać debugowanie lub konfigurację zwolnienia. Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md).

 Proces kompilacji tworzy ThrowsNullException.exe pliku wykonywalnego. Można je znaleźć w folderze, w której utworzono projekt C#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** lub **...\ThrowsNullException\ThrowsNullException\bin\Release**.

 Kliknij dwukrotnie ThrowsNullException.exe. Powinny zostać wyświetlone okno polecenia następująco:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Po kilku sekundach zostanie wyświetlone okno błąd:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Nie klikaj **anulować**! Po kilku sekundach, powinien zostać wyświetlony dwa przyciski o **debugowania** i **Zamknij program**. Kliknij przycisk **debugowania**.

> [!CAUTION]
> Jeśli aplikacja zawiera niezaufanego kodu, pojawi się okno dialogowe z ostrzeżeniem o zabezpieczeniach. To okno dialogowe umożliwia podjęcie decyzji, czy chcesz kontynuować debugowanie. Przed kontynuowaniem debugowania, należy zdecydować, czy kodowi można zaufać. Czy napisałeś kod samodzielnie? Czy można ufać koderowi? Jeśli aplikacja jest uruchomiona na komputerze zdalnym, czy rozpoznajesz nazwę procesu? Nawet wtedy, gdy aplikacja jest uruchomiona lokalnie, który nie musi oznaczać, że można jej zaufać. Należy wziąć pod uwagę możliwość złośliwy kod uruchomiony na Twoim komputerze. Jeśli zdecydujesz, że kod masz zamiar debugowania jest godny zaufania, kliknij przycisk **debugowania**. W przeciwnym razie kliknij przycisk **nie Debuguj**.

 **Debuger just in Time programu Visual Studio** zostanie wyświetlone okno:

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 W obszarze **debugery możliwe**, który powinien zostać wyświetlony **nowego wystąpienia programu Microsoft Visual Studio 2015** wybrany wiersz. Jeśli go nie jest wybrana, wybierz ją.

 W dolnej części okna w obszarze **chcesz debugować za pomocą wybranego debugera?** , kliknij przycisk **tak**.

 Projekt ThrowsNullException zostanie otwarty w nowym wystąpieniu programu Visual Studio z wykonywaniem zatrzymana w wierszu, który zgłasza wyjątek:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 Można rozpocząć debugowania na tym etapie. Gdyby to rzeczywistej aplikacji, należy dowiedzieć się, dlaczego kod zgłasza wyjątek.

## <a name="just-in-time-debugging-errors"></a>Błędy debugowania Just In Time
 Jeśli nie widzisz okna dialogowego, gdy program ulegnie awarii, może być to ze względu na ustawienia raportowania błędów Windows na komputerze. Aby uzyskać więcej informacji, zobacz [. Ustawienia raportowania błędów systemu Windows](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Można napotkać następujące komunikaty o błędach, które są skojarzone z Just-In-Time debugowania.

- **Nie można dołączyć do procesu powodującego awarię. Określony program nie jest programem Windows ani MS-DOS.**

     Ten błąd występuje, gdy użytkownik próbuje dołączyć do procesu uruchomionego jako inny użytkownik.

     Aby obejść ten problem, uruchom program Visual Studio, otwórz **dołączyć do procesu** okno dialogowe z **debugowania** menu, a następnie znajdź proces, który chcesz debugować w **dostępne procesy**listy. Jeśli nie znasz nazwy procesu, Przyjrzyj się **debuger just in Time programu Visual Studio** okna dialogowego i zwróć uwagę, identyfikator procesu. Wybierz proces na **dostępne procesy** listy, a następnie kliknij przycisk **Dołącz**. W **debuger just in Time programu Visual Studio** okno dialogowe, kliknij przycisk **nie** aby zamknąć okno dialogowe.

- **Nie można uruchomić debugera, ponieważ żaden użytkownik nie jest zalogowany.**

     Ten błąd występuje, gdy Just-In-Time debugowania próbuje uruchomić program Visual Studio na maszynie w przypadku, gdy nie ma żadnego użytkownika zalogowany do konsoli. Ponieważ żaden użytkownik nie jest zalogowany, nie istnieje żadna sesja użytkownika, aby wyświetlić Just-In-Time debugging okno dialogowe.

     Aby rozwiązać ten problem, należy zalogować się na komputerze.

- **Klasa nie jest zarejestrowana.**

     Ten błąd wskazuje, że debuger próbował utworzyć klasę modelu COM, który nie jest zarejestrowana, prawdopodobnie z powodu problemu z instalacją.

     Aby rozwiązać ten problem, należy użyć dysku instalacyjnego ponownie zainstalować lub naprawić instalację programu Visual Studio.

## <a name="see-also"></a>Zobacz też
 [Zabezpieczenia debugera](../debugger/debugger-security.md) [podstawowe informacje o debugerze](../debugger/debugger-basics.md) [Just-In-Time, debugowanie, okno dialogowe Opcje](../debugger/just-in-time-debugging-options-dialog-box.md) [ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub nie masz do nich pełnego zaufania, nie dołączaj do tego procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)
