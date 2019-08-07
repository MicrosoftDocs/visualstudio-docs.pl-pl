---
title: Tworzenie rozszerzenia za pomocą polecenia menu | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cb82a2a5e02b2e109bb5b27ec54d1a2cd965901
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821540"
---
# <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu

W tym instruktażu pokazano, jak utworzyć rozszerzenie za pomocą polecenia menu, które uruchamia Notatnik.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Utwórz polecenie menu

1. Utwórz projekt VSIX o nazwie **FirstMenuCommand**. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** , wyszukując frazę "VSIX".

2. Po otwarciu projektu Dodaj niestandardowy szablon elementu polecenia o nazwie **FirstCommand**. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do  >  **rozszerzalności** **wizualizacji C#** i wybierz **polecenie niestandardowe**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na *FirstCommand.cs*.

3. Skompiluj projekt, a następnie rozpocząć debugowanie.

    Pojawia się eksperymentalne wystąpienie programu Visual Studio. Aby uzyskać więcej informacji o wystąpieniu eksperymentalnym, zobacz [wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. W eksperymentalnym wystąpieniu Otwórz okno **Narzędzia** > **rozszerzenia i aktualizacje** . Tutaj powinno być widoczne rozszerzenie **FirstMenuCommand** . (Jeśli otworzysz **rozszerzenia i aktualizacje** w działającym wystąpieniu programu Visual Studio, nie zobaczysz **FirstMenuCommand**).

::: moniker-end

::: moniker range=">=vs-2019"

4. W eksperymentalnym wystąpieniu Otwórz okno **rozszerzenia** > **Zarządzanie rozszerzeniami** . Tutaj powinno być widoczne rozszerzenie **FirstMenuCommand** . (Jeśli otworzysz **rozszerzenia** w działającym wystąpieniu programu Visual Studio, nie zobaczysz **FirstMenuCommand**).

::: moniker-end

Teraz przejdź do menu **Narzędzia** w wystąpieniu eksperymentalnym. Powinien pojawić się polecenie **Invoke FirstCommand** . W tym momencie polecenie wyświetla okno komunikatu z informacją, że **FirstCommandPackage wewnątrz FirstMenuCommand. FirstCommand. MenuItemCallback ()** . Zobaczymy, jak faktycznie uruchomić Notatnik z tego polecenia w następnej sekcji.

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

3. Usuń metodę i `StartNotepad` Dodaj metodę, która spowoduje jedynie uruchomienie Notatnika: `MenuItemCallback`

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Wypróbuj teraz. Po rozpoczęciu debugowania projektu i kliknięciu przycisku **Narzędzia** > **Wywołaj FirstCommand**należy zobaczyć wystąpienie Notatnika.

    Możesz użyć wystąpienia <xref:System.Diagnostics.Process> klasy do uruchamiania dowolnego pliku wykonywalnego, a nie tylko Notatnika. `calc.exe`Wypróbuj na przykład.

## <a name="clean-up-the-experimental-environment"></a>Wyczyść środowisko eksperymentalne

Jeśli tworzysz wiele rozszerzeń lub po prostu Eksplorowanie wyników przy użyciu różnych wersji kodu rozszerzenia, środowisko eksperymentalne może przestać działać w sposób. W takim przypadku należy uruchomić skrypt Reset. Jest on wywoływany przez **zresetowanie eksperymentalnego wystąpienia programu Visual Studio**i jest dostarczane jako część zestawu Visual Studio SDK. Ten skrypt usuwa wszystkie odwołania do rozszerzeń ze środowiska eksperymentalnego, więc możesz zacząć od podstaw.

Możesz uzyskać dostęp do tego skryptu na jeden z dwóch sposobów:

1. Na pulpicie Znajdź pozycję **Zresetuj wystąpienie eksperymentalne programu Visual Studio**.

2. W wierszu polecenia Uruchom następujące polecenie:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Wdróż rozszerzenie

Teraz, gdy masz już swoje rozszerzenie narzędzia, Możesz pomyśleć o udostępnianiu go przyjaciołom i współpracownikom. To bardzo proste, tak długo, jak ma zainstalowany program Visual Studio 2015. Wszystko, co musisz zrobić, wysyła do nich utworzony plik *. vsix* . (Pamiętaj, aby skompilować go w trybie wydania).

Plik *VSIX* dla tego rozszerzenia można znaleźć w katalogu bin *FirstMenuCommand* . W celu założenia, że została skompilowana konfiguracja wydania, będzie ona dostępna w:

*\<Katalog kodu > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand. vsix*

Aby zainstalować rozszerzenie, znajomy musi zamknąć wszystkie otwarte wystąpienia programu Visual Studio, a następnie kliknąć dwukrotnie plik *. vsix* , który powoduje uruchomienie **Instalatora VSIX**. Pliki są kopiowane do *%LocalAppData%\Microsoft\VisualStudio\<wersja > \Extensions* .

Gdy znajomy ponownie powróci do programu Visual Studio, znajdzie rozszerzenie FirstMenuCommand w obszarze **Narzędzia** > **rozszerzenia i aktualizacje**. Można również przejść do **rozszerzeń i aktualizacji** , aby odinstalować lub wyłączyć rozszerzenie.

## <a name="next-steps"></a>Następne kroki

W tym instruktażu przedstawiono tylko niewielką część tego, co można zrobić za pomocą rozszerzenia programu Visual Studio. Poniżej przedstawiono krótką listę innych (w sposób łatwy) czynności, które można wykonać za pomocą rozszerzeń programu Visual Studio:

1. Za pomocą prostego polecenia menu można wykonać wiele innych czynności:

   1. Dodaj własną ikonę: [Dodawanie ikon do poleceń menu](../extensibility/adding-icons-to-menu-commands.md)

   2. Zmień tekst polecenia menu: [Zmiana tekstu polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Dodaj skrót menu do polecenia: [Powiąż skróty klawiaturowe z elementami menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Dodaj różne rodzaje poleceń, menu i paski narzędzi: [Poszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)

3. Dodaj okna narzędzi i rozwiń wbudowane okna narzędzi programu Visual Studio: [Rozszerzone i dostosowane okna narzędzi](../extensibility/extending-and-customizing-tool-windows.md)

4. Dodawanie technologii IntelliSense, sugestii dotyczących kodu i innych funkcji do istniejących edytorów kodu: [Poszerzanie edytora i usług językowych](../extensibility/extending-the-editor-and-language-services.md)

5. Dodaj opcje i strony właściwości oraz ustawienia użytkownika do rozszerzenia: [Rozwiń Właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md) oraz [Rozwiń Ustawienia użytkownika i opcje](../extensibility/extending-user-settings-and-options.md)

   Inne rodzaje rozszerzeń wymagają nieco więcej pracy, takich jak tworzenie nowego typu projektu ([rozszerzanie projektów](../extensibility/extending-projects.md)), tworzenie nowego typu edytora ([Tworzenie edytorów niestandardowych i projektantów](../extensibility/creating-custom-editors-and-designers.md)) lub Wdrażanie rozszerzenia w izolowanej Shell: [Powłoka izolowana programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
