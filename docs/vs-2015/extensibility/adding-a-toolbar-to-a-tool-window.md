---
title: Dodawanie paska narzędzi do okna narzędzi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 49
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c5df1ce1721c63b5c5cfc3c5b94929da088660f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184881"
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Dodawanie paska narzędzi do okna narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak dodać pasek narzędzi do okna narzędzi.  
  
 Pasek narzędzi to poziomy lub pionowy pasek, który zawiera przyciski powiązane z poleceniami. Długość paska narzędzi w oknie narzędzi jest zawsze taka sama jak szerokość lub wysokość okna narzędzi, w zależności od tego, gdzie jest zadokowany pasek narzędzi.  
  
 W przeciwieństwie do pasków narzędzi w IDE, pasek narzędzi w oknie narzędzi musi być zadokowany i nie można go przenieść ani dostosować. Jeśli pakietu VSPackage jest zapisywana w kodzie umanaged, pasek narzędzi można zadokować na dowolnej krawędzi.  
  
 Aby uzyskać więcej informacji na temat dodawania paska narzędzi, zobacz [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Tworzenie paska narzędzi dla okna narzędzi  
  
1. Utwórz projekt VSIX o nazwie `TWToolbar` z poleceniem menu o nazwie **TWTestCommand** i oknem narzędzia o nazwie **TestToolWindow**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md) i [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md). Musisz dodać szablon elementu polecenia przed dodaniem szablonu okna narzędzi.  
  
2. W TWTestCommandPackage. vsct poszukaj sekcji symboli. W węźle GuidSymbol o nazwie guidTWTestCommandPackageCmdSet Zadeklaruj pasek narzędzi i grupę pasków narzędzi w następujący sposób.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3. W górnej części `Commands` sekcji Utwórz `Menus` sekcję. Dodaj `Menu` element, aby zdefiniować pasek narzędzi.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Paski narzędzi nie mogą być zagnieżdżone jako podmenu. W związku z tym nie trzeba przypisywać elementu nadrzędnego. Ponadto nie ma konieczności ustawiania priorytetu, ponieważ użytkownik może przenosić paski narzędzi. Zwykle początkowe umieszczanie paska narzędzi jest zdefiniowane programowo, ale kolejne zmiany wprowadzane przez użytkownika są utrwalane.  
  
4. W sekcji grupy Zdefiniuj grupę zawierającą polecenia dla paska narzędzi.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5. W sekcji przyciski Zmień element nadrzędny istniejącego elementu Button na grupę paska narzędzi, aby wyświetlić pasek narzędzi.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Domyślnie, jeśli pasek narzędzi nie ma poleceń, nie jest wyświetlany.  
  
     Ponieważ nowy pasek narzędzi nie jest automatycznie dodawany do okna narzędzi, należy dodać go jawnie. Ta czynność została omówiona w następnej sekcji.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Dodawanie paska narzędzi do okna narzędzi  
  
1. W TWTestCommandPackageGuids.cs Dodaj następujące wiersze.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2. W TestToolWindow.cs Dodaj następującą instrukcję using.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3. W konstruktorze TestToolWindow Dodaj następujący wiersz.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>Testowanie paska narzędzi w oknie narzędzi  
  
1. Skompiluj projekt i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalne programu Visual Studio.  
  
2. W menu **Widok/inne okna** kliknij pozycję **Testuj ToolWindow** , aby wyświetlić okno narzędzia.  
  
     Powinien pojawić się pasek narzędzi (wygląda jak ikona domyślna) w lewym górnym rogu okna narzędzi, po prostu pod tytułem.  
  
3. Na pasku narzędzi kliknij ikonę, aby wyświetlić komunikat **TWTestCommandPackage wewnątrz TWToolbar. TWTestCommand. MenuItemCallback ()**.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md)
