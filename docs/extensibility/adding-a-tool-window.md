---
title: Dodawanie okna narzędzi | Microsoft Docs
description: Dowiedz się, jak utworzyć okno narzędzi i zintegrować je w programie Visual Studio, dodając kontrolkę i pasek narzędzi zawierający polecenie do okna narzędzi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3c84eafcfe19efdf6427db10f65dcf24504b598
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951436"
---
# <a name="add-a-tool-window"></a>Dodaj okno narzędzi

W tym instruktażu dowiesz się, jak utworzyć okno narzędzi i zintegrować je w programie Visual Studio w następujący sposób:

- Dodaj kontrolkę do okna narzędzi.

- Dodaj pasek narzędzi do okna narzędzi.

- Dodaj polecenie do paska narzędzi.

- Zaimplementuj polecenia.

- Ustaw domyślną pozycję okna narzędzi.

## <a name="prerequisites"></a>Wymagania wstępne

Zestaw Visual Studio SDK jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Utwórz okno narzędzi

1. Utwórz projekt o nazwie **FirstToolWin** przy użyciu szablonu VSIX i Dodaj szablon elementu niestandardowego okna narzędzi o nazwie **FirstToolWindow**.

    > [!NOTE]
    > Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Dodawanie kontrolki do okna narzędzi

1. Usuń domyślną kontrolkę. Otwórz *FirstToolWindowControl. XAML* i Usuń **kliknięcie mnie!** Edytuj...

2. W **przyborniku** rozwiń sekcję **wszystkie kontrolki WPF** i przeciągnij formant **elementu multimedialnego** do formularza **FirstToolWindowControl** . Zaznacz kontrolkę, a następnie w oknie **Właściwości** Nazwij ten element **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Dodawanie paska narzędzi do okna narzędzi
Dodanie paska narzędzi w następujący sposób gwarantuje, że jego gradienty i kolory są spójne z resztą środowiska IDE.

1. W **Eksplorator rozwiązań** Otwórz *FirstToolWindowPackage. vsct*. Plik *. vsct* definiuje graficzne elementy interfejsu użytkownika (GUI) w oknie narzędzia przy użyciu kodu XML.

2. W `<Symbols>` sekcji Znajdź `<GuidSymbol>` węzeł, którego `name` atrybut jest `guidFirstToolWindowPackageCmdSet` . Dodaj następujące dwa `<IDSymbol>` elementy do listy `<IDSymbol>` elementów w tym węźle, aby zdefiniować pasek narzędzi i grupę pasków narzędzi.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Tuż nad `<Buttons>` sekcją Utwórz `<Menus>` sekcję podobną do poniższej:

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    Istnieje kilka różnych rodzajów menu. To menu jest paskiem narzędzi w oknie narzędzia, zdefiniowanym przez jego `type` atrybut. `guid`Ustawienia i `id` składają się w pełni kwalifikowany identyfikator paska narzędzi. Zwykle `<Parent>` menu jest grupą zawierającą. Jednak pasek narzędzi jest zdefiniowany jako własny element nadrzędny. W związku z tym ten sam identyfikator jest używany `<Menu>` dla `<Parent>` elementów i. Ten `priority` atrybut ma tylko wartość "0".

4. Paski narzędzi przypominają menu na wiele sposobów. Na przykład, podobnie jak menu może zawierać grupy poleceń, paski narzędzi mogą również mieć grupy. (W menu grupy poleceń są oddzielone liniami poziomymi. Na paskach narzędzi grupy nie są oddzielone separatorami wizualnymi.)

    Dodaj `<Groups>` sekcję, która zawiera `<Group>` element. Definiuje grupę, której identyfikator został zadeklarowany w `<Symbols>` sekcji. Dodaj `<Groups>` sekcję bezpośrednio po `<Menus>` sekcji.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Ustawiając nadrzędny identyfikator GUID i identyfikator na identyfikator GUID i identyfikator paska narzędzi, Dodaj grupę do paska narzędzi.

## <a name="add-a-command-to-the-toolbar"></a>Dodaj polecenie do paska narzędzi

Dodaj polecenie do paska narzędzi, które jest wyświetlane jako przycisk.

1. W `<Symbols>` sekcji Zadeklaruj następujące elementy IDSymbol tuż po deklaracji grupy paska narzędzi i paska narzędzi.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Dodaj element Button wewnątrz `<Buttons>` sekcji. Ten element będzie wyświetlany na pasku narzędzi w oknie narzędzia z ikoną **wyszukiwania** (Lupa).

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. Otwórz *FirstToolWindowCommand.cs* i Dodaj następujące wiersze w klasie tuż po istniejących polach.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Dzięki temu polecenia są dostępne w kodzie.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Dodaj właściwość MediaPlayer do FirstToolWindowControl
Od programów obsługi zdarzeń dla formantów Toolbar, kod musi mieć dostęp do formantu Media Player, który jest elementem podrzędnym klasy FirstToolWindowControl.

W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy *FirstToolWindowControl. XAML*, kliknij polecenie **Wyświetl kod** i Dodaj następujący kod do klasy FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Tworzenie wystąpienia okna narzędzia i paska narzędzi
Dodaj pasek narzędzi i polecenie menu, które wywołuje okno dialogowe **Otwórz plik** i odtwarza wybrany plik multimedialny.

1. Otwórz *FirstToolWindow.cs* i Dodaj następujące `using` dyrektywy:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Wewnątrz klasy FirstToolWindow Dodaj publiczne odwołanie do kontrolki FirstToolWindowControl.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Na końcu konstruktora Ustaw tę zmienną kontroli na nowo utworzoną kontrolkę.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Utwórz wystąpienie paska narzędzi wewnątrz konstruktora.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. W tym momencie Konstruktor FirstToolWindow powinien wyglądać następująco:

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. Dodaj polecenie menu do paska narzędzi. W klasie FirstToolWindowCommand.cs Dodaj następującą dyrektywę using:

    ```csharp
    using System.Windows.Forms;
    ```

7. W klasie FirstToolWindowCommand Dodaj następujący kod na końcu metody ShowToolWindow (). Polecenie ButtonHandler zostanie zaimplementowane w następnej sekcji.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Aby zaimplementować polecenie menu w oknie narzędzi

1. W klasie FirstToolWindowCommand Dodaj metodę ButtonHandler, która wywołuje okno dialogowe **Otwórz plik** . Po wybraniu pliku plik multimedialny jest odtwarzany.

2. W klasie FirstToolWindowCommand Dodaj odwołanie prywatne do okna FirstToolWindow, które jest tworzone w metodzie FindToolWindow ().

    ```csharp
    private FirstToolWindow window;
    ```

3. Zmień metodę ShowToolWindow (), aby ustawić okno zdefiniowane powyżej (tak, aby program obsługi poleceń ButtonHandler mógł uzyskać dostęp do formantu okna. Oto pełna Metoda ShowToolWindow ().

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. Dodaj metodę ButtonHandler. Tworzy OpenFileDialog dla użytkownika, aby określić plik multimedialny do odtworzenia, a następnie odtwarza wybrany plik.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>Ustaw domyślną pozycję okna narzędzi

Następnie określ lokalizację domyślną w IDE dla okna narzędzi. Informacje o konfiguracji okna narzędzia są w pliku *FirstToolWindowPackage.cs* .

1. W *FirstToolWindowPackage.cs* Znajdź <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atrybut `FirstToolWindowPackage` klasy, który przekazuje typ FirstToolWindow do konstruktora. Aby określić domyślną pozycję, należy dodać więcej parametrów do konstruktora poniżej przykładu.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Pierwszy nazwany parametr jest `Style` i jego wartość to `Tabbed` , co oznacza, że okno będzie kartą w istniejącym oknie. Pozycja dokowania jest określana przez `Window` parametr, n ten przypadek, identyfikator GUID **Eksplorator rozwiązań**.

    > [!NOTE]
    > Aby uzyskać więcej informacji na temat typów systemu Windows w IDE, zobacz <xref:EnvDTE.vsWindowType> .

## <a name="test-the-tool-window"></a>Testowanie okna narzędzi

1. Naciśnij klawisz **F5** , aby otworzyć nowe wystąpienie eksperymentalnej kompilacji programu Visual Studio.

2. W menu **Widok** wskaż **inne okna** , a następnie kliknij pozycję **pierwsze okno narzędzi**.

    Okno narzędzia odtwarzacza multimedialnego powinno być otwarte w tym samym położeniu co **Eksplorator rozwiązań**. Jeśli nadal pojawia się w tym samym położeniu co poprzednio, zresetuj układ okna (**Układ okna/resetowania okien**).

3. Kliknij przycisk (zawiera ikonę **wyszukiwania** ) w oknie narzędzia. Wybierz obsługiwany plik dźwiękowy lub wideo, na przykład *C:\windows\media\chimes.wav*, a następnie naciśnij przycisk **Otwórz**.

    Należy słyszeć dźwięk CHIME.

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
