---
title: Dodawanie ostatnio używanej listy do podmenu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf389c0da7ec0aafb6e47dae8f09ffdc3b1d1e4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740304"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Dodawanie ostatnio używanej listy do podmenu
Ten instruktaż opiera się na demonstracjach w [menu Dodaj podmenu i](../extensibility/adding-a-submenu-to-a-menu.md)pokazuje, jak dodać listę dynamiczną do podmenu. Lista dynamiczna stanowi podstawę do utworzenia listy ostatnio używane (MRU).

Dynamiczna lista menu zaczyna się od symbolu zastępczego w menu. Za każdym razem, gdy menu jest wyświetlane, visual studio zintegrowane środowisko programistyczne (IDE) pyta VSPackage dla wszystkich poleceń, które powinny być wyświetlane w symbolu zastępczego. Lista dynamiczna może pojawić się w dowolnym miejscu w menu. Jednak listy dynamiczne są zazwyczaj przechowywane i wyświetlane samodzielnie na podmenu lub na dole menu. Za pomocą tych wzorców projektowych, można włączyć dynamiczną listę poleceń, aby rozwinąć i umowy bez wpływu na położenie innych poleceń w menu. W tym instruktażu dynamiczna lista MRU jest wyświetlana u dołu istniejącego podmenu, oddzielona od reszty podmenu wierszem.

Technicznie lista dynamiczna może być również zastosowana do paska narzędzi. Jednak możemy zniechęcić tego użycia, ponieważ pasek narzędzi powinien pozostać niezmieniony, chyba że użytkownik podejmie określone kroki, aby go zmienić.

W tym instruktażu utworzy się listę MRU czterech elementów, które zmieniają ich kolejność za każdym razem, gdy jeden z nich jest zaznaczony (wybrany element przenosi się na górę listy).

Aby uzyskać więcej informacji o menu i plikach *vsct,* zobacz [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Wymagania wstępne
Aby wykonać ten przewodnik, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Tworzenie rozszerzenia

- Postępuj zgodnie z [procedurami w dodawanie podmenu do menu,](../extensibility/adding-a-submenu-to-a-menu.md) aby utworzyć podmenu, który jest modyfikowany w poniższych procedurach.

  Procedury w tym instruktażu zakładają, że `TopLevelMenu`nazwa VSPackage jest , która jest nazwą, która jest używana w [Dodaj menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Tworzenie polecenia listy elementów dynamicznych

1. Otwórz *testCommandPackage.vsct*.

2. W `Symbols` sekcji w `GuidSymbol` węźle o nazwie guidTestCommandPackageCmdSet `MRUListGroup` dodaj `cmdidMRUList` symbol grupy i polecenia w następujący sposób.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. W `Groups` sekcji dodaj zadeklarowane grupy po istniejących wpisach grupy.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. W `Buttons` sekcji dodaj węzeł do reprezentowania nowo zadeklarowanego polecenia, po istniejących wpisach przycisku.

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

    Flaga `DynamicItemStart` umożliwia dynamiczne generowanie polecenia.

5. Skompiluj projekt i rozpocznij debugowanie, aby przetestować wyświetlanie nowego polecenia.

    W menu **TestMenu** kliknij nowe podmenu **Podmenu**, aby wyświetlić nowe polecenie **MRU Placeholder**. Po zaimplementowaniu dynamicznej listy poleceń MRU w następnej procedurze ta etykieta polecenia zostanie zastąpiona tą listą za każdym razem, gdy podmenu jest otwierane.

## <a name="filling-the-mru-list"></a>Wypełnianie listy MRU

1. W *TestCommandPackageGuids.cs*, dodaj następujące wiersze po istniejących identyfikatorach `TestCommandPackageGuids` poleceń w definicji klasy.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. W *TestCommand.cs* dodać następujące instrukcje.

    ```csharp
    using System.Collections;
    ```

3. Dodaj następujący kod w Konstruktorze TestCommand po ostatnim wywołaniu AddCommand. Zostanie `InitMRUMenu` ono zdefiniowane później

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Dodaj następujący kod w TestCommand klasy. Ten kod inicjuje listę ciągów, które reprezentują elementy, które mają być wyświetlane na liście MRU.

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

5. Po `InitializeMRUList` metodzie dodaj `InitMRUMenu` metodę. Spowoduje to zainicjowanie poleceń menu listy MRU.

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

    Należy utworzyć obiekt polecenia menu dla każdego możliwego elementu na liście MRU. IDE wywołuje `OnMRUQueryStatus` metodę dla każdego elementu na liście MRU, dopóki nie ma więcej elementów. W kodzie zarządzanym jedynym sposobem, aby IDE wiedzieć, że nie ma więcej elementów jest najpierw utworzyć wszystkie możliwe elementy. Jeśli chcesz, możesz oznaczyć dodatkowe elementy jako `mc.Visible = false;` niewidoczne na początku za pomocą polecenia menu jest tworzony. Elementy te mogą być następnie widoczne `mc.Visible = true;` później `OnMRUQueryStatus` przy użyciu metody.

6. Po `InitMRUMenu` zakończeniu metody dodaj `OnMRUQueryStatus` następującą metodę. Jest to program obsługi, który ustawia tekst dla każdego elementu MRU.

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

7. Po `OnMRUQueryStatus` zakończeniu metody dodaj `OnMRUExec` następującą metodę. Jest to program obsługi do wybierania elementu MRU. Ta metoda przenosi zaznaczony element na górę listy, a następnie wyświetla zaznaczony element w oknie komunikatu.

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

## <a name="testing-the-mru-list"></a>Testowanie listy MRU

1. Skompiluj projekt i rozpocznij debugowanie.

2. W menu **TestMenu** kliknij polecenie **Wywołaj polecenie TestCommand**. W ten sposób zostanie wyświetlone okno komunikatu wskazujące, że polecenie zostało wybrane.

    > [!NOTE]
    > Ten krok jest wymagany do wymuszenie vspackage załadować i poprawnie wyświetlić listę MRU. Jeśli pominiesz ten krok, lista MRU nie zostanie wyświetlona.

3. W menu **Menu testowe** kliknij polecenie **Pod menu**. Lista czterech elementów jest wyświetlana na końcu podmenu, poniżej separatora. Po **kliknięciu pozycji 3**powinno pojawić się okno komunikatu i wyświetlenie tekstu **Zaznaczony element 3**. (Jeśli lista czterech elementów nie jest wyświetlana, upewnij się, że postępowałeś zgodnie z instrukcjami we wcześniejszym kroku).

4. Ponownie otwórz podmenu. Należy zauważyć, że **element 3** znajduje się teraz na górze listy, a pozostałe elementy zostały przesunięte w dół o jedną pozycję. Kliknij ponownie **pozycję Element 3** i zwróć uwagę, że w oknie komunikatu nadal **jest wyświetlany zaznaczony element 3**, co oznacza, że tekst został poprawnie przeniesiony do nowej pozycji wraz z etykietą polecenia.

## <a name="see-also"></a>Zobacz też
- [Dynamiczne dodawanie elementów menu](../extensibility/dynamically-adding-menu-items.md)
