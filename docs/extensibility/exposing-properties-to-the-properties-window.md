---
title: Udostępnianie właściwości do okna Właściwości | Dokumenty firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f84962628ae550676e2c2eeb10c0f3baeca1bb58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711828"
---
# <a name="expose-properties-to-the-properties-window"></a>Uwidacznianie właściwości do okna Właściwości

Ten instruktaż udostępnia właściwości publiczne obiektu do **właściwości** okna. Zmiany wprowadzone w tych właściwościach są odzwierciedlane w oknie **Właściwości.**

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Uwidacznianie właściwości do okna Właściwości

W tej sekcji utworzysz niestandardowe okno narzędzia i wyświetlisz właściwości publiczne skojarzonego obiektu okienka okna w oknie **Właściwości.**

### <a name="to-expose-properties-to-the-properties-window"></a>Aby udostępnić właściwości do okna Właściwości

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierał zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX o nazwie `MyObjectPropertiesExtension`. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt,** wyszukując "vsix".

2. Dodaj okno narzędzia, dodając szablon elementu `MyToolWindow`niestandardowego okna narzędzia o nazwie . W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. W **oknie dialogowym Dodawanie nowego elementu**przejdź do pozycji**Rozszerzalność** **elementów** > programu Visual C# i wybierz pozycję **Okno narzędzia niestandardowego**. W polu **Nazwa** u dołu okna dialogowego zmień nazwę pliku na *MyToolWindow.cs*. Aby uzyskać więcej informacji na temat tworzenia niestandardowego okna narzędzia, zobacz [Tworzenie rozszerzenia z oknem narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Otwórz *MyToolWindow.cs* i dodaj następujące instrukcje za pomocą:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Teraz dodaj następujące pola `MyToolWindow` do klasy.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Dodaj następujący kod `MyToolWindow` do klasy.

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

   public void UpdateSelection()
   {
       ITrackSelection track = TrackSelection;
       if (track != null)
           track.OnSelectChange((ISelectionContainer)selContainer);
   }

   public void SelectList(ArrayList list)
   {
       selContainer = new SelectionContainer(true, false);
       selContainer.SelectableObjects = list;
       selContainer.SelectedObjects = list;
       UpdateSelection();
   }

   public override void OnToolWindowCreated()
   {
       ArrayList listObjects = new ArrayList();
       listObjects.Add(this);
       SelectList(listObjects);
   }
   ```

    Właściwość `TrackSelection` służy `GetService` do `STrackSelection` uzyskania usługi, <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> która zapewnia interfejs. Program `OnToolWindowCreated` obsługi `SelectList` zdarzeń i metoda razem utworzyć listę zaznaczonych obiektów, która zawiera tylko obiekt okienka okna narzędzia, sam. Metoda `UpdateSelection` informuje **właściwości** okna, aby wyświetlić właściwości publiczne okienka okna narzędzia.

6. Skompiluj projekt i rozpocznij debugowanie. Powinno pojawić się eksperymentalne wystąpienie programu Visual Studio.

7. Jeśli okno **Właściwości** nie jest widoczne, otwórz je, naciskając klawisz **F4**.

8. Otwórz okno **MyToolWindow.** Można go znaleźć w **Widoku** > **Inne okna**.

    Okno zostanie otwarte, a właściwości publiczne okienka okna pojawią się w oknie **Właściwości.**

9. Zmień właściwość **Caption** w oknie **Właściwości** na **Właściwości mojego obiektu**.

     Podpis okna MyToolWindow zmienia się odpowiednio.

## <a name="expose-tool-window-properties"></a>Uwidacznianie właściwości okna narzędzia

W tej sekcji należy dodać okno narzędzia i uwidaczniać jego właściwości. Zmiany wprowadzone we właściwościach są odzwierciedlane w oknie **Właściwości.**

### <a name="to-expose-tool-window-properties"></a>Aby udostępnić właściwości okna narzędzia

1. Otwórz *MyToolWindow.cs*i dodaj publiczną właściwość logiczną IsChecked do `MyToolWindow` klasy.

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

     Ta właściwość pobiera jego stan z WPF checkbox utworzysz później.

2. Otwórz *MyToolWindowControl.xaml.cs* i zastąp konstruktora MyToolWindowControl następującym kodem.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Daje `MyToolWindowControl` to dostęp `MyToolWindow` do okienka.

3. W *MyToolWindow.cs*zmień konstruktor w `MyToolWindow` następujący sposób:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Zmień widok projektu MyToolWindowControl.

5. Usuń przycisk i dodaj pole wyboru z **przybornika** do lewego górnego rogu.

6. Dodaj zdarzenia zaznaczone i niesprawdzone. Zaznacz pole wyboru w widoku projektu. W oknie **Właściwości** kliknij przycisk obsługi zdarzeń (w prawym górnym rogu okna **Właściwości).** Znajdź **pole tekstowe Pole zaznaczone** i wpisz **checkbox_Checked,** a następnie znajdź **pozycję Niezaznaczone** i wpisz **checkbox_Unchecked** w polu tekstowym.

7. Dodaj pole obsługi zdarzeń pola wyboru:

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

8. Skompiluj projekt i rozpocznij debugowanie.

9. W wystąpieniu eksperymentalnym otwórz okno **MyToolWindow.**

     Poszukaj właściwości okna w oknie **Właściwości.** **Właściwość IsChecked** pojawia się w dolnej części okna w kategorii **Moje właściwości.**

10. Zaznacz pole wyboru w oknie **MyToolWindow.** **Czysprawdzone** w oknie **Właściwości** zmienia się na **True**. Wyczyść pole wyboru w oknie **MyToolWindow.** **Czysprawdzone** w oknie **Właściwości** zmienia się na **Fałsz**. Zmień wartość **IsChecked** w oknie **Właściwości.** Pole wyboru w oknie **MyToolWindow** zmienia się, aby dopasować nową wartość.

    > [!NOTE]
    > Jeśli należy usunąć obiekt, który jest wyświetlany w oknie `OnSelectChange` **Właściwości,** najpierw wywołaj z kontenerem `null` wyboru. Po usunięciu właściwości lub obiektu można zmienić na kontener <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> zaznaczenia, który został zaktualizowany i wyświetla listę.

## <a name="change-selection-lists"></a>Zmienianie list wyboru

 W tej sekcji należy dodać listę wyboru dla klasy właściwości podstawowej i użyć interfejsu okna narzędzia, aby wybrać listę wyboru do wyświetlenia.

### <a name="to-change-selection-lists"></a>Aby zmienić listy wyboru

1. Otwórz *MyToolWindow.cs* i dodaj klasę `Simple`publiczną o nazwie .

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

2. Dodaj `SimpleObject` właściwość `MyToolWindow` do klasy oraz dwie metody przełączania wyboru okna **Właściwości** `Simple` między okienkiem okna a obiektem.

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

3. W *MyToolWindowControl.cs*zastąp programy obsługi pola wyboru tymi wierszami kodu:

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

4. Skompiluj projekt i rozpocznij debugowanie.

5. W wystąpieniu eksperymentalnym otwórz okno **MyToolWindow.**

6. Zaznacz pole wyboru w oknie **MyToolWindow.** Okno **Właściwości** wyświetla `Simple` właściwości obiektu, **SomeText** i **ReadOnly**. Wyczyść to pole wyboru. Właściwości publiczne okna są wyświetlane w oknie **Właściwości.**

    > [!NOTE]
    > Wyświetlana nazwa **SomeText** to **Mój tekst**.

## <a name="best-practice"></a>Najlepsze rozwiązania

W tym instruktażu jest zaimplementowana tak, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> aby kolekcja obiektów do wyboru i kolekcja wybranych obiektów były tej samej kolekcji. Na liście Przeglądarka właściwości pojawi się tylko zaznaczony obiekt. Aby uzyskać bardziej kompletną implementację ISelectionContainer, zobacz Reference.ToolWindow przykłady.

Okna narzędzia programu Visual Studio utrzymują się między sesjami programu Visual Studio. Aby uzyskać więcej informacji na temat <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>utrwalania stanu okna narzędzia, zobacz .

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie właściwości i okna Właściwość](../extensibility/extending-properties-and-the-property-window.md)
