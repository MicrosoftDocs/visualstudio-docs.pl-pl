---
title: Dodawanie menu skrótów w oknie narzędzi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa8d6f5c47289e66a51653e39d31890f09e8ceb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904188"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Dodawanie menu skrótów w oknie narzędzi
W tym instruktażu jest umieszczane menu skrótów w oknie narzędzi. Menu skrótów to menu, które pojawia się po kliknięciu prawym przyciskiem myszy przycisku, pola tekstowego lub tła okna. Polecenia w menu skrótów zachowują się tak samo jak polecenia w innych menu lub paskach narzędzi. Aby obsłużyć menu skrótów, określ je w pliku *. vsct* i Wyświetl go w odpowiedzi na kliknięcie prawym przyciskiem myszy.

Okno narzędzi składa się z kontrolki użytkownika WPF w niestandardowej klasie okna narzędzi, która dziedziczy z <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> .

W tym instruktażu pokazano, jak utworzyć menu skrótów jako menu programu Visual Studio, deklarując elementy menu w pliku *. vsct* , a następnie używając struktury pakietów zarządzanych do wdrożenia ich w klasie, która definiuje okno narzędzi. Takie podejście ułatwia dostęp do poleceń programu Visual Studio, elementów interfejsu użytkownika i modelu obiektów automatyzacji.

Alternatywnie, jeśli menu skrótów nie będzie miało dostępu do funkcji programu Visual Studio, można użyć <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwości elementu XAML w kontrolce użytkownika. Aby uzyskać więcej informacji, [Zobacz temat](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Wymagania wstępne
Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Tworzenie pakietu menu skrótów okna narzędzi

1. Utwórz projekt VSIX o nazwie `TWShortcutMenu` i Dodaj szablon okna narzędzia o nazwie **ShortcutMenu** do niego. Aby uzyskać więcej informacji na temat tworzenia okna narzędzi, zobacz [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Określanie menu skrótów
Menu skrótów, takie jak pokazane w tym instruktażu, umożliwia użytkownikowi wybranie z listy kolorów, które są używane do wypełnienia tła okna narzędzi.

1. W *ShortcutMenuPackage. vsct*Znajdź w elemencie GuidSymbol o nazwie guidShortcutMenuPackageCmdSet i Zadeklaruj menu skrótów, grupę menu skrótów i opcje menu. Element GuidSymbol powinien teraz wyglądać następująco:

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Tuż przed elementem Buttons Utwórz element menu, a następnie zdefiniuj w nim menu skrótów.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    Menu skrótów nie ma elementu nadrzędnego, ponieważ nie jest częścią menu lub paska narzędzi.

3. Utwórz element grup z elementem grupy, który zawiera elementy menu skrótów, a następnie skojarz grupę z menu skrótów.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. W elemencie przyciski Zdefiniuj poszczególne polecenia, które pojawią się w menu skrótów. Element Buttons powinien wyglądać następująco:

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. W *ShortcutMenuCommand.cs*, Dodaj definicje dla identyfikatora GUID zestawu poleceń, menu skrótów i elementów menu.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Są to te same identyfikatory poleceń, które są zdefiniowane w sekcji symboli w pliku *ShortcutMenuPackage. vsct* . Grupa kontekstowa nie została tutaj uwzględniona, ponieważ jest wymagana tylko w pliku *. vsct* .

## <a name="implementing-the-shortcut-menu"></a>Implementowanie menu skrótów
 Ta sekcja implementuje menu skrótów i jego poleceń.

1. W programie *ShortcutMenu.cs*okno narzędzi może pobrać usługę poleceń menu, ale kontrolka, która zawiera, nie może. Poniższe kroki pokazują, jak udostępnić usługę poleceń menu dla kontrolki użytkownika.

2. W *ShortcutMenu.cs*Dodaj następujące dyrektywy using:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Zastąp metodę Initialize () okna narzędzi, aby uzyskać usługę poleceń menu i dodać kontrolkę, przekazując do konstruktora usługę poleceń menu:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. W konstruktorze okna narzędzia ShortcutMenu Usuń wiersz, który dodaje formant. Konstruktor powinien teraz wyglądać następująco:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. W *ShortcutMenuControl.XAML.cs*Dodaj pole private dla usługi poleceń menu i Zmień konstruktora formantów, aby przetworzyć usługę poleceń menu. Następnie użyj usługi poleceń menu, aby dodać polecenia menu kontekstowego. Konstruktor ShortcutMenuControl powinien teraz wyglądać podobnie do następującego kodu. Program obsługi poleceń zostanie zdefiniowany później.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. W *ShortcutMenuControl. XAML*Dodaj <xref:System.Windows.UIElement.MouseRightButtonDown> zdarzenie do elementu najwyższego poziomu <xref:System.Windows.Controls.UserControl> . Plik XAML powinien teraz wyglądać następująco:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. W *ShortcutMenuControl.XAML.cs*, Dodaj element zastępczy dla programu obsługi zdarzeń.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Dodaj następujące dyrektywy using do tego samego pliku:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Zaimplementuj `MyToolWindowMouseRightButtonDown` zdarzenie w następujący sposób.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    Spowoduje to utworzenie <xref:System.ComponentModel.Design.CommandID> obiektu menu skrótów, określenie położenia kliknięcia myszą i otwarcie menu skrótów w tej lokalizacji przy użyciu <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> metody.

10. Zaimplementuj procedurę obsługi poleceń.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    W takim przypadku tylko jedna metoda obsługuje zdarzenia dla wszystkich elementów menu, identyfikując <xref:System.ComponentModel.Design.CommandID> odpowiednio i ustawiając kolor tła. Jeśli elementy menu zawierały niepowiązane polecenia, należy utworzyć osobną procedurę obsługi zdarzeń dla każdego polecenia.

## <a name="test-the-tool-window-features"></a>Testowanie funkcji okna narzędzi

1. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

2. W eksperymentalnym wystąpieniu kliknij pozycję **Wyświetl/inne okna**, a następnie kliknij pozycję **ShortcutMenu**. Powinno to spowodować wyświetlenie okna narzędzi.

3. Kliknij prawym przyciskiem myszy treść okna narzędzi. Powinno zostać wyświetlone menu skrótów zawierające listę kolorów.

4. Kliknij kolor w menu skrótów. Kolor tła okna narzędzia powinien zostać zmieniony na wybrany kolor.

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
- [Używanie i świadczenie usług](../extensibility/using-and-providing-services.md)
