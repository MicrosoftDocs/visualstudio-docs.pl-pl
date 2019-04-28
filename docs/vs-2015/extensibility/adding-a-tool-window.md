---
title: Dodawanie okna narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
caps.latest.revision: 53
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9099bc79a555f908ddda12dc9da83f015791fd86
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444837"
---
# <a name="adding-a-tool-window"></a>Dodawanie okna narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku dowiesz się, jak tworzyć okna narzędzi i zintegrować ją z programu Visual Studio w następujący sposób:  
  
- Dodawanie formantu do okna narzędzi.  
  
- Dodawanie paska narzędzi do okna narzędzi.  
  
- Dodaj polecenie do paska narzędzi.  
  
- Implementowanie polecenia.  
  
- Ustaw domyślne położenie okna narzędzia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tool-window"></a>Tworzenie okna narzędzi  
  
1. Utwórz projekt o nazwie **FirstToolWin** przy użyciu szablonu VSIX, a następnie dodaj niestandardowe narzędzie szablon elementu okno o nazwie **FirstToolWindow**.  
  
    > [!NOTE]
    > Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="add-a-control-to-the-tool-window"></a>Dodawanie formantu do okna narzędzi  
  
1. Usuń domyślny formant. Otwórz FirstToolWindowControl.xaml i Usuń **kliknij mnie!** przycisk.  
  
2. W **przybornika**, rozwiń węzeł **wszystkie formanty WPF** sekcji, a następnie przeciągnij **Element multimedialny** kontrolę **FirstToolWindowControl** formularza. Wybierz kontrolkę a następnie w **właściwości** oknie Nazwa tego elementu **mediaElement1**.  
  
## <a name="add-a-toolbar-to-the-tool-window"></a>Dodawanie paska narzędzi do okna narzędzi  
 Dodawanie paska narzędzi w następujący sposób, zagwarantować, jego gradientów i kolory są zgodne z pozostałą częścią środowiska IDE.  
  
1. W **Eksploratora rozwiązań**, otwórz FirstToolWindowPackage.vsct. Pliku vsct definiuje elementów graficznego interfejsu użytkownika (GUI) w oknie narzędzia, za pomocą pliku XML.  
  
2. W `<Symbols>` sekcji, Znajdź `<GuidSymbol>` węzła którego `name` atrybut jest `guidFirstToolWindowPackageCmdSet`. Dodaj dwie poniższe `<IDSymbol>` elementy do listy `<IDSymbol>` elementów w tym węźle, aby zdefiniować paska narzędzi i pasek narzędzi grupy.  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3. Tuż nad `<Buttons>` sekcji, Utwórz `<Menus>` sekcja, która jest podobny do tego:  
  
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
  
     Istnieje kilka różnych rodzajów menu. To menu jest pasek narzędzi w oknie narzędzi zdefiniowane przez jego `type` atrybutu. `guid` i `id` ustawienia tworzą w pełni kwalifikowanym Identyfikatorem paska narzędzi. Zazwyczaj `<Parent>` menu jest grupy zawierającej. Jednakże pasek narzędzi jest zdefiniowany jako własny element nadrzędny. W związku z tym, ten sam identyfikator jest używany dla `<Menu>` i `<Parent>` elementów. `priority` Atrybut jest po prostu "0".  
  
4. Paski narzędzi przypominają menu na wiele sposobów. Na przykład tak, jak menu mogą mieć grupy poleceń, paskach narzędzi grupy mogą również mieć. (W menu, grup poleceń są oddzielone poziome linie. Na paskach narzędzi grupy nie są rozdzielone visual separatorów.)  
  
     Dodaj `<Groups>` sekcję zawierającą `<Group>` elementu. Definiuje grupę, których identyfikator zadeklarowany w `<Symbols>` sekcji. Dodaj `<Groups>` sekcji tuż za `<Menus>` sekcji.  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     Ustawiając element nadrzędny identyfikator GUID i identyfikator GUID i identyfikator paska narzędzi, Dodaj grupę do paska narzędzi.  
  
## <a name="add-a-command-to-the-toolbar"></a>Dodaj polecenie do paska narzędzi  
 Dodaj polecenie do paska narzędzi, który jest wyświetlany jako przycisk.  
  
1. W `<Symbols>` sekcji, Zadeklaruj następujące elementy IDSymbol zaraz po narzędzi i pasek narzędzi deklaracje grupy.  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2. Dodaj element przycisku wewnątrz `<Buttons>` sekcji. Element ten pojawi się na pasku narzędzi w oknie narzędzia, za pomocą ikony wyszukiwania (Lupa).  
  
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
  
3. Otwórz FirstToolWindowCommand.cs i dodaj następujące wiersze w klasie zaraz po istniejących pól.  
  
    ```csharp  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     W ten sposób sprawia, że poleceń dostępnych w kodzie.  
  
## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Dodaj właściwość MediaPlayer do FirstToolWindowControl  
 Z programu obsługi zdarzeń dla formantów paska narzędzi kod musi umożliwiać dostęp do formantu programu Media Player, który jest elementem podrzędnym klasy FirstToolWindowControl.  
  
 W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy FirstToolWindowControl.xaml, kliknij przycisk **Wyświetl kod**i Dodaj następujący kod do klasy FirstToolWindowControl.  
  
```csharp  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## <a name="instantiate-the-tool-window-and-toolbar"></a>Utwórz wystąpienie okna narzędzi i pasek narzędzi  
 Dodawanie paska narzędzi i polecenia menu, który wywołuje **Otwórz plik** okno dialogowe i odtwarzany wybrany plik multimedialny.  
  
1. Otwórz FirstToolWindow.cs i Dodaj następujący kod `using` instrukcji.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2. Wewnątrz klasy FirstToolWindow dodać publiczny odwołanie do formantu FirstToolWindowControl.  
  
    ```csharp  
    public FirstToolWindowControl control;  
    ```  
  
3. Na koniec Konstruktor należy ustawić tę zmienną formantu do nowo utworzonego formantu.  
  
    ```csharp  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4. Tworzy pasek narzędzi w konstruktorze.  
  
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
  
6. Dodaj polecenie menu do paska narzędzi. W klasie FirstToolWindowCommand.cs, dodaj następującą instrukcję using  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
7. W klasie FirstToolWindowCommand Dodaj następujący kod na końcu metody ShowToolWindow(). Polecenie ButtonHandler będą realizowane w następnej sekcji.  
  
    ```csharp  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
#### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Implementowanie polecenia menu w oknie narzędzia  
  
1. W klasie FirstToolWindowCommand dodanie metody ButtonHandler, która wywołuje **Otwórz plik** okna dialogowego. Po wybraniu pliku odtwarza plik nośnika.  
  
2. W klasie FirstToolWindowCommand Dodaj odwołanie prywatnych do okna FirstToolWindow utworzonej w metodzie FindToolWindow().  
  
    ```csharp  
    private FirstToolWindow window;  
    ```  
  
3. Zmień metodę ShowToolWindow(), aby ustawić okno zdefiniowanych powyżej (tak, aby program obsługi poleceń ButtonHandler tak powstały formant będzie okna. Poniżej przedstawiono całą metodę ShowToolWindow().  
  
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
  
4. Dodaj metodę ButtonHandler. Tworzy OpenFileDialog dla użytkownika określić plik, aby odtworzyć, a następnie odgrywa wybranego pliku.  
  
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
  
## <a name="set-the-default-position-for-the-tool-window"></a>Ustaw domyślne położenie okna narzędzi  
 Następnie należy określić domyślną lokalizację w środowisku IDE dla okna narzędzia. Informacje o konfiguracji dla okna narzędzi jest w pliku FirstToolWindowPackage.cs.  
  
1. W FirstToolWindowPackage.cs, Znajdź <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atrybutu na `FirstToolWindowPackage` klasy, która przekazuje typ FirstToolWindow do konstruktora. Aby określić położenie domyślne, należy dodać większą liczbę parametrów dla konstruktora poniższy przykład.  
  
    ```csharp  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     Pierwszy parametr o danej nazwie jest `Style` i jego wartość wynosi `Tabbed`, co oznacza, że okno będzie na karcie w istniejącym oknie. Pozycję dokowania jest określona przez `Window` parametr, n-tym przypadku identyfikator GUID **Eksploratora rozwiązań**.  
  
    > [!NOTE]
    > Aby uzyskać więcej informacji na temat typów okna w IDE, zobacz <xref:EnvDTE.vsWindowType>.  
  
## <a name="testing-the-tool-window"></a>Testowanie okna narzędzi  
  
1. Naciśnij klawisz F5, aby otworzyć nowe wystąpienie eksperymentalne programu Visual Studio kompilacji.  
  
2. Na **widoku** menu wskaż **Windows inne** a następnie kliknij przycisk **pierwsze okno narzędzia**.  
  
     Okno narzędzia media player powinna zostać otwarta w tym samym położeniu co **Eksploratora rozwiązań**. Jeśli nadal występuje w tym samym miejscu wcześniej, Resetuj układ okien (**okno / Zresetuj układ okna**).  
  
3. W oknie narzędzia, kliknij przycisk (ma on ikonę wyszukiwania). Wybierz obsługiwany plik dźwiękowy lub wideo, na przykład C:\windows\media\chimes.wav naciśnij **Otwórz**.  
  
     Powinno być słychać dźwięk brzęczyka.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
