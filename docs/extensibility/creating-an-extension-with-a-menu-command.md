---
title: Tworzenie rozszerzenia za pomocą polecenia menu | Dokumenty firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
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
ms.openlocfilehash: da1be8c6e00efd5d9ac94e53bf551d82d0f17ca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739558"
---
# <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu

W tym przewodniku pokazano, jak utworzyć rozszerzenie za pomocą polecenia menu uruchamianego Notatnika.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Tworzenie polecenia menu

1. Utwórz projekt VSIX o nazwie **FirstMenuCommand**. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt,** wyszukując "vsix".

2. Po otwarciu projektu dodaj niestandardowy szablon elementu polecenia o nazwie **FirstCommand**. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. W oknie dialogowym **Dodawanie nowego elementu** przejdź do pozycji**Rozszerzalność** **programu Visual C#** > i wybierz polecenie **Niestandardowe**. W polu **Nazwa** u dołu okna zmień nazwę pliku polecenia na *FirstCommand.cs*.

3. Skompiluj projekt i rozpocznij debugowanie.

    Pojawi się eksperymentalne wystąpienie programu Visual Studio. Aby uzyskać więcej informacji na temat wystąpienia eksperymentalnego, zobacz [Wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. W wystąpieniu eksperymentalnym otwórz okno**Rozszerzenia i aktualizacje** **narzędzi.** >  W tym miejscu powinno zostać wyświetlona rozszerzenie **FirstMenuCommand.** (Jeśli otworzysz **rozszerzenia i aktualizacje** w wystąpieniu roboczym programu Visual Studio, nie zobaczysz **funkcji FirstMenuCommand).**

::: moniker-end

::: moniker range=">=vs-2019"

4. W wystąpieniu eksperymentalnym otwórz okno **Zarządzanie rozszerzeniami rozszerzeń.** > **Manage Extensions** W tym miejscu powinno zostać wyświetlona rozszerzenie **FirstMenuCommand.** (Jeśli otworzysz **Zarządzanie rozszerzeniami** w wystąpieniu roboczym programu Visual Studio, nie zobaczysz **funkcji FirstMenuCommand).**

::: moniker-end

Teraz przejdź do menu **Narzędzia** w wystąpieniu eksperymentalnym. Powinien zostać wyświetlony **polecenie Invoke FirstCommand.** W tym momencie polecenie wywołuje okno komunikatu z napisem **FirstCommandPackage Inside FirstMenuCommand.FirstCommand.MenuItemCallback()**. Zobaczymy, jak faktycznie uruchomić Notatnik z tego polecenia w następnej sekcji.

## <a name="change-the-menu-command-handler"></a>Zmienianie programu obsługi poleceń menu

Teraz zaktualizujmy program obsługi poleceń, aby uruchomić Notatnik.

1. Zatrzymaj debugowanie i wróć do działającego wystąpienia programu Visual Studio. Otwórz plik *FirstCommand.cs* i dodaj następującą instrukcję:

    ```csharp
    using System.Diagnostics;
    ```

2. Znajdź prywatny konstruktor FirstCommand. W tym miejscu polecenie jest podłączone do usługi poleceń i określono program obsługi poleceń. Zmień nazwę programu obsługi poleceń na StartNotepad w następujący sposób:

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

3. Usuń `MenuItemCallback` metodę i `StartNotepad` dodaj metodę, która po prostu uruchomi Notatnik:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Teraz wypróbuj. Po uruchomieniu debugowania projektu i kliknij polecenie **Narzędzia** > **Wywołaj PierwszyKommanda**, powinno zostać wyświetlona wystąpienie Notatnika.

    Można użyć wystąpienia klasy, <xref:System.Diagnostics.Process> aby uruchomić dowolny plik wykonywalny, nie tylko Notatnik. Spróbuj go `calc.exe`na przykład z , na przykład.

## <a name="clean-up-the-experimental-environment"></a>Oczyszczanie środowiska doświadczalnego

Jeśli tworzysz wiele rozszerzeń lub po prostu eksplorowanie wyników z różnych wersji kodu rozszerzenia, środowisko eksperymentalne może przestać działać tak, jak powinno. W takim przypadku należy uruchomić skrypt resetowania. Nazywa się **Resetowanie wystąpienia eksperymentalnego programu Visual Studio**i jest dostarczany jako część SDK programu Visual Studio. Ten skrypt usuwa wszystkie odwołania do rozszerzeń ze środowiska eksperymentalnego, dzięki czemu można rozpocząć od zera.

Możesz przejść do tego skryptu na jeden z dwóch sposobów:

1. Na pulpicie znajdź **pozycję Resetowanie wystąpienia eksperymentalnego programu Visual Studio**.

2. W wierszu polecenia uruchom następujące czynności:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Wdrażanie rozszerzenia

Teraz, gdy masz rozszerzenie narzędzia działa tak, jak chcesz, nadszedł czas, aby pomyśleć o udostępnieniu go znajomym i współpracownikom. To proste, o ile mają zainstalowane programu Visual Studio 2015. Wszystko, co musisz zrobić, to wysłać im plik *.vsix,* który zbudowałeś. (Pamiętaj, aby utworzyć go w trybie wydania.)

Plik *vsix* dla tego rozszerzenia można znaleźć w katalogu *pojemnika FirstMenuCommand.* W szczególności, zakładając, że zbudowano konfigurację wydania, będzie on w:

*\<katalog kodu>\FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix*

Aby zainstalować rozszerzenie, znajomy musi zamknąć wszystkie otwarte wystąpienia programu Visual Studio, a następnie dwukrotnie kliknąć plik *.vsix,* który powoduje wyświetlenie **Instalatora VSIX**. Pliki są kopiowane do *katalogu %LocalAppData%\Microsoft\VisualStudio\<>\Extensions.*

Gdy znajomy ponownie wygeneruje program Visual Studio, znajdzie rozszerzenie FirstMenuCommand w**rozszerzeniach i aktualizacjach** **narzędzi.** >  Mogą przejść do **rozszerzeń i aktualizacji,** aby odinstalować lub wyłączyć rozszerzenie.

## <a name="next-steps"></a>Następne kroki

W tym instruktażu pokazano tylko niewielką część tego, co można zrobić z rozszerzeniem programu Visual Studio. Oto krótka lista innych (dość łatwych) czynności, które można wykonać za pomocą rozszerzeń programu Visual Studio:

1. Możesz zrobić wiele innych rzeczy za pomocą prostego polecenia menu:

   1. Dodawanie własnej [ikony: Dodawanie ikon do poleceń menu](../extensibility/adding-icons-to-menu-commands.md)

   2. Zmienianie tekstu polecenia menu: [Zmienianie tekstu polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Dodawanie skrótu menu do polecenia: [Powiązanie skrótów klawiaturowych z elementami menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Dodawanie różnych rodzajów poleceń, menu i pasków narzędzi: [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)

3. Dodawanie okien narzędzi i rozszerzanie wbudowanych okien narzędzi programu Visual Studio: [Rozszerzanie i dostosowywanie okien narzędzi](../extensibility/extending-and-customizing-tool-windows.md)

4. Dodawanie funkcji IntelliSense, sugestie kodu i inne funkcje do istniejących edytorów kodu: [Rozszerzenie edytora i usług językowych](../extensibility/extending-the-editor-and-language-services.md)

5. Dodawanie opcji i stron właściwości oraz ustawień użytkownika do rozszerzenia: [Rozszerzanie właściwości i okno Właściwości](../extensibility/extending-properties-and-the-property-window.md) oraz [rozszerzanie ustawień i opcji użytkownika](../extensibility/extending-user-settings-and-options.md)

   Inne rodzaje rozszerzeń wymagają trochę więcej pracy, na przykład tworzenie nowego typu projektu ([Rozszerzanie projektów),](../extensibility/extending-projects.md)tworzenie nowego typu[edytora (Tworzenie niestandardowych edytorów i projektantów)](../extensibility/creating-custom-editors-and-designers.md)lub implementowanie rozszerzenia w izolowanej powłoce: [Izolowana powłoka programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
