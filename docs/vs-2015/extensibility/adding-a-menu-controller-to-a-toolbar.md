---
title: Dodawanie kontrolera Menu do paska narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c63f6c98153c9f7a9fab171b3caddd57df717cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184910"
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Dodawanie kontrolera menu do paska narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku opiera się na [Dodawanie paska narzędzi do okna narzędzi](../extensibility/adding-a-toolbar-to-a-tool-window.md) instruktażu przedstawiono sposób dodawania kontrolera menu do paska narzędzi okna narzędzia. Kroki opisane w tym miejscu można zastosować także do narzędzi, który jest tworzony w [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md) wskazówki.  
  
 Kontroler menu jest formantem podziału. Kontroler menu po lewej stronie pokazuje ostatnio używane polecenia, a następnie uruchomić, klikając go. Prawa strona kontroler menu jest strzałka, po kliknięciu otwiera listę dodatkowych poleceń. Kiedy kliknąć polecenie na liście, a polecenie działa, i zastępuje polecenia po lewej stronie kontroler menu. W ten sposób kontroler menu działa jak przycisk polecenia, które zawsze wyświetli ostatnio używane polecenia, z listy.  
  
 Kontrolery menu mogą być wyświetlane w menu, ale są najczęściej używane na paskach narzędzi.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Tworzenie kontrolera Menu  
  
#### <a name="to-create-a-menu-controller"></a>Aby utworzyć kontroler menu  
  
1. Wykonaj procedury opisane w temacie [Dodawanie paska narzędzi do okna narzędzi](../extensibility/adding-a-toolbar-to-a-tool-window.md) się utworzenie okna narzędzia, które ma pasek narzędzi.  
  
2. W TWTestCommandPackage.vsct przejdź do sekcji symboli. W GuidSymbol, element o nazwie **guidTWTestCommandPackageCmdSet**, Zadeklaruj kontroler menu, grupy kontrolera menu i trzech elementów menu.  
  
   ```xml  
   <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
   ```  
  
3. W sekcji menu po ostatni wpis menu zdefiniować kontroler menu jako menu.  
  
   ```xml  
   <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <CommandFlag>TextChanges</CommandFlag>  
       <CommandFlag>TextIsAnchorCommand</CommandFlag>  
       <Strings>  
           <ButtonText>Test Menu Controller</ButtonText>  
           <CommandName>Test Menu Controller</CommandName>  
       </Strings>  
   </Menu>  
   ```  
  
    `TextChanges` i `TextIsAnchorCommand` flagi należy dołączyć umożliwiające kontroler menu odzwierciedlić ostatnie wybranego polecenia.  
  
4. W grupach sekcji po ostatni wpis grupy dodać grupę kontroler menu.  
  
   ```xml  
   <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
   </Group>  
   ```  
  
    Ustawiając kontroler menu jako element nadrzędny, wszelkie polecenia umieszczone w tej grupie zostaną wyświetlone w kontroler menu. `priority` Atrybut zostanie pominięty, która ustawia wartości domyślnej 0, ponieważ będzie on tylko grupy na kontrolerze menu.  
  
5. W sekcji przyciski po ostatni wpis przycisku Dodaj element przycisku dla każdego z elementów menu.  
  
   ```xml  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPic1" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 1</ButtonText>  
           <CommandName>MC Item 1</CommandName>  
       </Strings>  
   </Button>  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPic2" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 2</ButtonText>  
           <CommandName>MC Item 2</CommandName>  
       </Strings>  
   </Button>  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPicSearch" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 3</ButtonText>  
           <CommandName>MC Item 3</CommandName>  
       </Strings>  
   </Button>  
   ```  
  
6. W tym momencie możesz obejrzeć kontroler menu. Skompiluj projekt, a następnie rozpocząć debugowanie. Powinien zostać wyświetlony wystąpienie eksperymentalne.  
  
   1. Na **widok / inne Windows** menu Otwórz **ToolWindow testu**.  
  
   2. Kontroler menu pojawia się na pasku narzędzi w oknie narzędzia.  
  
   3. Kliknij strzałkę po prawej stronie kontroler menu, aby wyświetlić trzy możliwe polecenia.  
  
      Zwróć uwagę, że po kliknięciu polecenia, tytuł kontroler menu zmienia się do wyświetlania tego polecenia. W następnej sekcji dodamy kod, aby aktywować te polecenia.  
  
## <a name="implementing-the-menu-controller-commands"></a>Implementowanie polecenia Menu kontrolera  
  
1. W TWTestCommandPackageGuids.cs Dodaj identyfikatory poleceń menu trzech elementów po poleceniu istniejących identyfikatorów.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2. W TWTestCommand.cs Dodaj następujący kod w górnej części klasy TWTestCommand.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3. W Konstruktorze TWTestCommand po ostatnim wywołaniu `AddCommand` metody, Dodaj kod, aby kierować zdarzenia dla każdego polecenia za pomocą tej samej procedury obsługi.  
  
    ```csharp  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4. Dodaj program obsługi zdarzeń do klasy TWTestCommand, aby oznaczyć wybrane polecenie jako zaznaczone.  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5. Dodaj program obsługi zdarzeń, która wyświetla komunikat MessageBox, gdy użytkownik wybierze polecenie na kontroler menu:  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## <a name="testing-the-menu-controller"></a>Testowanie kontroler Menu  
  
1. Skompiluj projekt, a następnie rozpocząć debugowanie. Powinien zostać wyświetlony wystąpienie eksperymentalne.  
  
2. Otwórz **ToolWindow testu** na **widok / inne Windows** menu.  
  
     Kontroler menu pojawia się na pasku narzędzi w oknie narzędzia i wyświetla **MC element 1**.  
  
3. Przycisk menu kontrolera strzałkę po lewej stronie.  
  
     Powinien zostać wyświetlony trzy elementy: pierwsze z nich jest zaznaczony i ma pole podświetlenie wokół odpowiednią ikonę. Kliknij przycisk **elementu MC 3**.  
  
     Pojawia się okno dialogowe z komunikatem **wybrane kontroler Menu 3 elementu**. Należy zauważyć, że komunikat odpowiada tekstem na przycisku kontrolera menu. Przycisk menu kontrolera są obecnie wyświetlane **3 elementu MC**.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie paska narzędzi do okna narzędzi](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md)
