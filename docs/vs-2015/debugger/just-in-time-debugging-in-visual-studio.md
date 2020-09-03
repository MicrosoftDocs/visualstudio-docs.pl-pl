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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690608"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Debugowanie just in time w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie just in Time uruchamia program Visual Studio automatycznie, gdy wystąpi wyjątek lub awaria w aplikacji, która jest uruchomiona poza programem Visual Studio. Dzięki temu można testować aplikację, gdy program Visual Studio nie jest uruchomiony, i rozpocząć debugowanie w programie Visual Studio w przypadku wystąpienia problemu.

Debugowanie just in Time działa w przypadku aplikacji klasycznych systemu Windows. Nie działa w przypadku uniwersalnych aplikacji systemu Windows i nie działa dla kodu zarządzanego hostowanego w aplikacji natywnej, takiej jak Wizualizatory.

## <a name="did-the-just-in-time-debugger-dialog-box-appear-when-trying-to-run-an-app"></a><a name="BKMK_Scenario"></a> Czy podczas próby uruchomienia aplikacji pojawił się okno dialogowe debugera just in Time?

Akcje, które należy wykonać, gdy zobaczysz okno dialogowe debuger just in Time programu Visual Studio, zależy od tego, co próbujesz zrobić:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Jeśli chcesz pozbyć się okna dialogowego i po prostu uruchomić aplikację normalnie

1. (Użytkownicy zaawansowani) Jeśli masz zainstalowany program Visual Studio (lub został on wcześniej zainstalowany i usunięty), [Wyłącz debugowanie just in Time](#BKMK_Enabling) i spróbuj ponownie uruchomić aplikację.

2. Jeśli używasz aplikacji sieci Web w programie Internet Explorer, wyłącz debugowanie skryptów.

    Wyłącz debugowanie skryptu w oknie dialogowym Opcje internetowe. Dostęp do niego można uzyskać za pomocą opcji Sieć i Internet Internet **Panelu sterowania**  /  **Network and Internet**  /  **Internet Options** (dokładne kroki zależą od używanej wersji systemu Windows i programu Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Otwórz ponownie stronę sieci Web, na której znaleziono błąd. Jeśli to nie rozwiąże problemu, skontaktuj się z właścicielem aplikacji sieci Web, aby rozwiązać ten problem.

4. Jeśli używasz innego typu aplikacji systemu Windows, musisz skontaktować się z właścicielem aplikacji, aby rozwiązać ten problem, a następnie ponownie zainstalować stałą wersję aplikacji.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Jeśli chcesz naprawić lub debugować błąd (Użytkownicy zaawansowani)

- Musisz mieć [zainstalowany program Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) , aby wyświetlić szczegółowe informacje o błędzie i spróbować go debugować. Szczegółowe instrukcje można znaleźć w temacie [using JIT](#BKMK_Using_JIT) . Jeśli nie możesz rozwiązać tego błędu i naprawić aplikacji, skontaktuj się z właścicielem aplikacji, aby rozwiązać ten problem.

## <a name="enable-or-disable-just-in-time-debugging"></a><a name="BKMK_Enabling"></a> Włączanie lub wyłączanie debugowania just-in-Time
 Debugowanie just in time można włączyć lub wyłączyć w oknie dialogowym **Narzędzia/Opcje** programu Visual Studio.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Aby włączyć lub wyłączyć debugowanie just in Time

1. Otwórz program Visual Studio. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. W oknie dialogowym **Opcje** wybierz folder **debugowanie** .

3. W folderze **debugowanie** wybierz stronę **just-in-Time** .

4. W polu **Włącz debugowanie just in Time tego typu kodu** , zaznacz lub wyczyść odpowiednie typy programów: **zarządzane**, **natywne**lub **skrypt**.

    Aby wyłączyć debugowanie just in Time, po jego włączeniu należy uruchomić polecenie z uprawnieniami administratora. Włączenie debugowania just in Time ustawia klucz rejestru, a uprawnienia administratora są wymagane do zmiany tego klucza.

5. Kliknij przycisk **OK**.

   Debugowanie just in Time nadal może być włączone nawet wtedy, gdy program Visual Studio nie jest już zainstalowany na komputerze. Gdy program Visual Studio nie jest zainstalowany, nie można wyłączyć debugowania just in Time z okna dialogowego **Opcje** programu Visual Studio. W takim przypadku można wyłączyć debugowanie just in Time, edytując rejestr systemu Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Aby wyłączyć debugowanie just in time przez edycję rejestru

1. W menu **Start** Wyszukaj i uruchom polecenie `regedit.exe`

2. W oknie **Edytor rejestru** Znajdź i Usuń następujące wpisy rejestru:

    - HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework\DbgManagedDebugger

3. Jeśli na komputerze jest uruchomiony 64-bitowy system operacyjny, Usuń również następujące wpisy rejestru:

    - HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework\DbgManagedDebugger

4. Pamiętaj, aby nie przypadkowo usuwać ani zmieniać żadnych innych kluczy rejestru.

5. Zamknij okno **Edytor rejestru** .

> [!NOTE]
> Jeśli próbujesz wyłączyć debugowanie just in Time dla aplikacji po stronie serwera, a te kroki nie rozwiążą problemu, wyłącz debugowanie po stronie serwera w ustawieniach aplikacji usług IIS i ponów próbę.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Aby włączyć debugowanie just in Time formularza systemu Windows

1. Domyślnie aplikacje Windows Forms mają program obsługi wyjątków najwyższego poziomu, który umożliwia programowi kontynuowanie działania, jeśli można go odzyskać. Na przykład jeśli aplikacja Windows Forms zgłasza nieobsługiwany wyjątek, zobaczysz okno dialogowe podobne do następujących:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Aby włączyć debugowanie just in Time aplikacji Windows Forms, należy wykonać następujące dodatkowe czynności:

2. Ustaw `jitDebugging` wartość na `true` w `system.windows.form` sekcji pliku machine.config lub *\<application name>*.exe.config:

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. W aplikacji formularza systemu Windows w języku C++ należy również ustawić `DebuggableAttribute` w pliku config lub w kodzie. Jeśli kompilujesz z [/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) i bez [/og](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), kompilator ustawi dla Ciebie ten atrybut. Jeśli jednak chcesz debugować niezoptymalizowaną kompilację wydania, musisz ustawić ją samodzielnie. Możesz to zrobić, dodając następujący wiersz do pliku AssemblyInfo. cpp aplikacji:

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmk_using_jituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Korzystanie z debugowania just in Time
 Ta sekcja zawiera informacje o tym, co się stanie, gdy plik wykonywalny zgłosi wyjątek.

 Aby wykonać te kroki, musisz mieć zainstalowany program Visual Studio. Jeśli nie masz programu Visual Studio, możesz pobrać bezpłatnie [program Visual studio 2015 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/).

 Po zainstalowaniu programu Visual Studio debugowanie just in time jest domyślnie włączone.

 Na potrzeby tej sekcji wprowadzimy aplikację konsolową w języku C# w programie Visual Studio, która zgłasza <xref:System.NullReferenceException> .

 W programie Visual Studio Utwórz aplikację konsolową w języku C# (**plik/nowy/projekt/Visual C#/Aplikacja konsolowa**) o nazwie **ThrowsNullException**. Aby uzyskać więcej informacji na temat tworzenia projektów w programie Visual Studio, zobacz [Przewodnik: tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Gdy projekt zostanie otwarty w programie Visual Studio, Otwórz plik Program.cs. Zastąp metodę Main () następującym kodem, który drukuje linię do konsoli programu, a następnie zgłasza NullReferenceException:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> Aby ta procedura działała w [konfiguracji wydania](../debugger/how-to-set-debug-and-release-configurations.md), należy wyłączyć [tylko mój kod](../debugger/just-my-code.md). W programie Visual Studio kliknij pozycję **Narzędzia/Opcje**. W oknie dialogowym **Opcje** wybierz pozycję **debugowanie**. Usuń zaznaczenie opcji **włącz tylko mój kod**.

 Skompiluj rozwiązanie (w programie Visual Studio wybierz opcję **Kompiluj/Kompiluj rozwiązanie**). Można wybrać opcję debugowanie lub Konfiguracja wydania. Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).

 Proces kompilacji tworzy ThrowsNullException.exe pliku wykonywalnego. Można go znaleźć w folderze, w którym został utworzony projekt C#: **. ..\ThrowsNullException\ThrowsNullException\bin\Debug** lub **. ..\ThrowsNullException\ThrowsNullException\bin\Release**.

 Kliknij dwukrotnie ThrowsNullException.exe. Powinno zostać wyświetlone okno polecenia podobne do tego:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Po kilku sekundach zostanie wyświetlone okno błędu:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Nie klikaj przycisku **Anuluj**! Po kilku sekundach powinny zostać wyświetlone dwa przyciski, **Debuguj** i **Zamknij program**. Kliknij pozycję **Debuguj**.

> [!CAUTION]
> Jeśli aplikacja zawiera niezaufany kod, pojawi się okno dialogowe z ostrzeżeniem dotyczącym zabezpieczeń. To okno dialogowe umożliwia podjęcie decyzji o tym, czy kontynuować debugowanie. Przed kontynuowaniem debugowania Zdecyduj, czy ufasz kodowi. Czy udało Ci się napisać kod samodzielnie? Czy ufasz kodowi? Jeśli aplikacja jest uruchomiona na komputerze zdalnym, czy nazwa procesu jest rozpoznawana? Nawet jeśli aplikacja działa lokalnie, niekoniecznie oznacza to, że może być zaufana. Weź pod uwagę możliwość złośliwego kodu uruchomionego na komputerze. Jeśli zdecydujesz, że kod, który ma być debugowany, jest godny zaufania, kliknij pozycję **Debuguj**. W przeciwnym razie kliknij przycisk **nie Debuguj**.

 Zostanie wyświetlone okno **debuger just in Time programu Visual Studio** :

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 W obszarze **możliwe debugery**należy zobaczyć, że jest zaznaczone **nowe wystąpienie Microsoft Visual Studio wiersza 2015** . Jeśli ta opcja nie została jeszcze wybrana, wybierz ją teraz.

 W dolnej części okna, w obszarze **czy chcesz debugować przy użyciu wybranego debugera?** kliknij przycisk **tak**.

 Projekt ThrowsNullException zostanie otwarty w nowym wystąpieniu programu Visual Studio, a wykonywanie zostało zatrzymane w wierszu, który zgłasza wyjątek:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 Debugowanie można rozpocząć od tego momentu. Jeśli była to prawdziwa aplikacja, należy dowiedzieć się, dlaczego kod zgłasza wyjątek.

## <a name="just-in-time-debugging-errors"></a>Błędy debugowania just in Time
 Jeśli nie widzisz okna dialogowego, gdy wystąpi awaria programu, może to być spowodowane ustawieniami Raportowanie błędów systemu Windows na komputerze. Aby uzyskać więcej informacji, zobacz [. Ustawienia raportowania błędów systemu Windows](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Mogą pojawić się następujące komunikaty o błędach, które są skojarzone z debugowaniem just-in-Time.

- **Nie można dołączyć do procesu powodującego awarię. Określony program nie jest programem systemu Windows lub MS-DOS.**

     Ten błąd występuje podczas próby dołączenia do procesu działającego jako inny użytkownik.

     Aby obejść ten problem, uruchom program Visual Studio, Otwórz okno dialogowe **dołączanie do procesu** z menu **Debuguj** i Znajdź proces, który chcesz debugować, na liście **dostępne procesy** . Jeśli nie znasz nazwy procesu, zajrzyj do okna dialogowego **debuger just in Time programu Visual Studio** i zanotuj identyfikator procesu. Wybierz proces z listy **dostępne procesy** , a następnie kliknij pozycję **Dołącz**. W oknie dialogowym **debuger just in Time programu Visual Studio** kliknij przycisk **nie** , aby zamknąć okno dialogowe.

- **Nie można uruchomić debugera, ponieważ żaden użytkownik nie jest zalogowany.**

     Ten błąd występuje, gdy debugowanie just in Time próbuje uruchomić program Visual Studio na komputerze, na którym nie ma użytkownika zalogowanego na konsoli. Ponieważ żaden użytkownik nie jest zalogowany, nie istnieje sesja użytkownika, aby wyświetlić okno dialogowe debugowanie just-in-Time.

     Aby rozwiązać ten problem, zaloguj się na komputerze.

- **Klasa nie jest zarejestrowana.**

     Ten błąd wskazuje, że debuger próbował utworzyć klasę COM, która nie jest zarejestrowana, prawdopodobnie z powodu problemu z instalacją.

     Aby rozwiązać ten problem, użyj dysku instalacyjnego, aby ponownie zainstalować lub naprawić instalację programu Visual Studio.

## <a name="see-also"></a>Zobacz też
 Debuger [zabezpieczeń](../debugger/debugger-security.md) debugera [— Informacje podstawowe](../debugger/debugger-basics.md) [, debugowanie, Opcje okno dialogowe](../debugger/just-in-time-debugging-options-dialog-box.md) [ostrzeżenie zabezpieczeń: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)
