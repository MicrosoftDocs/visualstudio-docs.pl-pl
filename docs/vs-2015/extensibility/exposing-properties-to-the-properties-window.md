---
title: Uwidacznianie właściwości w oknie dialogowym właściwości | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 0b7b9e352c3042e5175b7420a9d4203ca7f59e7f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117144"
---
# <a name="exposing-properties-to-the-properties-window"></a>Uwidacznianie właściwości w oknie właściwości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik udostępnia publiczne właściwości obiektu do **właściwości** okna. Zmiany te właściwości są odzwierciedlane w **właściwości** okna.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Uwidacznianie właściwości w oknie właściwości  
 W tej sekcji utworzysz niestandardowego okna narzędzi i wyświetlić publiczne właściwości obiektu w okienku skojarzonych okien w **właściwości** okna.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Aby udostępnić właściwości w oknie właściwości  
  
1. Każde rozszerzenie programu Visual Studio rozpoczyna się od Projekt wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Tworzenie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu VSIX, o nazwie `MyObjectPropertiesExtension`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2. Dodawanie okna narzędzi, dodając szablon elementu niestandardowego okna narzędzi o nazwie `MyToolWindow`. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **okna dialogowego Dodaj nowy element**, przejdź do **elementy Visual C# / rozszerzalności** i wybierz **okna narzędzi niestandardowych**. W **nazwa** pola w dolnej części okna dialogowego, Zmień nazwę pliku, aby `MyToolWindow.cs`. Aby uzyskać więcej informacji o sposobie tworzenia niestandardowego okna narzędzi, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3. Otwórz MyToolWindow.cs i dodaj następującą instrukcję using:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4. Teraz dodaj następujące pola do `MyToolWindow` klasy.  
  
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
  
     `TrackSelection` Używa właściwości `GetService` uzyskać `STrackSelection` usługa, która zapewnia <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfejsu. `OnToolWindowCreated` Programu obsługi zdarzeń i `SelectList` metoda razem utworzyć listę wybranych obiektów, która zawiera tylko narzędzie okno okienka samego obiektu. `UpdateSelection` Informuje metoda **właściwości** okno, aby wyświetlić właściwości publiczne okienka okna narzędzi.  
  
6. Skompiluj projekt, a następnie rozpocząć debugowanie. Powinna zostać wyświetlona doświadczalnym wystąpieniu programu Visual Studio.  
  
7. Jeśli **właściwości** okno nie jest widoczna, otwórz ją, naciskając klawisz F4.  
  
8. Otwórz **MyToolWindow** okna. Znaleźć go w **widok / inne Windows**.  
  
     Zostanie otwarte okno i publicznymi właściwościami okienku okna pojawiają się w **właściwości** okna.  
  
9. Zmiana **podpis** właściwość **właściwości** okna **Moje właściwości obiektu**.  
  
     Tytuł okna MyToolWindow zmienia się odpowiednio.  
  
## <a name="exposing-tool-window-properties"></a>Udostępnianie właściwości okna narzędzi  
 W tej sekcji można dodać okna narzędzi i udostępnianie jej właściwości. Zmiany wprowadzone do właściwości są odzwierciedlane w **właściwości** okna.  
  
#### <a name="to-expose-tool-window-properties"></a>Aby udostępnić narzędzia Właściwości okna  
  
1. Otwórz MyToolWindow.cs i Dodaj właściwość typu boolean publicznych IsChecked do klasy MyToolWindow.  
  
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
  
     Tej właściwości pobiera jego stan z pola wyboru WPF, która zostanie utworzona później.  
  
2. Otwórz MyToolWindowControl.xaml.cs i Zamień Konstruktor MyToolWindowControl następujący kod.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Dzięki temu `MyToolWindowControl` dostęp do `MyToolWindow` okienka.  
  
3. W MyToolWindow.cs, zmień `MyToolWindow` konstruktora w następujący sposób:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4. Zmień na widok projektu MyToolWindowControl.  
  
5. Usuń przycisk i pole wyboru z **przybornika** na lewym górnym rogu.  
  
6. Dodaj zdarzenia zaznaczone i niezaznaczone. Zaznacz pole wyboru w widoku Projekt. W **właściwości** okna, kliknij przycisk programów obsługi zdarzeń (u góry po prawej stronie **właściwości** okno). Znajdź **zaznaczone** i typ **checkbox_Checked** w polu tekstowym, następnie znajdź **niezaznaczone** i typ **checkbox_Unchecked** w polu tekstowym.  
  
7. Dodawanie obsługi zdarzeń pola wyboru:  
  
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
  
8. Skompiluj projekt, a następnie rozpocząć debugowanie.  
  
9. W doświadczalnym wystąpieniu Otwórz **MyToolWindow** okna.  
  
     Wyszukaj w oknie właściwości w **właściwości** okna. **IsChecked** właściwość pojawia się w dolnej części okna, w obszarze **właściwości mojego** kategorii.  
  
10. Zaznacz to pole wyboru **MyToolWindow** okna. **IsChecked** w **właściwości** okno zmienia się na **True**. Usuń zaznaczenie pola wyboru w **MyToolWindow** okna. **IsChecked** w **właściwości** okno zmienia się na **False**. Zmień wartość właściwości **IsChecked** w **właściwości** okna. Pole wyboru w **MyToolWindow** okno zmiany, aby pasowała do nowej wartości.  
  
    > [!NOTE]
    >  Jeśli użytkownik musi dysponować obiektu, który jest wyświetlany w **właściwości** okna, wywołanie `OnSelectChange` z `null` kontener wyboru pierwszego. Po disposing właściwość lub obiekt, można zmienić na kontenerze zaznaczenia, który został zaktualizowany <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> i <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> listy.  
  
## <a name="changing-selection-lists"></a>Zmiana listy wyboru  
 W tej sekcji możesz dodać listę wyboru dla klasy podstawowe właściwości i wybierz które listy wyboru, aby wyświetlić za pomocą interfejsu okna narzędzia.  
  
#### <a name="to-change-selection-lists"></a>Aby zmienić wybór dotyczący listy  
  
1. Otwórz MyToolWindow.cs i Dodaj klasę publiczną, o nazwie `Simple`.  
  
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
  
2. Dodawanie właściwości SimpleObject do klasy MyToolWindow, a także dwie metody, aby przełączyć **właściwości** okno wyboru między okienka w oknie i `Simple` obiektu.  
  
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
  
3. W MyToolWindowControl.cs programy obsługi pól wyboru należy zastąpić następujące wiersze kodu:  
  
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
  
4. Skompiluj projekt, a następnie rozpocząć debugowanie.  
  
5. W doświadczalnym wystąpieniu Otwórz **MyToolWindow** okna.  
  
6. Zaznacz pole wyboru w **MyToolWindow** okna. **Właściwości** jest wyświetlana w oknie `Simple` obiektu właściwości **SomeText** i **tylko do odczytu**. Usuń zaznaczenie pola wyboru. Właściwości publiczne okna pojawiają się w **właściwości** okna.  
  
    > [!NOTE]
    >  Nazwa wyświetlana **SomeText** jest **Mój tekst**.  
  
## <a name="best-practice"></a>Najlepszym rozwiązaniem jest  
 W tym przewodniku <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jest implementowany kolekcji obiektów można wybierać i kolekcji wybranego obiektu są tej samej kolekcji. Wybranego obiektu pojawia się na liście przeglądarkę właściwości. Bardziej kompletny wykonania ISelectionContainer Zobacz przykłady Reference.ToolWindow.  
  
 Okna narzędzi w usłudze Visual Studio są zachowywane między sesjami programu Visual Studio. Aby uzyskać więcej informacji na temat utrwalanie stanu okna narzędzi, zobacz <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md)
