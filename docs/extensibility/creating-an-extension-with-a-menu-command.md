---
title: Tworzenie rozszerzenia za pomocą polecenia Menu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bd25b7ed02cb8d45ae693eacdb397a250d2456e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847827"
---
# <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu
W tym instruktażu przedstawiono sposób tworzenia rozszerzenia za pomocą polecenia menu, który uruchamia program Notatnik.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-menu-command"></a>Utwórz polecenie menu  
  
1.  Utwórz projekt VSIX, o nazwie **FirstMenuCommand**. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C#** > **rozszerzalności**.  
  
2.  Po otwarciu projektu, Dodaj polecenie niestandardowe szablon elementu o nazwie **FirstCommand**. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C#** > **rozszerzalności** i wybierz **polecenia niestandardowego**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby *FirstCommand.cs*.  
  
3.  Skompiluj projekt, a następnie rozpocząć debugowanie.  
  
     Pojawi się doświadczalnym wystąpieniu programu Visual Studio. Aby uzyskać więcej informacji na temat wystąpienia eksperymentalnego zobacz [wystąpienie doświadczalne](../extensibility/the-experimental-instance.md).  
  
4.  W doświadczalnym wystąpieniu Otwórz **narzędzia** > **rozszerzenia i aktualizacje** okna. Powinien zostać wyświetlony **FirstMenuCommand** rozszerzenia w tym miejscu. (Jeśli otworzysz **rozszerzenia i aktualizacje** wystąpienia pracy programu Visual Studio, nie będziesz widzieć **FirstMenuCommand**).  
  
     Teraz przejdź do **narzędzia** menu w eksperymentalnym wystąpieniu. Powinien zostać wyświetlony **wywołania FirstCommand** polecenia. W tym momencie ją po prostu wywołuje okno komunikatu, informujący, że **FirstCommandPackage wewnątrz FirstMenuCommand.FirstCommand.MenuItemCallback()**. Zobaczymy, jak faktycznie Uruchom Notatnik z tego polecenia, w następnej sekcji.  
  
## <a name="change-the-menu-command-handler"></a>Zmień program obsługi poleceń menu  
 Teraz zaktualizujmy program obsługi poleceń, aby uruchomić program Notatnik.  
  
1.  Zatrzymaj debugowanie i wrócić do pracy Twojego wystąpienia programu Visual Studio. Otwórz *FirstCommand.cs* pliku i dodaj następującą instrukcję using:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Znajdź Konstruktor prywatny FirstCommand. Jest to, gdy polecenie jest podłączany do usługi polecenia, a określono program obsługi poleceń. Zmień nazwę program obsługi poleceń StartNotepad, w następujący sposób:  
  
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
  
3.  Usuń `MenuItemCallback` metody i Dodaj `StartNotepad` metodę, która będzie po prostu uruchom program Notatnik:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Teraz wypróbuj działanie rozwiązania. Po rozpoczęciu debugowania projektu i kliknięciu **narzędzia** > **wywołania FirstCommand**, powinny zostać wyświetlone wystąpienia programu Notatnik, pojawiają się.  
  
     Można użyć wystąpienia <xref:System.Diagnostics.Process> klasy do uruchamiania dowolnych plików wykonywalnych, nie tylko Notatnik. Wypróbuj ją za pomocą `calc.exe`, na przykład.  
  
## <a name="clean-up-the-experimental-environment"></a>Wyczyść środowisko eksperymentalne  
 Jeśli tworzysz wiele rozszerzeń lub tylko zapoznać się z wynikami z różnymi wersjami kod rozszerzenia, środowiska eksperymentalne mogą przestać działać sposób, w jaki powinien. W takim przypadku należy uruchomić skrypt resetowania. Jest on nazywany **Zresetuj Visual Studio 2015 wystąpienie eksperymentalne programu**, a jego jest dostarczany jako część programu Visual Studio SDK. Ten skrypt umożliwia usunięcie wszystkich odwołań do rozszerzeń z eksperymentalnego środowiska, aby można było zacząć od podstaw.  
  
 Aby przejść do tego skryptu w jeden z dwóch sposobów:  
  
1.  Na pulpicie, Znajdź **Zresetuj Visual Studio 2015 wystąpienie eksperymentalne programu**.  
  
2.  W wierszu polecenia Uruchom następujące polecenie:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploy-your-extension"></a>Wdrażanie rozszerzenia  
 Teraz, gdy masz uruchomiony sposób, który ma rozszerzenie narzędzia, nadszedł czas na zastanów się, udostępniając je znajomymi. Może to być proste, jak długo mają zainstalowanego programu Visual Studio 2015. Wszystkie trzeba je wysłać *.vsix* utworzony plik. (Należy ją skompilować w trybie wydania.)  
  
 Możesz znaleźć *.vsix* pliku dla tego rozszerzenia w *FirstMenuCommand* katalogu bin. W szczególności przy założeniu, że utworzone konfiguracji wydania, będzie:  
  
 *\<katalog kodu > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix*  
  
 Aby zainstalować rozszerzenie, przyjaciela musi Zamknij wszystkie otwarte wystąpienia programu Visual Studio, a następnie kliknij dwukrotnie *.vsix* pliku, co umożliwia wyświetlenie **Instalator VSIX**. Pliki są kopiowane do *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions* katalogu.  
  
 Jeśli przyjaciela powoduje próbę instalacji programu Visual Studio, znajdziesz on rozszerzenie FirstMenuCommand w **narzędzia** > **rozszerzenia i aktualizacje**. Użytkownik może przejść do **rozszerzenia i aktualizacje** Aby odinstalować lub wyłączyć rozszerzenie, zbyt.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym instruktażu jest wyświetlane tylko niewielką część co można zrobić za pomocą rozszerzenia programu Visual Studio. Poniżej przedstawiono krótką listę innymi (względnie proste), które można wykonać przy użyciu rozszerzeń programu Visual Studio:  
  
1. Możesz wykonać wiele innych rzeczy przy użyciu prostego polecenia:  
  
   1.  Dodaj własną ikonę: [Dodawanie ikon do poleceń menu](../extensibility/adding-icons-to-menu-commands.md)  
  
   2.  Zmiana tekstu polecenia menu: [Zmiana tekstu polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3.  Dodaj skrót menu do polecenia: [Powiąż skrótów klawiaturowych z elementami menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. Dodaj różne rodzaje polecenia, menu i paski narzędzi: [Rozszerzenie menu i poleceń](../extensibility/extending-menus-and-commands.md)  
  
3. Dodawanie okna narzędzi i rozszerzyć wbudowane okna narzędzi programu Visual Studio: [Rozszerzanie i dostosowywanie okien narzędzi](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. Dodaj funkcję IntelliSense, sugestie dotyczące kodu i inne funkcje do istniejących edytory kodu: [Rozszerzanie usług edytora i języka](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Dodaj strony Opcje i właściwości i ustawienia użytkownika do rozszerzenia: [Rozszerzanie właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md) i [rozszerzenie ustawienia użytkownika i Ooptions](../extensibility/extending-user-settings-and-options.md)  
  
   Innych rodzajów rozszerzenia wymaga trochę więcej pracy, takich jak tworzenie nowego typu projektu ([rozszerzanie projektów](../extensibility/extending-projects.md)), tworzenia nowego typu edytora ([Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)), lub implementacji usługi rozszerzenie w izolowanej powłoki: [Programu Visual Studio isolated shell](/visualstudio/extensibility/shell/visual-studio-isolated-shell)