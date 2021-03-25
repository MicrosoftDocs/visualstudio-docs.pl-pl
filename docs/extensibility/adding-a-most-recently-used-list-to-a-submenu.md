---
title: Dodawanie ostatnio używanej listy do podmenu | Microsoft Docs
description: Dowiedz się, jak dodać listę dynamiczną zawierającą ostatnio używane polecenia menu do podmenu w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb238afb0f583f1b913fbd87f4f50e43679ebd7d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060019"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Dodaj ostatnio używaną listę do podmenu
Ten przewodnik jest oparty na pokazach w oknie [Dodawanie podmenu do menu](../extensibility/adding-a-submenu-to-a-menu.md)i pokazuje, jak dodać listę dynamiczną do podmenu. Lista dynamiczna stanowi podstawę tworzenia ostatnio używanej listy (MRU).

Dynamiczna lista jest rozpoczynana z symbolem zastępczym w menu. Za każdym razem, gdy zostanie wyświetlone menu, zintegrowane środowisko programistyczne programu Visual Studio (IDE) pyta pakietu VSPackage o wszystkie polecenia, które powinny być wyświetlane w symbolu zastępczym. Dynamiczna lista może wystąpić w dowolnym miejscu w menu. Jednak listy dynamiczne są zwykle przechowywane i wyświetlane samodzielnie w podmenu lub w dolnej części menu. Korzystając z tych wzorców projektowych, należy włączyć dynamiczną listę poleceń do rozwinięcia i kontraktu bez wpływu na pozycję innych poleceń w menu. W tym instruktażu dynamiczna lista MRU jest wyświetlana u dołu istniejącego podmenu, oddzielona od reszty podmenu przez wiersz.

Technicznie można również zastosować listę dynamiczną do paska narzędzi. Niestety, odradzamy takie użycie, ponieważ pasek narzędzi powinien pozostać niezmieniony, chyba że użytkownik wykona konkretne czynności, aby go zmienić.

W tym instruktażu zostanie utworzona lista ostatnio używanych czterech elementów, które zmieniają ich kolejność za każdym razem, gdy zostanie wybrana jedna z nich (zaznaczony element zostanie przesunięty w górę listy).

Aby uzyskać więcej informacji na temat menu i plików *. vsct* , zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Wymagania wstępne
Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Utwórz rozszerzenie

- Postępuj zgodnie z procedurami w temacie [Dodawanie podmenu do menu](../extensibility/adding-a-submenu-to-a-menu.md) , aby utworzyć podmenu, które zostało zmodyfikowane w poniższych procedurach.

  W procedurach w tym instruktażu przyjęto założenie, że nazwa pakietu VSPackage jest `TestCommand` nazwą, która jest używana w [Dodaj menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Utwórz polecenie dynamicznego listy elementów

1. Otwórz *TestCommandPackage. vsct*.

2. W `Symbols` sekcji w `GuidSymbol` węźle o nazwie guidTestCommandPackageCmdSet Dodaj symbol dla `MRUListGroup` grupy i `cmdidMRUList` polecenia w następujący sposób.

    ```xml
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. W `Groups` sekcji Dodaj zadeklarowaną grupę po istniejących wpisach grupy.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

4. W `Buttons` sekcji Dodaj węzeł reprezentujący nowo zadeklarowane polecenie po istniejących wpisach przycisku.

    ```xml
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

    `DynamicItemStart`Flaga umożliwia dynamiczne generowanie polecenia.

5. Skompiluj projekt i Rozpocznij debugowanie w celu przetestowania wyświetlania nowego polecenia.

    W menu **TestMenu** kliknij nowe podmenu, **podmenu**, aby wyświetlić nowe polecenie i **symbol zastępczy MRU**. Po zaimplementowaniu dynamicznej listy MRU poleceń w następnej procedurze Ta etykieta polecenia zostanie zastąpiona tą listą za każdym razem, gdy podmenu zostanie otwarte.

## <a name="filling-the-mru-list"></a>Wypełnianie listy MRU

1. W *TestCommandPackageGuids. cs* Dodaj następujące wiersze po istniejących identyfikatorach poleceń w `TestCommandPackageGuids` definicji klasy.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. W *TestCommand. cs* Dodaj następującą instrukcję using.

    ```csharp
    using System.Collections;
    ```

3. Dodaj następujący kod w konstruktorze TestCommand po ostatnim wywołaniu AddCommand. `InitMRUMenu`Zostanie zdefiniowany później

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Dodaj następujący kod do klasy TestCommand. Ten kod inicjuje listę ciągów reprezentujących elementy, które mają być wyświetlane na liście MRU.

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

5. Po `InitializeMRUList` metodzie Dodaj `InitMRUMenu` metodę. Spowoduje to zainicjowanie poleceń menu listy MRU.

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

    Należy utworzyć obiekt polecenia menu dla każdego możliwego elementu na liście MRU. IDE wywołuje `OnMRUQueryStatus` metodę dla każdego elementu na liście MRU do momentu, gdy nie będzie więcej elementów. W kodzie zarządzanym jedynym sposobem na środowisko IDE jest wiadomo, że nie ma więcej elementów, aby najpierw utworzyć wszystkie możliwe elementy. Jeśli chcesz, możesz oznaczyć dodatkowe elementy jako niewidoczne jako pierwsze przy użyciu `mc.Visible = false;` po utworzeniu polecenia menu. Elementy te można następnie wyświetlić później za pomocą `mc.Visible = true;` `OnMRUQueryStatus` metody.

6. Po `InitMRUMenu` metodzie Dodaj następującą `OnMRUQueryStatus` metodę. Jest to procedura obsługi, która ustawia tekst dla każdego elementu MRU.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. Po `OnMRUQueryStatus` metodzie Dodaj następującą `OnMRUExec` metodę. Jest to procedura obsługi wybierania elementu MRU. Ta metoda przenosi wybrany element na początek listy, a następnie wyświetla wybrany element w oknie komunikatu.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
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

1. Skompiluj projekt i Rozpocznij debugowanie.

2. W menu **TestMenu** kliknij pozycję **Wywołaj TestCommand**. Spowoduje to wyświetlenie okna komunikatu, które wskazuje, że polecenie zostało wybrane.

    > [!NOTE]
    > Ten krok jest wymagany, aby wymusić załadowanie i prawidłowe wyświetlanie listy MRU przez pakietu VSPackage. W przypadku pominięcia tego kroku lista MRU nie zostanie wyświetlona.

3. W menu **test** menu kliknij polecenie **sub menu**. Na końcu podmenu zostanie wyświetlona lista czterech elementów poniżej separatora. Gdy klikniesz **element 3**, pojawi się okno komunikatu i zostanie wyświetlony tekst, **wybrany element 3**. (Jeśli lista czterech elementów nie jest wyświetlana, upewnij się, że wykonano instrukcje w poprzednim kroku).

4. Ponownie Otwórz podmenu. Zauważ, że **element 3** znajduje się teraz w górnej części listy, a pozostałe elementy zostały wypchnięte do jednego stanowiska. Kliknij ponownie **element Item 3** i zwróć uwagę, że w oknie komunikatu nadal jest wyświetlany **wybrany element 3**, który wskazuje, że tekst został prawidłowo przeniesiony do nowej pozycji i z etykietą polecenia.

## <a name="see-also"></a>Zobacz też
- [Dynamiczne dodawanie elementów menu](../extensibility/dynamically-adding-menu-items.md)
