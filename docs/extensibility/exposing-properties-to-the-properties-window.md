---
title: Udostępnianie właściwości w oknie właściwości | Microsoft Docs
description: Dowiedz się więcej o właściwościach publicznych obiektu. Zmiany wprowadzone w tych właściwościach są odzwierciedlane w okno Właściwości.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5f932772b031332d7df2a2487c70576f49407ba1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898740"
---
# <a name="expose-properties-to-the-properties-window"></a>Uwidocznij właściwości okno Właściwości

Ten przewodnik uwidacznia publiczne właściwości obiektu w **oknie** Właściwości. Zmiany wprowadzone w tych właściwościach są odzwierciedlane w **oknie** Właściwości.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od Visual Studio 2015 r., zestaw SDK usługi Visual Studio nie jest instalowany z Centrum pobierania. Jest ona dołączona jako opcjonalna funkcja w Visual Studio konfiguracji. Zestaw VS SDK można również zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="expose-properties-to-the-properties-window"></a>Uwidocznij właściwości okno Właściwości

W tej sekcji utworzysz niestandardowe okno narzędzi i wyświetlisz właściwości publiczne skojarzonego obiektu okienka okna w **oknie** Właściwości.

### <a name="to-expose-properties-to-the-properties-window"></a>Aby uwidocznić właściwości okno Właściwości

1. Każde Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Utwórz projekt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX o nazwie `MyObjectPropertiesExtension` . Szablon projektu VSIX można znaleźć w **oknie dialogowym Nowy projekt,** wyszukując "vsix".

2. Dodaj okno narzędzi, dodając szablon elementu niestandardowego okna narzędzi o nazwie `MyToolWindow` . W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. W **oknie dialogowym Dodawanie nowego elementu** przejdź do pozycji Rozszerzalność elementów Visual **C#**  >   i wybierz pozycję Okno **narzędzi niestandardowych.** W polu **Nazwa** w dolnej części okna dialogowego zmień nazwę pliku na *MyToolWindow.cs.* Aby uzyskać więcej informacji na temat tworzenia niestandardowego okna narzędzi, zobacz [Create an extension with a tool window (Tworzenie rozszerzenia za pomocą okna narzędzi).](../extensibility/creating-an-extension-with-a-tool-window.md)

3. Otwórz *myToolWindow.cs* i dodaj następującą instrukcje using:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Teraz dodaj następujące pola do `MyToolWindow` klasy .

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Dodaj poniższy kod do klasy `MyToolWindow`.

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

    Właściwość `TrackSelection` używa właściwości w celu uzyskania `GetService` `STrackSelection` usługi, która udostępnia <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfejs. Procedura `OnToolWindowCreated` obsługi zdarzeń i metoda razem tworzą listę wybranych obiektów, które zawierają tylko sam obiekt `SelectList` okienka okna narzędzi. Metoda `UpdateSelection` informuje okno **Właściwości** o wyświetlaniu właściwości publicznych okienka okna narzędzi.

6. Skompilowanie projektu i rozpoczęcie debugowania. Powinno zostać wyświetlone eksperymentalne Visual Studio.

7. Jeśli okno **Właściwości** nie jest widoczne, otwórz je, naciskając **klawisz F4**.

8. Otwórz **okno MyToolWindow.** Można go znaleźć w widoku  >  **innych okien**.

    Zostanie otwarte okno, a właściwości publiczne okienka zostaną wyświetlone w **oknie** Właściwości.

9. Zmień właściwość **Caption** w **oknie Właściwości** na **Właściwości obiektu**.

     Podpis okna MyToolWindow odpowiednio się zmienia.

## <a name="expose-tool-window-properties"></a>Uwidocznij właściwości okna narzędzi

W tej sekcji dodasz okno narzędzia i uwidocznisz jego właściwości. Zmiany wprowadzone we właściwościach są odzwierciedlane w **oknie** Właściwości.

### <a name="to-expose-tool-window-properties"></a>Aby uwidocznić właściwości okna narzędzi

1. Otwórz *myToolWindow.cs* i dodaj do klasy publiczną właściwość logiczną IsChecked. `MyToolWindow`

    ```csharp
    [Category("My Properties")]
    [Description("MyToolWindowControl properties")]
    public bool IsChecked
    {
        get {
            if (base.Content == null)  return false;
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;
        }
        set {
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;
        }
    }
    ```

     Ta właściwość pobiera stan z pola wyboru WPF, które utworzysz później.

2. Otwórz *myToolWindowControl.xaml.cs* i zastąp konstruktor MyToolWindowControl następującym kodem.

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

3. W *myToolWindow.cs* zmień `MyToolWindow` konstruktor w następujący sposób:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Zmień widok projektu na MyToolWindowControl.

5. Usuń przycisk i dodaj pole wyboru w **przyborniku** w lewym górnym rogu.

6. Dodaj zdarzenia Checked (Zaznaczone) i Unchecked (Niezaznaczone). Zaznacz pole wyboru w widoku projektu. W **oknie** Właściwości kliknij przycisk procedury obsługi zdarzeń (w prawym górnym rogu **okna** Właściwości). Znajdź **pole Wyboru** **checkbox_Checked** wpisz w polu tekstowym, a następnie znajdź pozycję Niezaznaczone i **wpisz checkbox_Unchecked** w polu tekstowym. 

7. Dodaj procedury obsługi zdarzeń pola wyboru:

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

8. Skompilowanie projektu i rozpoczęcie debugowania.

9. W wystąpieniu eksperymentalnym otwórz okno **MyToolWindow.**

     Poszukaj właściwości okna w **oknie** Właściwości. Właściwość **IsChecked jest** wyświetlana w dolnej części okna w kategorii **Moje** właściwości.

10. Zaznacz pole wyboru w oknie **MyToolWindow.** **Wartość IsChecked w** **oknie Właściwości** zmieni się na **True**. Wyczyść pole wyboru w oknie **MyToolWindow.** **Wartość IsChecked w** **oknie Właściwości** zmieni się na **False**. Zmień wartość **IsChecked w** **oknie** Właściwości. Pole wyboru w oknie **MyToolWindow** zmieni się tak, aby dopasować nową wartość.

    > [!NOTE]
    > Jeśli musisz usunąć obiekt wyświetlany w oknie **Właściwości,** najpierw wywołaj element `OnSelectChange` z `null` kontenerem wyboru. Po rozdysponowyniu właściwości lub obiektu można przejść do kontenera wyboru, który ma zaktualizowane <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> listy <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> i .

## <a name="change-selection-lists"></a>Zmienianie list wyboru

 W tej sekcji dodasz listę wyboru dla podstawowej klasy właściwości i użyjesz interfejsu okna narzędzi, aby wybrać listę wyboru do wyświetlenia.

### <a name="to-change-selection-lists"></a>Aby zmienić listy wyboru

1. Otwórz *myToolWindow.cs* i dodaj klasę publiczną o nazwie `Simple` .

    ```csharp
    public class Simple
    {
        private string someText = "";

        [Category("My Properties")]
        [Description("Simple Properties")]
        [DisplayName("My Text")]
        public string SomeText
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

2. Dodaj właściwość do klasy oraz dwie metody przełączania wyboru okna `SimpleObject` `MyToolWindow` Właściwości między okienkiem okna a  `Simple` obiektem.

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

3. W *pliku MyToolWindowControl.cs* zastąp programy obsługi pola wyboru tymi liniami kodu:

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

4. Skompilowanie projektu i rozpoczęcie debugowania.

5. W wystąpieniu eksperymentalnym otwórz okno **MyToolWindow.**

6. Zaznacz pole wyboru w oknie **MyToolWindow.** W **oknie** Właściwości są `Simple` wyświetlane właściwości obiektu **SomeText** i **ReadOnly.** Wyczyść pole wyboru. Właściwości publiczne okna zostaną wyświetlone w **oknie** Właściwości.

    > [!NOTE]
    > Nazwa wyświetlana aplikacji **SomeText** to **My Text**.

## <a name="best-practice"></a>Najlepsze rozwiązanie

W tym przewodniku jest implementowane tak, aby kolekcja obiektów do wyboru i kolekcja wybranych <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiektów była tą samą kolekcją. Na liście Przeglądarka właściwości jest wyświetlany tylko wybrany obiekt. Aby uzyskać bardziej kompletną implementację ISelectionContainer, zobacz przykłady Reference.ToolWindow.

Visual Studio narzędzi są utrwalane między Visual Studio sesji. Aby uzyskać więcej informacji na temat utrwalania stanu okna narzędzia, zobacz <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie właściwości i okno Właściwości](../extensibility/extending-properties-and-the-property-window.md)
