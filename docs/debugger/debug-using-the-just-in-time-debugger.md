---
title: Debugowanie przy użyciu debugera just in time | Microsoft Docs
description: Debuguj przy użyciu debugera just in time w Visual Studio. Debugowanie just in time może automatycznie Visual Studio w przypadku błędów lub awarii aplikacji.
ms.custom: SEO-VS-2020
ms.date: 09/24/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3bdd35056706491ace6e5e6b2f7c3f6a45464d2e
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729250"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Debugowanie przy użyciu debugera just in time w Visual Studio

Debugowanie just in time może automatycznie uruchamiać Visual Studio, gdy aplikacja uruchomiona poza Visual Studio błędy lub awarie. W przypadku debugowania just in time można testować aplikacje poza Visual Studio i otwierać Visual Studio, aby rozpocząć debugowanie w przypadku wystąpienia problemu.

Debugowanie just in time działa w przypadku aplikacji klasycznych systemu Windows. Nie działa w przypadku aplikacji uniwersalnych systemu Windows ani kodu zarządzanego, który jest hostowany w aplikacji natywnej, takiej jak Wizualizatory.

> [!TIP]
> Jeśli chcesz tylko zatrzymać wyświetlanie okna dialogowego Debuger just in time, ale nie masz zainstalowanych Visual Studio, zobacz Wyłączanie debugera just [in time.](../debugger/just-in-time-debugging-in-visual-studio.md) Jeśli po zainstalowaniu Visual Studio, może być konieczne wyłączenie debugowania [just in time z rejestru systemu Windows.](#disable-just-in-time-debugging-from-the-windows-registry)

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Włączanie lub wyłączanie debugowania just in time w programie Visual Studio

>[!NOTE]
>Aby włączyć lub wyłączyć debugowanie just in time, musisz uruchamiać Visual Studio jako administrator. Włączenie lub wyłączenie debugowania just in time ustawia klucz rejestru, a do zmiany tego klucza mogą być wymagane uprawnienia administratora. Aby otworzyć Visual Studio jako administrator, kliknij prawym przyciskiem myszy aplikację Visual Studio i wybierz **polecenie Uruchom jako administrator.**

Debugowanie just in time można skonfigurować w oknie dialogowym Opcje Visual Studio **(lub**  >   **Opcje**  >  debugowania).

**Aby włączyć lub wyłączyć debugowanie just in time:**

1. W menu **Narzędzia** lub **Debugowanie** wybierz pozycję **Opcje**  >    >  **Debugowanie just in time.**

   ![Włączanie lub wyłączanie debugowania JIT](../debugger/media/dbg-jit-enable-or-disable.png "Włączanie lub wyłączanie debugowania JIT")

1. W polu Włącz debugowanie just **in time** dla tych typów kodu wybierz typy kodu, które mają być debugowane przez debugowanie just in **time:** **zarządzany,** natywny , i/lub **skrypt**.

1. Wybierz przycisk **OK**.

Jeśli włączysz debuger just in time, ale nie zostanie otwarty, gdy aplikacja ulega awarii lub występują błędy, zobacz [Troubleshoot Just-In-Time debugging](#jit_errors)(Rozwiązywanie problemów z debugowaniem just in time).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Wyłączanie debugowania just in time z rejestru systemu Windows

Debugowanie just in time może być nadal włączone, nawet Visual Studio nie jest już zainstalowane na komputerze. Jeśli Visual Studio nie jest już zainstalowany, możesz wyłączyć debugowanie just in time, edytując rejestr systemu Windows.

**Aby wyłączyć debugowanie just in time, edytując rejestr:**

1. W menu **Start systemu** Windows uruchom Edytor **rejestru** (*regedit.exe*).

2. W **oknie Edytor** rejestru znajdź i usuń następujące wpisy rejestru:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ . NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Klucz rejestru JIT](../debugger/media/dbg-jit-registry.png "Klucz rejestru JIT")

3. Jeśli na komputerze jest uruchomiony 64-bitowy system operacyjny, usuń również następujące wpisy rejestru:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\ . NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Upewnij się, że nie usuwasz ani nie zmieniasz żadnych innych kluczy rejestru.

5. Zamknij okno **Edytor rejestru.**

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Włączanie debugowania just in time formularza systemu Windows

Domyślnie aplikacje formularzy systemu Windows mają program obsługi wyjątków najwyższego poziomu, który umożliwia aplikacji działanie w przypadku odzyskiwania. Jeśli aplikacja Windows Forms zgłasza nieobsługiwany wyjątek, zostanie wyświetlone następujące okno dialogowe:

![Nieobsługiwany wyjątek formularza systemu Windows](../debugger/media/windowsformsunhandledexception.png "Nieobsługiwany wyjątek formularza systemu Windows")

Aby włączyć debugowanie just in time zamiast standardowej obsługi błędów formularza systemu Windows, dodaj następujące ustawienia:

- W `system.windows.forms` sekcji pliku *machine.config* *\<app name> lub.exe.config* ustaw wartość na `jitDebugging` `true` :

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- W aplikacji Formularz systemu Windows w języku C++ ustaw również wartość w pliku `DebuggableAttribute` `true` *config* lub w kodzie. W przypadku kompilacji [z /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) i bez [/Og](/cpp/build/reference/og-global-optimizations)kompilator ustawia ten atrybut za Ciebie. Jeśli jednak chcesz debugować niezoptymacyjną kompilację wydania, musisz to zrobić, dodając następujący wiersz w pliku `DebuggableAttribute` *AssemblyInfo.cpp* aplikacji:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Korzystanie z debugowania just in time
W tym przykładzie oswaja cię przez debugowanie just in time, gdy aplikacja zgłasza błąd.

- Aby wykonać te Visual Studio, musisz mieć zainstalowane oprogramowanie. Jeśli nie masz jeszcze wersji Visual Studio, możesz pobrać bezpłatną wersję [Visual Studio Community Edition.](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)

- Upewnij się, że debugowanie just in time jest włączone w [opcji](#BKMK_Enabling) **Narzędzia**  >    >  **Debugowanie**  >  **just in time.**

W tym przykładzie w języku C# zostanie w języku Visual Studio zgłaszany jest wyjątek [NullReferenceException.](/dotnet/api/system.nullreferenceexception)

1. W Visual Studio utwórz aplikację konsoli języka C#**(File**  >  **New**  >  **Project**  >  **Visual C#** Console  >  **Application**) o nazwie *ThrowsNullException*. Aby uzyskać więcej informacji na temat tworzenia projektów w Visual Studio, [zobacz Przewodnik: tworzenie prostej aplikacji.](../get-started/csharp/tutorial-wpf.md)

1. Po otwarciu projektu w Visual Studio otwórz *plik Program.cs.* Zastąp metodę Main() następującym kodem, który drukuje wiersz w konsoli, a następnie zgłasza wyjątek NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Aby skompilować rozwiązanie, wybierz konfigurację **Debuguj** (ustawienie domyślne) lub **Wydanie,** a następnie wybierz pozycję **Skompilowaj**  >  **ponownie rozwiązanie.**

   > [!NOTE]
   > - Wybierz **pozycję Konfiguracja** debugowania, aby uzyskać pełne środowisko debugowania.
   > - W przypadku wybrania [opcji Konfiguracja](../debugger/how-to-set-debug-and-release-configurations.md) wydania należy wyłączyć tę [Tylko mój kod,](../debugger/just-my-code.md) aby ta procedura działała. W **obszarze Narzędzia** Opcje  >    >  **debugowania** usuń zaznaczenie **opcji Włącz Tylko mój kod**.

   Aby uzyskać więcej informacji na temat konfiguracji kompilacji, zobacz [Understanding build configurations (Opis konfiguracji kompilacji).](../ide/understanding-build-configurations.md)

1. Otwórz sbudowaną aplikację *ThrowsNullException.exe* folderze projektu języka C# (*...\ThrowsNullException\ThrowsNullException\bin\Debug* lub *...\ThrowsNullException\ThrowsNullException\bin\Release).*

   Powinno zostać wyświetlony następujące okno polecenia:

   ![Zrzut ekranu przedstawiający konsolę programu ThrowsNullException.exe, który zgłasza nieobsługiwany wyjątek odwołania o wartości null (System.NullReferenceException).](../debugger/media/throwsnullexceptionconsole.png)

1. Zostanie otwarte okno dialogowe **Wybieranie debugera just in time.**

   ![Zrzut ekranu przedstawiający okno dialogowe Wybieranie debugera just in time, które pojawia się po wyjątku w ThrowsNullException.exe konsoli.](../debugger/media/justintimedialog.png)

   W **obszarze Dostępne debugery** wybierz **pozycję Nowe \<your preferred Visual Studio version/edition> wystąpienie** klasy , jeśli nie zostało jeszcze wybrane.

1. Wybierz przycisk **OK**.

   Projekt ThrowsNullException otwiera się w nowym wystąpieniu klasy Visual Studio, a wykonywanie zostało zatrzymane w wierszu, który zrzucił wyjątek:

   ![Zrzut ekranu przedstawiający projekt ThrowsNullException w Visual Studio, z wyróżnieniem wiersza kodu źródłowego, który zwrócił wyjątek.](../debugger/media/nullreferencesecondinstance.png)

W tym momencie możesz rozpocząć debugowanie. Jeśli debugujesz rzeczywistą aplikację, musisz dowiedzieć się, dlaczego kod zgłasza wyjątek.

> [!CAUTION]
> Jeśli aplikacja zawiera niezaufany kod, zostanie wyświetlone okno dialogowe ostrzeżenia o zabezpieczeniach umożliwiające podjęcie decyzji, czy kontynuować debugowanie. Przed kontynuowaniem debugowania zdecyduj, czy ufasz kodowi. Czy kod został napisać samodzielnie? Jeśli aplikacja jest uruchomiona na maszynie zdalnej, czy rozpoznajesz nazwę procesu? Jeśli aplikacja działa lokalnie, rozważ możliwość uruchomienia złośliwego kodu na komputerze. Jeśli zdecydujesz, że kod jest godny zaufania, wybierz **przycisk OK**. W przeciwnym razie wybierz pozycję **Anuluj.**

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Rozwiązywanie problemów z debugowaniem just in time

Jeśli debugowanie just in time nie uruchamia się, gdy aplikacja ulega awarii, mimo że jest włączona w Visual Studio:

- Raportowanie błędów systemu Windows może przejmować obsługę błędów na komputerze.

  Aby rozwiązać ten problem, użyj Edytora rejestru, aby  dodać wartość **DWORD** **Disabled** z danymi o wartości **1** do następujących kluczy rejestru:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (W przypadku maszyn 64-bitowych): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**

  Aby uzyskać więcej informacji, zobacz [. Ustawienia WER](/windows/desktop/wer/wer-settings).

- Znany problem z systemem Windows może powodować niepowodzenie debugera just in time.

  Aby rozwiązać ten problem, należy dodać  wartość **DWORD** auto **z** danymi o wartości **1** do następujących kluczy rejestru:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (W przypadku maszyn 64-bitowych): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Podczas debugowania just in time mogą pojawić się następujące komunikaty o błędach:

- **Nie można dołączyć do procesu awarii. Określony program nie jest programem systemu Windows ani MS-DOS.**

    Debuger próbował dołączyć do procesu uruchomionego w ramach innego użytkownika.

    Aby rozwiązać ten problem, w Visual Studio otwórz polecenie **Debuguj** dołączanie do procesu (lub naciśnij klawisze  >   **Ctrl**  +  **Alt** P  +  ) i znajdź proces, który chcesz debugować, na liście **Dostępne procesy.** Jeśli nie znasz nazwy procesu, znajdź identyfikator procesu w oknie **dialogowym Visual Studio debuger** just in time. Wybierz proces z listy **Dostępne procesy,** a następnie wybierz pozycję **Dołącz**. Wybierz **pozycję Nie,** aby odrzucić okno dialogowe debugera just in time.

- **Nie można rozpocząć debugera, ponieważ żaden użytkownik nie jest zalogowany.**

    W konsoli nie jest zalogowany żaden użytkownik, więc nie ma sesji użytkownika do wyświetlania okna dialogowego debugowania just in time.

    Aby rozwiązać ten problem, zaloguj się na maszynie.

- **Klasa nie jest zarejestrowana.**

    Debuger próbował utworzyć klasę COM, która nie jest zarejestrowana, prawdopodobnie z powodu problemu z instalacją.

    Aby rozwiązać ten problem, użyj Instalator programu Visual Studio, aby ponownie zainstalować lub naprawić Visual Studio instalacji.

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Opcje, debugowanie, okno dialogowe Just-In-Time](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
