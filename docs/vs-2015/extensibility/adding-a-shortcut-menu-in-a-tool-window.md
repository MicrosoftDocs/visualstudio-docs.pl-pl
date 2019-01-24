---
title: Dodawanie Menu skrótów w oknie narzędzia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5587c559615bcf6ae17a445490951c32741086c3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797529"
---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Dodawanie menu skrótów w oknie narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku umieszcza menu skrótów w oknie narzędzi. Menu podręczne jest menu, który jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy przycisk, pole tekstowe lub tło okna. Polecenia menu skrótów zachowują się taka sama jak poleceń na inne menu i paski narzędzi. Do obsługi menu skrótów, należy je określić w pliku vsct i wyświetl ją w odpowiedzi na prawym przyciskiem myszy myszy.  
  
 Okna narzędzi, który składa się z kontrolki użytkownika WPF w klasę okna narzędzia niestandardowego, który dziedziczy z <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.  
  
 W tym instruktażu przedstawiono sposób tworzenia menu skrótów jako menu programu Visual Studio, przez zadeklarowanie elementów menu w pliku vsct, a następnie wdrożyć je w klasie, która definiuje okno narzędzia przy użyciu środowiska pakietu zarządzanego. Takie podejście ułatwia dostęp do poleceń programu Visual Studio, elementy interfejsu użytkownika i modelu obiektu automatyzacji.  
  
 Alternatywnie, jeśli z menu skrótów nie uzyskać dostępu do funkcji programu Visual Studio, możesz użyć <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwość elementu XAML w kontrolce użytkownika. Aby uzyskać więcej informacji, zobacz [ContextMenu](http://msdn.microsoft.com/library/2f40b2bb-b702-4706-9fc4-10bcfd7cc35d).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Tworzenie pakietu Menu skrótów okna narzędzi  
  
1.  Utwórz projekt VSIX, o nazwie `TWShortcutMenu` i Dodaj szablon do okna narzędzia o nazwie **ShortCutMenu** do niego. Aby uzyskać więcej informacji na temat tworzenia okna narzędzi, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Określanie Menu skrótów  
 Menu skrótów, takich jak przedstawionego w tym przewodniku zezwala użytkownikowi na wybranie z listy kolorów, które są używane do wypełnienia tła okna narzędzi.  
  
1.  Znajdź w GuidSymbol, element o nazwie guidShortcutMenuPackageCmdSet ShortcutMenuPackage.vsct i zadeklarować menu skrótów, grupy menu skrótów i opcje menu. GuidSymbol, element powinien teraz wyglądać następująco:  
  
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
  
2.  Tuż przed Buttons, element należy utworzyć element menu, a następnie zdefiniować menu skrótów w nim.  
  
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
  
3.  Utwórz element grupy z elementem grupy, który zawiera elementy menu skrótów i skojarzyć grupy z menu skrótów.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  W elemencie przyciski należy zdefiniować pojedynczych poleceń, które będą pojawiać się w menu skrótów. Buttons, element powinien wyglądać następująco:  
  
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
  
5.  W ShortcutMenuPackageGuids.cs dodania definicji dla polecenia zestawu identyfikator GUID, menu skrótów i elementów menu.  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Są to takich samych identyfikatorów polecenia, które są zdefiniowane w sekcji symbole pliku ShortcutMenuPackage.vsct. Grupy kontekstu nie jest uwzględnione w tym miejscu, ponieważ jest wymagany tylko w pliku vsct.  
  
## <a name="implementing-the-shortcut-menu"></a>Implementowanie Menu skrótów  
 W tej sekcji implementuje menu skrótów i jego poleceń.  
  
1.  W ShortcutMenu.cs okno narzędzia można uzyskać usługi polecenia menu, ale nie kontrolki, które zawiera. Poniższe kroki pokazują, jak udostępnić usługi polecenia menu do kontrolki użytkownika.  
  
2.  W ShortcutMenu.cs, Dodaj następujące instrukcje using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Przesłoń metodę Initialize() okna narzędzi, aby uzyskać usługi polecenia menu i Dodaj kontrolkę, przekazując usługi polecenia menu do konstruktora:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  W Konstruktorze okna narzędzia ShortcutMenu usunąć wiersza, który dodaje formant. Konstruktor powinien teraz wyglądać następująco:  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  W ShortcutMenuControl.xaml.cs Dodaj pole prywatne dla usługi polecenia menu i zmień Konstruktor kontrolki do wykonania usługi polecenia menu. Następnie użyj usługi polecenia menu, aby dodać polecenia menu kontekstowego. Konstruktor ShortcutMenuControl powinna teraz wyglądać podobnie do poniższego kodu. Później będzie można zdefiniować program obsługi poleceń.  
  
    ```csharp  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  W ShortcutMenuControl.xaml, Dodaj <xref:System.Windows.UIElement.MouseRightButtonDown> zdarzenia najwyższego poziomu <xref:System.Windows.Controls.UserControl> elementu. Plik XAML powinien teraz wyglądać następująco:  
  
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
  
7.  W ShortcutMenuControl.xaml.cs Dodaj odcinek programu obsługi zdarzeń.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Dodaj następujący kod do tego samego pliku przy użyciu instrukcji:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. Implementowanie `MyToolWindowMouseRightButtonDown` zdarzeń w następujący sposób.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     Spowoduje to utworzenie <xref:System.ComponentModel.Design.CommandID> obiekt menu skrótów, określa lokalizację kliknięcie myszą i otwarcie menu skrótów w tej lokalizacji przy użyciu <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> metody.  
  
10. Zaimplementuj program obsługi poleceń.  
  
    ```csharp  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     W tym przypadku tylko jedna metoda obsługi zdarzeń dla wszystkich elementów menu, określając <xref:System.ComponentModel.Design.CommandID> i w związku z tym Ustawianie koloru tła. Jeśli elementy menu miał niepowiązanych poleceń, czy utworzono oddzielne zdarzenie procedury obsługi dla każdego polecenia.  
  
## <a name="testing-the-tool-window-features"></a>Testowanie funkcji okna narzędzi  
  
1.  Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.  
  
2.  W doświadczalnym wystąpieniu kliknij **widok / inne Windows**, a następnie kliknij przycisk **ShortcutMenu**. W ten sposób powinien być wyświetlany okna narzędzia.  
  
3.  Kliknij prawym przyciskiem myszy w treści okna narzędzia. Powinny być wyświetlane menu skrótów, które zawiera listę kolorów.  
  
4.  Kliknij przycisk koloru w menu skrótów. Wybrany kolor, należy je zmienić kolor tła okna narzędzia.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Korzystanie z usług i dostarczanie ich](../extensibility/using-and-providing-services.md)
