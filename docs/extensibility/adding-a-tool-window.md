---
title: Dodawanie okna narzędzia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573f01043d8b1b0c2293a3ebf6e0c246a8727d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740253"
---
# <a name="add-a-tool-window"></a>Dodawanie okna narzędzia

W tym instruktażu dowiesz się, jak utworzyć okno narzędzia i zintegrować je z programem Visual Studio w następujący sposób:

- Dodaj formant do okna narzędzia.

- Dodawanie paska narzędzi do okna narzędzia.

- Dodaj polecenie do paska narzędzi.

- Zaimplementuj polecenia.

- Ustaw domyślną pozycję okna narzędzia.

## <a name="prerequisites"></a>Wymagania wstępne

Zestaw SDK programu Visual Studio jest dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Tworzenie okna narzędzia

1. Utwórz projekt o nazwie **FirstToolWin** przy użyciu szablonu VSIX i dodaj niestandardowy szablon elementu okna narzędzia o nazwie **FirstToolWindow**.

    > [!NOTE]
    > Aby uzyskać więcej informacji na temat tworzenia rozszerzenia z oknem narzędzia, zobacz [Tworzenie rozszerzenia z oknem narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Dodawanie formantu do okna narzędzia

1. Usuń formant domyślny. Otwórz *plik FirstToolWindowControl.xaml* i usuń **przycisk Kliknij mnie!** Edytuj...

2. W **przyborniku**rozwiń sekcję **Wszystkie formanty WPF** i przeciągnij kontrolkę **elementu multimedialnego** do formularza **FirstToolWindowControl.** Wybierz formant i w oknie **Właściwości nazwij** ten element **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Dodawanie paska narzędzi do okna narzędzia
Dodając pasek narzędzi w następujący sposób, gwarantujesz, że jego gradienty i kolory są zgodne z resztą IDE.

1. W **Eksploratorze rozwiązań**otwórz *plik FirstToolWindowPackage.vsct*. Plik *vsct* definiuje elementy graficznego interfejsu użytkownika (GUI) w oknie narzędzia przy użyciu formatu XML.

2. W `<Symbols>` sekcji znajdź `<GuidSymbol>` węzeł, `name` którego `guidFirstToolWindowPackageCmdSet`atrybutem jest . Dodaj następujące `<IDSymbol>` dwa elementy do `<IDSymbol>` listy elementów w tym węźle, aby zdefiniować pasek narzędzi i grupę paska narzędzi.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Tuż nad `<Buttons>` sekcją `<Menus>` utwórz sekcję podobną do tej następującej:

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

    Istnieje kilka różnych rodzajów menu. To menu jest paskiem narzędzi w oknie `type` narzędzia, zdefiniowanym przez jego atrybut. Ustawienia `guid` `id` i ustawienia składają się na w pełni kwalifikowany identyfikator paska narzędzi. Zazwyczaj `<Parent>` menu jest grupą zawierającą. Jednak pasek narzędzi jest zdefiniowany jako własny element nadrzędny. W związku z tym ten sam `<Menu>` `<Parent>` identyfikator jest używany dla i elementów. Atrybut `priority` jest tylko "0".

4. Paski narzędzi przypominają menu na wiele sposobów. Na przykład, tak jak menu może mieć grupy poleceń, paski narzędzi mogą również mieć grupy. (W menu grupy poleceń są oddzielone liniami poziomymi. Na paskach narzędzi grupy nie są oddzielone przegrodami wizualnymi.)

    Dodaj `<Groups>` sekcję, `<Group>` która zawiera element. Definiuje grupę, której identyfikator został `<Symbols>` zadeklarowany w sekcji. Dodaj `<Groups>` sekcję tuż `<Menus>` za sekcją.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Ustawiając nadrzędny identyfikator GUID i identyfikator na identyfikator GUID i identyfikator paska narzędzi, należy dodać grupę do paska narzędzi.

## <a name="add-a-command-to-the-toolbar"></a>Dodawanie polecenia do paska narzędzi

Dodaj polecenie do paska narzędzi, które jest wyświetlane jako przycisk.

1. W `<Symbols>` sekcji zadeklarować następujące IDSymbol elementów tuż po pasku narzędzi i deklaracji grupy paska narzędzi.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Dodaj button element `<Buttons>` wewnątrz sekcji. Ten element pojawi się na pasku narzędzi w oknie narzędzia z ikoną **wyszukiwania** (lupy).

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

3. Otwórz *FirstToolWindowCommand.cs* i dodaj następujące wiersze w klasie tuż po istniejących polach.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    W ten sposób sprawia, że polecenia dostępne w kodzie.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Dodawanie właściwości MediaPlayer do usługi FirstToolWindowControl
Z obsługi zdarzeń dla formantów paska narzędzi, kod musi mieć możliwość uzyskania dostępu do formantu media player, który jest elementem podrzędnym FirstToolWindowControl klasy.

W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy *pozycję FirstToolWindowControl.xaml*, kliknij polecenie **Wyświetl kod**i dodaj następujący kod do klasy FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Tworzenie wystąpienia okna narzędzia i paska narzędzi
Dodaj pasek narzędzi i polecenie menu, które wywołuje okno dialogowe **Otwórz plik** i odtwarza wybrany plik multimedialny.

1. Otwórz *FirstToolWindow.cs* i dodaj następujące `using` dyrektywy:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Wewnątrz FirstToolWindow klasy, dodać odwołanie publiczne do Formantu FirstToolWindowControl.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Na końcu konstruktora ustaw tę zmienną formantu na nowo utworzony formant.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Tworzenie wystąpienia paska narzędzi wewnątrz konstruktora.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. W tym momencie FirstToolWindow konstruktora powinien wyglądać następująco:

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

6. Dodaj polecenie menu do paska narzędzi. W FirstToolWindowCommand.cs klasy dodaj następujące elementy przy użyciu dyrektywy:

    ```csharp
    using System.Windows.Forms;
    ```

7. W klasie FirstToolWindowCommand dodaj następujący kod na końcu metody ShowToolWindow(). ButtonHandler polecenia zostaną zaimplementowane w następnej sekcji.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Aby zaimplementować polecenie menu w oknie narzędzia

1. W klasie FirstToolWindowCommand dodaj metodę ButtonHandler, która wywołuje okno dialogowe **Otwórz plik.** Po wybraniu pliku jest odtwarzany plik multimedialny.

2. W klasie FirstToolWindowCommand dodaj odwołanie prywatne do okna FirstToolWindow, które zostanie utworzone w metodzie FindToolWindow().

    ```csharp
    private FirstToolWindow window;
    ```

3. Zmień metodę ShowToolWindow(), aby ustawić okno zdefiniowane powyżej (tak, aby program obsługi poleceń ButtonHandler mógł uzyskać dostęp do formantu okna. Oto pełna metoda ShowToolWindow().

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

4. Dodaj ButtonHandler metody. Tworzy OpenFileDialog dla użytkownika, aby określić plik multimedialny do odtworzenia, a następnie odtwarza wybrany plik.

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

## <a name="set-the-default-position-for-the-tool-window"></a>Ustawianie domyślnej pozycji okna narzędzia

Następnie należy określić domyślną lokalizację w IDE dla okna narzędzia. Informacje o konfiguracji okna narzędzia znajdują się w pliku *FirstToolWindowPackage.cs.*

1. W *FirstToolWindowPackage.cs*, znajdź <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atrybut w `FirstToolWindowPackage` klasie, który przekazuje FirstToolWindow typu do konstruktora. Aby określić pozycję domyślną, należy dodać więcej parametrów do konstruktora w poniższym przykładzie.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Pierwszy nazwany parametr `Style` jest i `Tabbed`jego wartość jest , co oznacza, że okno będzie kartę w istniejącym oknie. Pozycja dokowania jest `Window` określona przez parametr, n w tym przypadku, identyfikator GUID **Eksploratora rozwiązań**.

    > [!NOTE]
    > Aby uzyskać więcej informacji na temat typów <xref:EnvDTE.vsWindowType>okien w IDE, zobacz .

## <a name="test-the-tool-window"></a>Testowanie okna narzędzia

1. Naciśnij **klawisz F5,** aby otworzyć nowe wystąpienie eksperymentalnej kompilacji programu Visual Studio.

2. W menu **Widok** wskaż polecenie **Inne okna,** a następnie kliknij polecenie **Pierwsze okno narzędzia**.

    Okno narzędzia odtwarzacza multimedialnego powinno być otwierane w tej samej pozycji co **Eksplorator rozwiązań**. Jeśli nadal pojawia się w tej samej pozycji co poprzednio, zresetuj układ okna **(Okno / Resetowanie układu okna**).

3. Kliknij przycisk (ma ikonę **wyszukiwania)** w oknie narzędzia. Wybierz obsługiwany plik dźwiękowy lub wideo, na przykład *C:\windows\media\chimes.wav*, a następnie naciśnij **przycisk Otwórz**.

    Powinieneś usłyszeć dźwięk gongu.

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
