---
title: Tworzenie rozszerzenia za pomocą polecenia menu | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c8639ede4a01157718f0ab1a1514927e620fa8d
ms.sourcegitcommit: cb0c6e55ae560960a493df9ab56e3e9d9bc50100
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972338"
---
# <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu

W tym instruktażu pokazano, jak utworzyć rozszerzenie za pomocą polecenia menu, które uruchamia Notatnik.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Utwórz polecenie menu

1. Utwórz projekt VSIX o nazwie **FirstMenuCommand**. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** , wyszukując frazę "VSIX".

::: moniker range="vs-2017"

2. Po otwarciu projektu Dodaj niestandardowy szablon elementu polecenia o nazwie **FirstCommand**. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do rozszerzalności **Visual C#**  >  **Extensibility** i wybierz **polecenie niestandardowe**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na *FirstCommand.cs*.

::: moniker-end

::: moniker range=">=vs-2019"

2. Po otwarciu projektu Dodaj niestandardowy szablon elementu polecenia o nazwie **FirstCommand**. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do rozszerzalności **Visual C#**  >  **Extensibility** i wybierz **polecenie**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na *FirstCommand.cs*.

::: moniker-end

3. Skompiluj projekt i Rozpocznij debugowanie.

    Pojawia się eksperymentalne wystąpienie programu Visual Studio. Aby uzyskać więcej informacji o wystąpieniu eksperymentalnym, zobacz [wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. W eksperymentalnym wystąpieniu Otwórz okno **Narzędzia**  >  **rozszerzenia i aktualizacje** . Tutaj powinno być widoczne rozszerzenie **FirstMenuCommand** . (Jeśli otworzysz **rozszerzenia i aktualizacje** w działającym wystąpieniu programu Visual Studio, nie zobaczysz **FirstMenuCommand**).

::: moniker-end

::: moniker range=">=vs-2019"

4. W eksperymentalnym wystąpieniu Otwórz okno **rozszerzenia**  >  **Zarządzanie rozszerzeniami** . Tutaj powinno być widoczne rozszerzenie **FirstMenuCommand** . (Jeśli otworzysz **rozszerzenia** w działającym wystąpieniu programu Visual Studio, nie zobaczysz **FirstMenuCommand**).

::: moniker-end

Teraz przejdź do menu **Narzędzia** w wystąpieniu eksperymentalnym. Powinien pojawić się polecenie **Invoke FirstCommand** . W tym momencie polecenie wyświetla okno komunikatu z informacją, że **FirstCommand wewnątrz FirstMenuCommand. FirstCommand. MenuItemCallback ()**. Zobaczymy, jak faktycznie uruchomić Notatnik z tego polecenia w następnej sekcji.

## <a name="change-the-menu-command-handler"></a>Zmień procedurę obsługi poleceń menu

Teraz zaktualizujmy procedurę obsługi poleceń, aby uruchomić Notatnik.

1. Zatrzymaj debugowanie i wróć do działającego wystąpienia programu Visual Studio. Otwórz plik *FirstCommand.cs* i Dodaj następującą instrukcję using:

    ```csharp
    using System.Diagnostics;
    ```

2. Znajdź prywatnego konstruktora FirstCommand. Jest to miejsce, w którym polecenie jest podłączane do usługi poleceń i został określony program obsługi poleceń. Zmień nazwę programu obsługi poleceń na StartNotepad w następujący sposób:

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. Usuń `Execute` metodę i Dodaj `StartNotepad` metodę, która spowoduje jedynie uruchomienie Notatnika:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();

        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Wypróbuj teraz. Po rozpoczęciu debugowania projektu i kliknięciu przycisku **Narzędzia**  >  **Wywołaj FirstCommand**należy zobaczyć wystąpienie Notatnika.

    Możesz użyć wystąpienia <xref:System.Diagnostics.Process> klasy do uruchamiania dowolnego pliku wykonywalnego, a nie tylko Notatnika. Wypróbuj `calc.exe` na przykład.

## <a name="clean-up-the-experimental-environment"></a>Wyczyść środowisko eksperymentalne

Jeśli tworzysz wiele rozszerzeń lub po prostu Eksplorowanie wyników przy użyciu różnych wersji kodu rozszerzenia, środowisko eksperymentalne może przestać działać w sposób. W takim przypadku należy uruchomić skrypt Reset. Jest on wywoływany przez **zresetowanie eksperymentalnego wystąpienia programu Visual Studio**i jest dostarczane jako część zestawu Visual Studio SDK. Ten skrypt usuwa wszystkie odwołania do rozszerzeń ze środowiska eksperymentalnego, więc możesz zacząć od podstaw.

Możesz uzyskać dostęp do tego skryptu na jeden z dwóch sposobów:

1. Na pulpicie Znajdź pozycję **Zresetuj wystąpienie eksperymentalne programu Visual Studio**.

2. W wierszu polecenia Uruchom następujące polecenie:

    ```cmd
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Wdróż rozszerzenie

Teraz, gdy masz już swoje rozszerzenie narzędzia, Możesz pomyśleć o udostępnianiu go przyjaciołom i współpracownikom. To bardzo proste, tak długo, jak ma zainstalowany program Visual Studio 2015. Wszystko, co musisz zrobić, wysyła do nich utworzony plik *. vsix* . (Pamiętaj, aby skompilować go w trybie wydania).

Plik *VSIX* dla tego rozszerzenia można znaleźć w katalogu bin *FirstMenuCommand* . W celu założenia, że została skompilowana konfiguracja wydania, będzie ona dostępna w:

*\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\FirstMenuCommand.vsix*

Aby zainstalować rozszerzenie, znajomy musi zamknąć wszystkie otwarte wystąpienia programu Visual Studio, a następnie kliknąć dwukrotnie plik *. vsix* , który powoduje uruchomienie **Instalatora VSIX**. Pliki są kopiowane do katalogu *%LocalAppData%\Microsoft\VisualStudio \<version> \Extensions* .

Gdy znajomy ponownie powróci do programu Visual Studio, znajdzie rozszerzenie FirstMenuCommand w obszarze **Narzędzia**  >  **rozszerzenia i aktualizacje**. Można również przejść do **rozszerzeń i aktualizacji** , aby odinstalować lub wyłączyć rozszerzenie.

## <a name="next-steps"></a>Następne kroki

W tym instruktażu przedstawiono tylko niewielką część tego, co można zrobić za pomocą rozszerzenia programu Visual Studio. Poniżej przedstawiono krótką listę innych (w sposób łatwy) czynności, które można wykonać za pomocą rozszerzeń programu Visual Studio:

1. Za pomocą prostego polecenia menu można wykonać wiele innych czynności:

   1. Dodaj własną ikonę: [Dodaj ikony do poleceń menu](../extensibility/adding-icons-to-menu-commands.md)

   2. Zmień tekst polecenia menu: [Zmiana tekstu polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Dodaj skrót menu do polecenia: [Powiąż skróty klawiaturowe z elementami menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Dodaj różne rodzaje poleceń, menu i paski narzędzi: [Rozwiń menu i polecenia](../extensibility/extending-menus-and-commands.md)

3. Dodaj okna narzędzi i rozwiń wbudowane okna narzędzi programu Visual Studio: [rozszerzone i dostosowane okna narzędzi](../extensibility/extending-and-customizing-tool-windows.md)

4. Dodawanie technologii IntelliSense, sugestii dotyczących kodu i innych funkcji do istniejących edytorów kodu: [poszerzanie edytora i usług językowych](../extensibility/extending-the-editor-and-language-services.md)

5. Dodawanie opcji i stron właściwości oraz ustawień użytkownika do rozszerzenia: [Rozszerzanie właściwości i okna właściwości](../extensibility/extending-properties-and-the-property-window.md) oraz [rozszerzanie ustawień i opcji użytkownika](../extensibility/extending-user-settings-and-options.md)

   Inne rodzaje rozszerzeń wymagają nieco więcej pracy, takich jak tworzenie nowego typu projektu ([rozszerzanie projektów](../extensibility/extending-projects.md)), tworzenie nowego typu edytora ([Tworzenie edytorów niestandardowych i projektantów](../extensibility/creating-custom-editors-and-designers.md)) lub Wdrażanie rozszerzenia w izolowanej Shell: [powłoka izolowana programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
