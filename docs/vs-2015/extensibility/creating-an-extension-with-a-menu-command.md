---
title: Tworzenie rozszerzenia za pomocą polecenia menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3bbf6b3b1ed2565d5e58806bd0935f713ba5bfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62572890"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak utworzyć rozszerzenie za pomocą polecenia menu, które uruchamia Notatnik.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Tworzenie polecenia menu  
  
1. Utwórz projekt VSIX o nazwie **FirstMenuCommand**. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** w obszarze **Visual C#/rozszerzalność**.  
  
2. Po otwarciu projektu Dodaj niestandardowy szablon elementu polecenia o nazwie **FirstCommand**. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj/nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do pozycji **Visual C#/rozszerzalność** i wybierz **polecenie niestandardowe**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na **FirstCommand.cs**.  
  
3. Skompiluj projekt i Rozpocznij debugowanie.  
  
     Pojawia się eksperymentalne wystąpienie programu Visual Studio. Aby uzyskać więcej informacji o wystąpieniu eksperymentalnym, zobacz [wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).  
  
4. W eksperymentalnym wystąpieniu Otwórz okno  **Narzędzia/rozszerzenia i aktualizacje** . Tutaj powinno być widoczne rozszerzenie **FirstMenuCommand** . (Jeśli otworzysz **rozszerzenia i aktualizacje** w działającym wystąpieniu programu Visual Studio, nie zobaczysz **FirstMenuCommand**).  
  
     Teraz przejdź do menu **Narzędzia** w wystąpieniu eksperymentalnym. Powinien pojawić się polecenie **Invoke FirstCommand** . W tym momencie po prostu zostanie wyświetlone okno komunikatu z informacją o "FirstCommandPackage wewnątrz FirstMenuCommand. FirstCommand. MenuItemCallback ()". Zobaczymy, jak faktycznie uruchomić Notatnik z tego polecenia w następnej sekcji.  
  
## <a name="changing-the-menu-command-handler"></a>Zmiana programu obsługi poleceń menu  
 Teraz zaktualizujmy procedurę obsługi poleceń, aby uruchomić Notatnik.  
  
1. Zatrzymaj debugowanie i wróć do działającego wystąpienia programu Visual Studio. Otwórz plik FirstCommand.cs i Dodaj następującą instrukcję using:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2. Znajdź prywatnego konstruktora FirstCommand. Jest to miejsce, w którym polecenie jest podłączane do usługi poleceń i został określony program obsługi poleceń. Zmień nazwę programu obsługi poleceń na StartNotepad w następujący sposób:  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3. Usuń metodę MenuItemCallback i Dodaj metodę StartNotepad, która spowoduje jedynie uruchomienie programu Notepad:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4. Wypróbuj teraz. Po rozpoczęciu debugowania projektu i kliknięciu przycisku **Narzędzia/Wywołaj FirstCommand**należy zobaczyć wystąpienie Notatnika.  
  
     Możesz użyć wystąpienia <xref:System.Diagnostics.Process> klasy do uruchamiania dowolnego pliku wykonywalnego, a nie tylko Notatnika. Wypróbuj calc.exe, na przykład.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Czyszczenie eksperymentalnego środowiska  
 Jeśli tworzysz wiele rozszerzeń lub po prostu Eksplorowanie wyników przy użyciu różnych wersji kodu rozszerzenia, środowisko eksperymentalne może przestać działać w sposób. W takim przypadku należy uruchomić skrypt Reset. Jest on wywoływany przez **zresetowanie wystąpienia eksperymentalnego programu Visual studio 2015**i jest dostarczane jako część zestawu Visual Studio SDK. Ten skrypt usuwa wszystkie odwołania do rozszerzeń ze środowiska eksperymentalnego, więc możesz zacząć od podstaw.  
  
 Możesz uzyskać dostęp do tego skryptu na jeden z dwóch sposobów:  
  
1. Na pulpicie Znajdź pozycję **Zresetuj wystąpienie eksperymentalne programu Visual Studio 2015**.  
  
2. W wierszu polecenia Uruchom następujące polecenie:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Wdrażanie rozszerzenia  
 Teraz, gdy masz już swoje rozszerzenie narzędzia, Możesz pomyśleć o udostępnianiu go przyjaciołom i współpracownikom. To bardzo proste, tak długo, jak ma zainstalowany program Visual Studio 2015. Wszystko, co musisz zrobić, wysyła do nich utworzony plik. VSIX. (Pamiętaj, aby skompilować go w trybie wydania).  
  
 Plik VSIX dla tego rozszerzenia można znaleźć w katalogu bin FirstMenuCommand. W celu założenia, że została skompilowana konfiguracja wydania, będzie ona dostępna w:  
  
 **\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand. vsix**  
  
 Aby zainstalować rozszerzenie, znajomy musi zamknąć wszystkie otwarte wystąpienia programu Visual Studio, a następnie kliknąć dwukrotnie plik. vsix, który powoduje uruchomienie **Instalatora VSIX**. Pliki są kopiowane do katalogu **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** .  
  
 Gdy znajomy ponownie utworzy program Visual Studio, znajdzie rozszerzenie FirstMenuCommand w oknie **Narzędzia/rozszerzenia i aktualizacje**. Można również przejść do **rozszerzeń i aktualizacji** , aby odinstalować lub wyłączyć rozszerzenie.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym instruktażu przedstawiono tylko niewielką część tego, co można zrobić za pomocą rozszerzenia programu Visual Studio. Poniżej przedstawiono krótką listę innych (w sposób łatwy) czynności, które można wykonać za pomocą rozszerzeń programu Visual Studio:  
  
1. Za pomocą prostego polecenia menu można wykonać wiele innych czynności:  
  
   1. Dodaj własną ikonę: [Dodawanie ikon do poleceń menu](../extensibility/adding-icons-to-menu-commands.md)  
  
   2. Zmień tekst polecenia menu: [Zmiana tekstu polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3. Dodawanie skrótu menu do polecenia: [Powiązywanie skrótów klawiaturowych z elementami menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. Dodaj różne rodzaje poleceń, menu i paski narzędzi: [rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)  
  
3. Dodawanie okien narzędzi i rozszerzanie wbudowanych okien narzędzi programu Visual Studio: [rozszerzanie i dostosowywanie okien narzędzi](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. Dodawanie technologii IntelliSense, sugestii dotyczących kodu i innych funkcji do istniejących edytorów kodu: [rozszerzanie edytora i usług językowych](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Dodawanie opcji i stron właściwości oraz ustawień użytkownika do rozszerzenia: [Rozszerzanie właściwości i okna właściwości](../extensibility/extending-properties-and-the-property-window.md) oraz [rozszerzanie ustawień i opcji użytkownika](../extensibility/extending-user-settings-and-options.md)  
  
   Inne rodzaje rozszerzeń wymagają nieco więcej pracy, takich jak tworzenie nowego typu projektu ([rozszerzanie projektów](../extensibility/extending-projects.md)), tworzenie nowego typu edytora ([Tworzenie edytorów niestandardowych i projektantów](../extensibility/creating-custom-editors-and-designers.md)) lub Wdrażanie rozszerzenia w izolowanej Shell: [powłoka izolowana programu Visual Studio](../extensibility/visual-studio-isolated-shell.md)
