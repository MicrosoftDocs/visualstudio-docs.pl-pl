---
title: Uwidacznianie właściwości w oknie właściwości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c28a0520680951920ee19e91f3df098066f432dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787043"
---
# <a name="exposing-properties-to-the-properties-window"></a>Uwidacznianie właściwości w oknie właściwości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten Instruktaż przedstawia publiczne właściwości obiektu do okna **Właściwości** . Zmiany wprowadzane do tych właściwości są odzwierciedlone w oknie **Właściwości** .  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Uwidacznianie właściwości w oknie właściwości  
 W tej sekcji utworzysz niestandardowe okno narzędzi i zostanie wyświetlone właściwości publiczne skojarzonego obiektu okienka okna w oknie **Właściwości** .  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Aby uwidocznić właściwości okno Właściwości  
  
1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projekt VSIX o nazwie `MyObjectPropertiesExtension` . Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** w obszarze **Visual C#/rozszerzalność**.  
  
2. Dodaj okno narzędzi, dodając szablon elementu niestandardowego okna narzędzi o nazwie `MyToolWindow` . W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj/nowy element**. W **oknie dialogowym Dodaj nowy element**przejdź do **pozycji Visual C# elementy/rozszerzalność** i wybierz **niestandardowe okno narzędzi**. W polu **Nazwa** w dolnej części okna dialogowego Zmień nazwę pliku na `MyToolWindow.cs` . Aby uzyskać więcej informacji na temat tworzenia niestandardowego okna narzędzi, zobacz [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3. Otwórz MyToolWindow.cs i Dodaj następującą instrukcję using:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4. Teraz Dodaj następujące pola do `MyToolWindow` klasy.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5. Dodaj następujący kod do klasy MyToolWindow.  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection`Właściwość używa `GetService` do uzyskania `STrackSelection` usługi, która dostarcza <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfejs. `OnToolWindowCreated`Procedura obsługi zdarzeń i `SelectList` Metoda razem tworzą listę wybranych obiektów, które zawierają tylko obiekt okienka okna narzędzi. `UpdateSelection`Metoda informuje okno **Właściwości** , aby wyświetlić właściwości publiczne okienka okna narzędzi.  
  
6. Skompiluj projekt i Rozpocznij debugowanie. Powinno zostać wyświetlone eksperymentalne wystąpienie programu Visual Studio.  
  
7. Jeśli okno **Właściwości** nie jest widoczne, otwórz je, naciskając klawisz F4.  
  
8. Otwórz okno **MyToolWindow** . Można je znaleźć w **widoku/innych oknach**.  
  
     Zostanie otwarte okno, a właściwości publiczne okienka okno pojawiają się w oknie **Właściwości** .  
  
9. Zmień właściwość **Caption** w oknie **Właściwości** na **właściwości My obiektu**.  
  
     Podpis okna MyToolWindow zostanie odpowiednio zmieniony.  
  
## <a name="exposing-tool-window-properties"></a>Uwidacznianie właściwości okna narzędzi  
 W tej sekcji dodasz okno narzędzi i uwidocznisz jego właściwości. Zmiany wprowadzane do właściwości zostaną odzwierciedlone w oknie **Właściwości** .  
  
#### <a name="to-expose-tool-window-properties"></a>Aby uwidocznić właściwości okna narzędzi  
  
1. Otwórz MyToolWindow.cs i Dodaj publiczną właściwość Boolean ischeckd do klasy MyToolWindow.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Ta właściwość pobiera swój stan z pola wyboru WPF, które zostanie utworzone później.  
  
2. Otwórz MyToolWindowControl.xaml.cs i Zastąp Konstruktor MyToolWindowControl następującym kodem.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Zapewnia to `MyToolWindowControl` dostęp do `MyToolWindow` okienka.  
  
3. W MyToolWindow.cs Zmień konstruktora w `MyToolWindow` następujący sposób:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4. Przejdź do widoku projektu MyToolWindowControl.  
  
5. Usuń przycisk i Dodaj pole wyboru z **przybornika** do lewego górnego rogu.  
  
6. Dodaj sprawdzone i niesprawdzone zdarzenia. Zaznacz pole wyboru w widoku projektu. W oknie **Właściwości** kliknij przycisk programy obsługi zdarzeń (w prawym górnym rogu okna **Właściwości** ). Znajdź **zaznaczone** i wpisz **checkbox_Checked** w polu tekstowym, a następnie w polu tekstowym Znajdź tekst **unchecked** i wpisz **checkbox_Unchecked** .  
  
7. Dodaj programy obsługi zdarzeń pola wyboru:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8. Skompiluj projekt i Rozpocznij debugowanie.  
  
9. W eksperymentalnym wystąpieniu Otwórz okno **MyToolWindow** .  
  
     Poszukaj właściwości okna w oknie **Właściwości** . Właściwość **IsChecked** pojawia się u dołu okna, w kategorii **Moje właściwości** .  
  
10. Zaznacz pole wyboru w oknie **MyToolWindow** . **IsChecked** w oknie **Właściwości** zmienia się na **true**. Wyczyść pole wyboru w oknie **MyToolWindow** . **IsChecked** w oknie **Właściwości** zmieni się na **Fałsz**. Zmień wartość właściwości **Ischeckd** w oknie **Właściwości** . Pole wyboru w oknie **MyToolWindow** zmieni się na zgodną z nową wartością.  
  
    > [!NOTE]
    > Jeśli musisz usunąć obiekt, który jest wyświetlany w oknie **Właściwości** , najpierw Wywołaj `OnSelectChange` z `null` kontenerem wyboru. Po usunięciu właściwości lub obiektu można przejść do kontenera wyboru, który został zaktualizowany <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> i <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> listę.  
  
## <a name="changing-selection-lists"></a>Zmienianie list wyboru  
 W tej sekcji dodasz listę wyboru dla podstawowej klasy właściwości i użyj interfejsu okna narzędzi, aby wybrać listę wyboru do wyświetlenia.  
  
#### <a name="to-change-selection-lists"></a>Aby zmienić listy wyboru  
  
1. Otwórz MyToolWindow.cs i Dodaj klasę publiczną o nazwie `Simple` .  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2. Dodaj właściwość Simpleobject do klasy MyToolWindow oraz dwie metody, aby przełączyć wybór okna **Właściwości** między okienkiem okna a `Simple` obiektem.  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3. W MyToolWindowControl.cs Zastąp programy obsługi pól wyboru następującymi wierszami kodu:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4. Skompiluj projekt i Rozpocznij debugowanie.  
  
5. W eksperymentalnym wystąpieniu Otwórz okno **MyToolWindow** .  
  
6. Zaznacz pole wyboru w oknie **MyToolWindow** . W oknie **Właściwości** są wyświetlane `Simple` właściwości obiektu, **SomeText** i **ReadOnly**. Wyczyść pole wyboru. Właściwości publiczne okna pojawiają się w oknie **Właściwości** .  
  
    > [!NOTE]
    > Nazwa wyświetlana **SomeText** to **mój tekst**.  
  
## <a name="best-practice"></a>Najlepsze rozwiązanie  
 W tym instruktażu <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jest zaimplementowany, tak aby wybrana kolekcja obiektów i wybrana kolekcja obiektów były tymi samymi kolekcjami. Tylko wybrany obiekt pojawia się na liście przeglądarki właściwości. Aby uzyskać bardziej kompletną implementację ISelectionContainer, zobacz przykłady Reference. ToolWindow.  
  
 Okna narzędzi programu Visual Studio są utrwalane między sesjami programu Visual Studio. Aby uzyskać więcej informacji na temat utrwalania stanu okna narzędzi, zobacz <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md)
