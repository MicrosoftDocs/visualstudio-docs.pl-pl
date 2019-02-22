---
title: Debugowanie za pomocą debugera just in Time | Dokumentacja firmy Microsoft
ms.date: 09/24/18
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5300417f7a84292528ff6e1eaea439d7fe82f43
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636687"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Debugowanie w programie Visual Studio za pomocą debugera just in Time

Debugowanie Just In Time uruchomić program Visual Studio automatycznie podczas uruchamiania poza programem Visual Studio błędy lub awarie aplikacji. Za pomocą Just-In-Time debugging można testować aplikacje poza programem Visual Studio i Otwórz program Visual Studio, aby rozpocząć debugowanie, jeśli wystąpi problem.

Debugowanie Just In Time działa w przypadku aplikacji komputerowych Windows. Nie działa dla uniwersalnych aplikacji dla Windows lub dla kodu zarządzanego, który znajduje się w aplikacji macierzystej, jak na przykład Wizualizatory.

> [!TIP]
> Jeśli chcesz zatrzymać okno dialogowe debuger just in Time pojawianiu się, ale nie ma zainstalowanego programu Visual Studio, zobacz [wyłączyć debuger just in Time](../debugger/just-in-time-debugging-in-visual-studio.md). Jeśli po był zainstalowany program Visual Studio, konieczne może być [wyłączyć Just-In-Time, debugowanie z rejestru Windows](#disable-just-in-time-debugging-from-the-windows-registry).

##  <a name="BKMK_Enabling"></a> Włączanie lub wyłączanie debugowania w programie Visual Studio Just-In-Time

>[!NOTE]
>Aby włączyć lub wyłączyć debugowanie Just In Time, że uruchomione programu Visual Studio jako administrator. Włączanie lub wyłączanie Just-In-Time debugging Ustawia klucz rejestru i może być wymagane uprawnienia administratora, aby zmienić ten klucz. Aby otworzyć program Visual Studio jako administrator, kliknij prawym przyciskiem myszy aplikację programu Visual Studio, a następnie wybierz **Uruchom jako administrator**.

Można skonfigurować debugowania programu Visual Studio Just-In-Time **narzędzia** > **opcje** (lub **debugowania** > **opcje**) okno dialogowe.

**Aby włączyć lub wyłączyć Just-In-Time debugowanie:**

1. Na **narzędzia** lub **debugowania** menu, wybierz opcję **opcje** > **debugowanie**  >   **Just In Time**.

   ![Włączanie lub wyłączanie debugowania JIT](../debugger/media/dbg-jit-enable-or-disable.png "włączyć lub wyłączyć debugowanie JIT")

1. W **włączyć debugowanie just in Time dla tych typów kodu** wybierz typy kodu, które chcesz, aby debugowanie debugowania Just In Time: **Zarządzane**, **natywnych**, i/lub **skryptu**.

1. Kliknij przycisk **OK**.

Po włączeniu Just-In-Time debugera, ale nie zostanie otwarte, gdy aplikacja ulegnie awarii lub błędy, zobacz [Rozwiązywanie problemów z debudowanie](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Wyłącz debugowanie z rejestru Windows Just In Time

Debugowanie Just In Time może być wciąż włączone, nawet jeśli program Visual Studio nie jest już zainstalowane na tym komputerze. Jeśli program Visual Studio nie jest już zainstalowany, możesz wyłączyć debugowanie, edytując Rejestr Windows Just In Time.

**Aby wyłączyć debugowanie, edytując rejestr Just In Time:**

1.  Od Windows **Start** menu, uruchom **Edytora rejestru** (*regedit.exe*).

2.  W **Edytora rejestru** okna, zlokalizuj i Usuń następujące wpisy rejestru:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Klucz rejestru JIT](../debugger/media/dbg-jit-registry.png "klucza rejestru JIT")

3.  Jeśli komputer działa w 64-bitowym systemie operacyjnym, także Usuń następujące wpisy rejestru:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Upewnij się nie usunąć ani zmienić żadnych kluczy rejestru.

5.  Zamknij **Edytora rejestru** okna.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Włącz Just-In-Time debugowanie formularza Windows

Domyślnie aplikacje Windows formularza mają program obsługi wyjątków najwyższego poziomu, który umożliwia aplikacji działały, jeśli możliwe jest odzyskiwanie. Jeśli w aplikacji Windows Forms zwraca nieobsługiwany wyjątek, przedstawia następujące okno dialogowe:

![Formularz Windows nieobsłużony wyjątek](../debugger/media/windowsformsunhandledexception.png "formularza Windows nieobsługiwany wyjątek")

Aby włączyć debugowanie zamiast standardowego obsługi błędów formularza Windows Just In Time, należy dodać te ustawienia:

-  W `system.windows.forms` części *machine.config* lub  *\<Nazwa aplikacji >. exe.config* plików, należy ustawić `jitDebugging` wartość `true`:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

-  W aplikacji formularzy Windows w języku C++, należy również ustawić `DebuggableAttribute` do `true` w *.config* plików lub w kodzie. Jeśli kompilujesz z opcją [/zi](/cpp/build/reference/z7-zi-zi-debug-information-format) i bez [/Og](/cpp/build/reference/og-global-optimizations), kompilator ustawia ten atrybut. Jeśli chcesz debugować kompilację niezoptymalizowanego wydania, jednak należy ustawić `DebuggableAttribute` , dodając następujący wiersz w swojej aplikacji *AssemblyInfo.cpp* pliku:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="BKMK_Using_JIT"></a>Użyj Just-In-Time debugging
 W tym przykładzie przedstawiono w przypadku aplikacji zgłasza błąd debugowania Just In Time.

 - Konieczne jest posiadanie programu Visual Studio wykonaj następujące kroki. Jeśli nie masz programu Visual Studio, możesz pobrać bezpłatną [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

 - Upewnij się, że Just-In-Time debugging jest [włączone](#BKMK_Enabling) w **narzędzia** > **opcje** > **debugowanie**  >  **Just-In-Time**.

Na przykład wprowadzisz aplikację konsoli C# w programie Visual Studio, które zgłasza [obiektu NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. W programie Visual Studio, tworzenie aplikacji konsolowej C# (**pliku** > **New** > **projektu** > **Visual C#**  >  **Aplikację konsolową**) o nazwie *ThrowsNullException*. Aby uzyskać więcej informacji dotyczących tworzeniu projektów w programie Visual Studio, zobacz [instruktażu: Tworzenie prostej aplikacji](/visualstudio/get-started/csharp/tutorial-wpf).

1. Po otwarciu projektu w programie Visual Studio, otwórz *Program.cs* pliku. Zastąp następujący kod, który wyświetla wiersz do konsoli i następnie zgłasza obiektu NullReferenceException metody Main():

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Aby skompilować rozwiązanie, wybierz **debugowania** (ustawienie domyślne) lub **wersji** konfiguracji, a następnie wybierz **kompilacji** > **Kompiluj ponownie rozwiązanie** .

   > [!NOTE]
   > - Wybierz **debugowania** konfiguracji do pełnego środowiska debugowania.
   > - Jeśli wybierzesz [wersji](../debugger/how-to-set-debug-and-release-configurations.md) konfiguracji, należy wyłączyć [tylko mój kod](../debugger/just-my-code.md) do wykonania tej procedury do pracy. W obszarze **narzędzia** > **opcje** > **debugowanie**, usuń zaznaczenie opcji **Włącz tylko mój kod**.

   Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).

1. Otwórz aplikację utworzonych *ThrowsNullException.exe* w folderze projektu C# (*...\ThrowsNullException\ThrowsNullException\bin\Debug* lub *...\ThrowsNullException\ ThrowsNullException\bin\Release*).

   Powinny zostać wyświetlone następujące okno polecenia:

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. **Wybierz debuger just in Time** zostanie otwarte okno dialogowe.

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   W obszarze **dostępne debugery**, wybierz opcję **nowe wystąpienie klasy \<Twojego preferowanego wersji programu Visual Studio/wydania >**, jeśli jeszcze nie wybrano.

1. Kliknij przycisk **OK**.

   Projekt ThrowsNullException zostanie otwarty w nowym wystąpieniu programu Visual Studio z wykonywaniem został zatrzymany na wierszu, który wygenerował wyjątek:

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

Można rozpocząć debugowania na tym etapie. Gdybyś debugował rzeczywistej aplikacji należy dowiedzieć się, dlaczego kod zgłasza wyjątek.

> [!CAUTION]
> Jeśli aplikacja zawiera niezaufanego kodu, pojawi się okno dialogowe ostrzeżenia o zabezpieczeniach, dzięki któremu można zdecydować, czy chcesz kontynuować debugowanie. Przed kontynuowaniem debugowania, należy zdecydować, czy kodowi można zaufać. Czy napisałeś kod samodzielnie? Jeśli aplikacja jest uruchomiona na komputerze zdalnym, czy rozpoznajesz nazwę procesu? Jeśli aplikacja działa lokalnie, należy wziąć pod uwagę możliwość złośliwy kod uruchomiony na Twoim komputerze. Kod jest godny zaufania, należy zaznaczyć opcję **OK**. W przeciwnym razie wybierz **anulować**.

## <a name="jit_errors"></a> Rozwiązywanie problemów z Just-In-Time debugging

Jeśli Just-In-Time debugowania nie zaczyna się, gdy aplikacja ulegnie awarii, nawet jeśli jest włączona w programie Visual Studio:

- Raportowanie błędów Windows może biorąc błędów, obsługę na tym komputerze.

  Aby rozwiązać ten problem, użyj Edytora rejestru w celu dodania **wartość DWORD** z **wyłączone**, za pomocą **dane wartości** z **1**, do następujących kluczy rejestru:

  - **Raportowanie błędów HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows**

  - (Dla 64-bitowych komputerów): **Raportowanie błędów HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows**

  Aby uzyskać więcej informacji, zobacz [. Ustawienia raportowania błędów systemu Windows](https://docs.microsoft.com/windows/desktop/wer/wer-settings).

- Znany problem Windows może być przyczyną Just-In-Time debugera, aby zakończyć się niepowodzeniem.

  Poprawka jest dodanie **wartość DWORD** z **automatycznie**, za pomocą **dane wartości** z **1**, do następujących kluczy rejestru:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Dla 64-bitowych komputerów): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Można napotkać następujące komunikaty o błędach podczas Just-In-Time debugging:

- **Nie można dołączyć do procesu powodującego awarię. Określony program nie jest programem Windows ani MS-DOS.**

    Debuger próbował dołączanie do procesu uruchomionego w ramach innego użytkownika.

    Aby obejść ten problem, w programie Visual Studio, otwórz **debugowania** > **dołączyć do procesu**i Znajdź proces, który chcesz debugować w **dostępne procesy** Lista. Jeśli nie znasz nazwy procesu, Znajdź identyfikator procesu w **debuger just in Time programu Visual Studio** okna dialogowego. Wybierz proces na **dostępne procesy** listy i wybierz **Dołącz**. Wybierz **nie** odrzucać Just-In-Time okno dialogowe debugera.

- **Nie można uruchomić debugera, ponieważ żaden użytkownik nie jest zalogowany.**

    Nie ma żadnego użytkownika zalogowany do konsoli, dlatego żadna sesja użytkownika, aby wyświetlić Just-In-Time debugging okna dialogowego.

    Aby rozwiązać ten problem, należy zalogować się na komputerze.

- **Klasa nie jest zarejestrowana.**

    Debuger próbował utworzyć klasę modelu COM, który nie jest zarejestrowana, prawdopodobnie z powodu problemu z instalacją.

    Aby rozwiązać ten problem, należy użyć Instalatora programu Visual Studio ponownie zainstalować lub naprawić instalację programu Visual Studio.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Opcje debugowania Just-In-Time okno dialogowe](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub nie masz do nich pełnego zaufania, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)