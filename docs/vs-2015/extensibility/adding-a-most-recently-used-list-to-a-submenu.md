---
title: Dodawanie listy ostatnio używanych elementów do podmenu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 47
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3aa3058c20fe0d5697b56adb72769f5f6962da1e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086289"
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>Dodawanie listy ostatnio używanych elementów do podmenu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku opiera się na pokazach w [dodawanie podmenu do Menu](../extensibility/adding-a-submenu-to-a-menu.md)i przedstawiono sposób dodawania listy dynamicznych elementów do podmenu. Lista dynamiczna stanowi podstawę do tworzenia list najbardziej ostatnio używanych elementów.  
  
 Menu dynamiczne listy rozpoczyna się od symbolu zastępczego, w menu. Za każdym razem, gdy zostanie wyświetlone menu, Visual Studio zintegrowane środowisko programistyczne (IDE) pyta, czy pakietu VSPackage dla wszystkich poleceń, które mają być pokazywane na symbol zastępczy. Lista dynamiczna może występować w dowolnym miejscu w menu. Jednak listy dynamiczne są zwykle przechowywane i wyświetlane przez siebie, w podmenu lub u dołu menu. Za pomocą te wzorce projektowe, możesz włączyć dynamiczną listę poleceń, aby rozwinąć lub zwinąć bez wywierania wpływu na pozycji innych poleceń w menu. W tym przewodniku listy ostatnio używanych w dynamicznych jest wyświetlane w dolnej części istniejącego podmenu, oddzielone od reszty podmenu wiersza.  
  
 Technicznie rzecz biorąc lista dynamiczna może również będą stosowane do paska narzędzi. Jednak firma Microsoft zniechęcić to użycie, ponieważ pasek narzędzi powinien pozostać bez zmian, chyba że użytkownik ma specjalne kroki, aby ją zmienić.  
  
 Ten przewodnik tworzy listę MRU cztery elementy, które zmienić ich kolejność, za każdym razem, gdy wybrano że jeden z nich (Przenosi wybrany element do góry listy).  
  
 Aby uzyskać więcej informacji na temat menu i plików vsct zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-an-extension"></a>Tworzenie rozszerzenia  
  
- Postępuj zgodnie z procedurami w [dodawanie podmenu do Menu](../extensibility/adding-a-submenu-to-a-menu.md) utworzyć podmenu, który jest modyfikowany w poniższych procedurach.  
  
  W procedurach przedstawionych w tym przewodniku przyjęto założenie, że nazwa pakietu VSPackage jest `TopLevelMenu`, czyli nazwę, która jest używana w [Dodawanie Menu na pasku Menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="creating-a-dynamic-item-list-command"></a>Tworzenie polecenia List elementów dynamicznych  
  
1. Open TestCommandPackage.vsct.  
  
2. W `Symbols` sekcji w `GuidSymbol` węzeł o nazwie guidTestCommandPackageCmdSet, dodać symbol `MRUListGroup` grupy i `cmdidMRUList` polecenia w następujący sposób.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3. W `Groups` sekcji i Dodaj grupy zadeklarowanych po istniejące wpisy grupy.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4. W `Buttons` Dodaj węzeł do reprezentowania polecenie nowo zadeklarowanych po istniejącej pozycji przycisku.  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     `DynamicItemStart` Flagi włączone polecenie być generowany dynamicznie.  
  
5. Skompilować projekt i rozpocząć debugowanie w celu przetestowania nowego polecenia.  
  
     Na **TestMenu** menu, kliknij przycisk nowe podmenu **podmenu**, aby wyświetlić nowe polecenie **symbolu zastępczego MRU**. Po zaimplementowaniu dynamiczne listy ostatnio używanych poleceń w następnej procedurze tej etykiety polecenia zostanie zastąpiona przez tę listę, każdym razem, który jest otwierany w podmenu.  
  
## <a name="filling-the-mru-list"></a>Wypełnianie listy ostatnio używanych  
  
1. W TestCommandPackageGuids.cs, Dodaj następujące wiersze po istniejące identyfikatory poleceń w `TestCommandPackageGuids` definicji klasy.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2. W TestCommand.cs Dodaj następującą instrukcję using.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3. Dodaj następujący kod w Konstruktorze TestCommand po ostatnim wywołaniu funkcji AddCommand. `InitMRUMenu` Zostanie zdefiniowana później  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4. Dodaj następujący kod w klasie TestCommand. Ten kod inicjalizuje listę ciągów reprezentujących elementy, które mają być wyświetlane na liście MRU.  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5. Po `InitializeMRUList` metody, Dodaj `InitMRUMenu` metody. Polecenia menu listy ostatnio używanych elementów jest inicjowana.  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     Należy utworzyć obiekt polecenia menu dla każdego elementu możliwe na listę MRU. Wywołania środowiska IDE `OnMRUQueryStatus` metody dla każdego elementu na liście MRU, dopóki nie ma żadnych elementów. W kodzie zarządzanym jedynym sposobem dla środowiska IDE dowiedzieć się, że nie istnieją żadne więcej elementów jest najpierw utworzyć wszystkie możliwe elementy. Jeśli chcesz, można oznaczyć dodatkowe elementy jako nie są widoczne w najpierw za pomocą `mc.Visible = false;` po utworzeniu polecenia menu. Te elementy mogą następnie być widoczne później za pomocą `mc.Visible = true;` w `OnMRUQueryStatus` metody.  
  
6. Po `InitMRUMenu` metody, Dodaj następujący kod `OnMRUQueryStatus` metody. To jest program obsługi, który ustawia tekst dla każdego elementu listy ostatnio używanych.  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7. Po `OnMRUQueryStatus` metody, Dodaj następujący kod `OnMRUExec` metody. To jest obsługa zaznaczenie elementu MRU. Ta metoda Przenosi wybrany element do góry listy, a następnie wyświetla wybrany element w oknie komunikatu.  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>Testowanie na listę MRU  
  
#### <a name="to-test-the-mru-menu-list"></a>Aby sprawdzić listę ostatnio używanych elementów menu  
  
1. Skompiluj projekt, a następnie rozpocząć debugowanie  
  
2. Na **TestMenu** menu, kliknij przycisk **wywołania TestCommand**. W ten sposób Wyświetla okno komunikatu, który wskazuje, że wybrano polecenie.  
  
    > [!NOTE]
    >  Ten krok jest wymagany, aby wymusić pakietu VSPackage, aby załadować i poprawnego wyświetlania listy ostatnio używanych. Jeśli pominiesz ten krok nie jest wyświetlana na liście MRU.  
  
3. Na **Test Menu** menu, kliknij przycisk **podmenu**. Na koniec podmenu, poniżej separator zostanie wyświetlona lista cztery elementy. Po kliknięciu **3 elementu**, okno komunikatu powinno wyświetlane i wyświetlić tekst "Wybrany element 3". (Jeśli nie zostanie wyświetlona lista cztery elementy, upewnij się, że zostały wykonane z instrukcjami wyświetlanymi w poprzednim kroku.)  
  
4. Ponownie otworzyć podmenu. Należy zauważyć, że **3 elementu** jest teraz w górnej części listy i inne elementy zostały wypchnięte jedną pozycję w dół. Kliknij przycisk **3 elementu** ponownie i zwróć uwagę, w oknie komunikatu Wyświetla nadal "Wybrany element 3", co oznacza, że tekst poprawnie zostały przeniesione do nowej pozycji wraz z etykiety polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Dynamiczne dodawanie elementów menu](../extensibility/dynamically-adding-menu-items.md)
