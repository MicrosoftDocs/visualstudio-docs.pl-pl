---
title: Dodawanie menu skrótów w oknie narzędzia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 0f5b5b79721aa910c46e2580228d3f3a7836f70d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740282"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Dodawanie menu skrótów w oknie narzędzia
W tym instruktażu umieszcza się menu skrótów w oknie narzędzia. Menu skrótów to menu wyświetlane, gdy użytkownik kliknie prawym przyciskiem myszy przycisk, pole tekstowe lub tło okna. Polecenia w menu skrótów zachowują się tak samo jak polecenia w innych menu lub na paskach narzędzi. Aby obsługiwać menu skrótów, określ go w pliku *vsct* i wyświetl go w odpowiedzi na kliknięcie prawym przyciskiem myszy.

Okno narzędzia składa się z formantu użytkownika WPF w <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>niestandardowej klasie okna narzędzia, która dziedziczy po .

W tym przewodniku pokazano, jak utworzyć menu skrótów jako menu programu Visual Studio, deklarując elementy menu w pliku *vsct,* a następnie za pomocą struktury pakietu zarządzanego, aby zaimplementować je w klasie, która definiuje okno narzędzia. Takie podejście ułatwia dostęp do poleceń programu Visual Studio, elementów interfejsu użytkownika i modelu obiektów automatyzacji.

Alternatywnie, jeśli menu skrótów nie będzie uzyskiwać <xref:System.Windows.FrameworkElement.ContextMenu%2A> dostępu do funkcji programu Visual Studio, można użyć właściwości elementu XAML w formancie użytkownika. Aby uzyskać więcej informacji, zobacz [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Wymagania wstępne
Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Tworzenie pakietu menu skrótów okna narzędzia

1. Utwórz projekt VSIX o nazwie `TWShortcutMenu` i dodaj do niego szablon okna narzędzia o nazwie **ShortcutMenu.** Aby uzyskać więcej informacji na temat tworzenia okna narzędzia, zobacz [Tworzenie rozszerzenia z oknem narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Określanie menu skrótów
Menu skrótów, takie jak pokazane w tym instruktażu, umożliwia użytkownikowi wybranie z listy kolorów, które są używane do wypełnienia tła okna narzędzia.

1. W *pliku ShortcutMenuPackage.vsct*znajdź w elemencie GuidSymbol o nazwie guidShortcutMenuPackageCmdSet i zadeklaruj menu skrótów, grupę menu skrótów i opcje menu. GuidSymbol element powinien teraz wyglądać następująco:

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

2. Tuż przed Button element, utwórz menu element, a następnie zdefiniować menu skrótów w nim.

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

    Menu skrótów nie ma obiektu nadrzędnego, ponieważ nie jest częścią menu ani paska narzędzi.

3. Utwórz element Grupy z elementem Grupy zawierającym elementy menu skrótów i skojarz grupę z menu skrótów.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. W przyciskach element, zdefiniuj poszczególne polecenia, które pojawią się w menu skrótów. Buttons element powinien wyglądać następująco:

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

5. W *ShortcutMenuCommand.cs*dodaj definicje identyfikatora GUID zestawu poleceń, menu skrótów i elementów menu.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Są to te same identyfikatory poleceń, które są zdefiniowane w sekcji Symbole pliku *ShortcutMenuPackage.vsct.* Grupa kontekstu nie jest uwzględniona w tym miejscu, ponieważ jest wymagana tylko w pliku *vsct.*

## <a name="implementing-the-shortcut-menu"></a>Implementowanie menu skrótów
 W tej sekcji zaimplementowano menu skrótów i jego polecenia.

1. W *ShortcutMenu.cs*okno narzędzia może uzyskać usługę poleceń menu, ale formant, który zawiera, nie może. Poniższe kroki pokazują, jak udostępnić usługę poleceń menu dla formantu użytkownika.

2. W *ShortcutMenu.cs*, dodaj następujące za pomocą dyrektyw:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Zastąp metodę Initialize() okna narzędzia, aby uzyskać usługę poleceń menu i dodać formant, przekazując usługę poleceń menu do konstruktora:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. W konstruktorze okna narzędzia ShortcutMenu usuń linię, która dodaje formant. Konstruktor powinien teraz wyglądać następująco:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. W *ShortcutMenuControl.xaml.cs*, dodaj pole prywatne dla usługi poleceń menu i zmień konstruktor formantu, aby przejąć usługę poleceń menu. Następnie użyj usługi poleceń menu, aby dodać polecenia menu kontekstowego. Konstruktor ShortcutMenuControl powinien teraz wyglądać następująco. Program obsługi poleceń zostanie zdefiniowany później.

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

6. W *pliku ShortcutMenuControl.xaml*dodaj <xref:System.Windows.UIElement.MouseRightButtonDown> zdarzenie <xref:System.Windows.Controls.UserControl> do elementu najwyższego poziomu. Plik XAML powinien teraz wyglądać następująco:

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

7. W *ShortcutMenuControl.xaml.cs*, dodaj skrót dla programu obsługi zdarzeń.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Dodaj do tego samego pliku następujące elementy za pomocą dyrektyw:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Zaimplementuj zdarzenie w `MyToolWindowMouseRightButtonDown` następujący sposób.

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

    Spowoduje to <xref:System.ComponentModel.Design.CommandID> utworzenie obiektu dla menu skrótów, określenie lokalizacji kliknięcia myszą i <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> otwarcie menu skrótów w tym miejscu przy użyciu metody.

10. Zaimplementuj program obsługi poleceń.

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

    W takim przypadku tylko jedna metoda obsługuje zdarzenia dla wszystkich <xref:System.ComponentModel.Design.CommandID> elementów menu, identyfikując i odpowiednio ustawiając kolor tła. Jeśli elementy menu zawierały niepowiązane polecenia, dla każdego polecenia utworzono osobny program obsługi zdarzeń.

## <a name="test-the-tool-window-features"></a>Testowanie funkcji okna narzędzia

1. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.

2. W wystąpieniu eksperymentalnym kliknij pozycję **Widok / Inny system Windows**, a następnie kliknij pozycję **ShortcutMenu**. W ten sposób należy wyświetlić okno narzędzia.

3. Kliknij prawym przyciskiem myszy w treści okna narzędzia. Powinno być wyświetlane menu skrótów z listą kolorów.

4. Kliknij kolor w menu skrótów. Kolor tła okna narzędzia należy zmienić na wybrany kolor.

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
- [Korzystanie i świadczenie usług](../extensibility/using-and-providing-services.md)
