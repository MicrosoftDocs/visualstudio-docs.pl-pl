---
title: Wprowadzenie do WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b33c558187fd32ef7cbd420dce8d627ddc944d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664337"
---
# <a name="introduction-to-wpf"></a>Wprowadzenie do WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Presentation Foundation (WPF) umożliwia tworzenie aplikacji klienckich dla komputerów z systemem Windows przy użyciu wizualnie atrakcyjnych środowisk użytkownika.

 ![Przykład interfejsu użytkownika dla opieki zdrowotnej firmy Contoso](../designers/media/wpfintrofigure24.png "WPFIntroFigure24")

 Rdzeń WPF to mechanizm renderowania niezależny od rozdzielczości i oparty na wektorach, który jest zbudowany w celu wykorzystania nowoczesnego sprzętu graficznego. WPF rozszerza rdzeń z kompleksowym zestawem funkcji programistycznych aplikacji, które obejmują Extensible Application Markup Language (XAML), kontrolki, powiązanie danych, układ, 2-D i trójwymiarowe grafiki, animacje, style, szablony, dokumenty, multimedia, tekst i Typografia. Funkcja WPF jest dołączona do .NET Framework, dzięki czemu można tworzyć aplikacje, które zawierają inne elementy biblioteki klas .NET Framework.

 Ten przegląd jest przeznaczony dla nowych elementów i obejmuje kluczowe możliwości i koncepcje WPF.

## <a name="programming-with-wpf"></a><a name="Programming_with_WPF"></a> Programowanie przy użyciu WPF
 WPF istnieje jako podzbiór typów .NET Framework, które są dla większości części znajdujących się w <xref:System.Windows> przestrzeni nazw. Jeśli wcześniej skompilowano aplikacje z .NET Framework przy użyciu technologii zarządzanych, takich jak ASP.NET i Windows Forms, podstawowe środowisko programistyczne WPF powinno być znane. Tworzenie wystąpień klas, Ustawianie właściwości, metody wywoływania i obsługa zdarzeń jest możliwe przy użyciu ulubionego języka programowania .NET, takiego jak C# lub Visual Basic.

 WPF zawiera dodatkowe konstrukcje programistyczne, które rozszerzają właściwości i zdarzenia: [właściwości zależności](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx) i [zdarzenia kierowane](https://msdn.microsoft.com/library/ms742806\(v=vs.100\).aspx).

## <a name="markup-and-code-behind"></a><a name="Markup_And_Codebehind"></a> Znaczniki i kod w tle
 WPF umożliwia tworzenie aplikacji przy użyciu *znaczników* i *kodu*, które są dostępne dla deweloperów ASP.NET. Zwykle używasz znacznika XAML do zaimplementowania wyglądu aplikacji przy użyciu zarządzanych języków programowania (związanych z kodem), aby zaimplementować jego zachowanie. Takie rozdzielenie wyglądu i zachowania ma następujące zalety:

- Koszty związane z programowaniem i konserwacją są ograniczone, ponieważ znaczniki specyficzne dla wyglądu nie są ściśle powiązane z kodem specyficznym dla zachowania.

- Programowanie jest wydajniejsze, ponieważ projektanci mogą zaimplementować wygląd aplikacji jednocześnie dla deweloperów, którzy implementują zachowanie aplikacji.

- [Globalizacja i lokalizacja](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx) dla aplikacji WPF jest uproszczona.

  Poniżej przedstawiono krótkie wprowadzenie do znaczników i kodu WPF.

### <a name="markup"></a>Znaczniki
 XAML jest językiem znaczników opartym na języku XML, który służy do deklaratywnego implementowania wyglądu aplikacji. Jest zazwyczaj używany do tworzenia okien, okien dialogowych, stron i kontrolek użytkownika oraz do wypełniania kontrolk, kształtów i grafiki.

 Poniższy przykład używa języka XAML do zaimplementowania wyglądu okna zawierającego pojedynczy przycisk.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

 W tym języku XAML definiuje okno i przycisk przy użyciu `Window` `Button` odpowiednio elementów i. Każdy element jest skonfigurowany z atrybutami, takimi jak `Window` atrybut elementu, `Title` Aby określić tekst paska tytułu okna. W czasie wykonywania WPF konwertuje elementy i atrybuty, które są zdefiniowane w znacznikach do wystąpień klas WPF. Na przykład `Window` element jest konwertowany na wystąpienie <xref:System.Windows.Window> klasy, której <xref:System.Windows.Window.Title%2A> Właściwość jest wartością `Title` atrybutu.

 Na poniższej ilustracji przedstawiono interfejs użytkownika, który jest definiowany przez kod XAML w poprzednim przykładzie.

 ![Okno zawierające przycisk](../designers/media/wpfintrofigure10.png "WPFIntroFigure10")

 Ponieważ XAML jest oparty na języku XML, tworzony przez siebie interfejs użytkownika jest montowany w hierarchii elementów zagnieżdżonych znanych jako [drzewo elementów](https://msdn.microsoft.com/library/ms753391\(v=vs.100\).aspx). Drzewo elementu zawiera logiczny i intuicyjny sposób tworzenia interfejsów użytkownika i zarządzania nimi.

### <a name="code-behind"></a>Związane z kodem
 Głównym zachowaniem aplikacji jest zaimplementowanie funkcji, która reaguje na interakcje użytkowników, w tym obsługę zdarzeń (na przykład kliknięcie menu, paska narzędzi lub przycisku) i wywołanie logiki biznesowej i logiki dostępu do danych w odpowiedzi. W WPF to zachowanie jest zazwyczaj zaimplementowane w kodzie, który jest skojarzony ze znacznikiem. Ten typ kodu jest znany jako kod. Poniższy przykład pokazuje zaktualizowany znacznik z poprzedniego przykładu i kodu.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox 

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI 
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI 
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub 

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub 

    End Class 

End Namespace

```

 W tym przykładzie w kodzie jest implementowana Klasa, która pochodzi od <xref:System.Windows.Window> klasy. Ten `x:Class` atrybut służy do kojarzenia znacznika z klasą związaną z kodem. `InitializeComponent` jest wywoływany z konstruktora klasy związanej z kodem, aby scalić interfejs użytkownika, który jest zdefiniowany w adjustacji z klasą powiązanymi z kodem. ( `InitializeComponent` jest generowany podczas tworzenia aplikacji, co oznacza, że nie trzeba jej zaimplementować ręcznie). Kombinacja `x:Class` i upewnij się `InitializeComponent` , że implementacja została prawidłowo zainicjowana za każdym razem, gdy zostanie utworzona. Klasa związany z kodem także implementuje procedurę obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia przycisku. Gdy przycisk zostanie kliknięty, program obsługi zdarzeń wyświetli okno komunikatu, wywołując <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> metodę.

 Poniższy rysunek przedstawia wynik po kliknięciu przycisku.

 ![Element MessageBox](../designers/media/wpfintrofigure25.png "WPFIntroFigure25")

## <a name="controls"></a><a name="Controls"></a> Kontrolek
 Środowiska użytkownika, które są dostarczane przez model aplikacji, są konstruowanymi kontrolkami. W WPF "Control" to termin, który ma zastosowanie do kategorii klas WPF, które są hostowane w oknie lub na stronie, mają interfejs użytkownika i implementuje pewne zachowanie.

 Aby uzyskać więcej informacji, zobacz [Controls](https://msdn.microsoft.com/library/3f255a8a-35a8-4712-9065-472ff7d75599).

### <a name="wpf-controls-by-function"></a>Formanty WPF według funkcji
 Wbudowane kontrolki WPF są wymienione tutaj.

- **Przyciski**: <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Primitives.RepeatButton> .

- **Wyświetlanie danych**: <xref:System.Windows.Controls.DataGrid> , <xref:System.Windows.Controls.ListView> , i <xref:System.Windows.Controls.TreeView> .

- **Wyświetlanie i wybór daty**: <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker> .

- **Okna dialogowe**: <xref:Microsoft.Win32.OpenFileDialog> , <xref:System.Windows.Controls.PrintDialog> i <xref:Microsoft.Win32.SaveFileDialog> .

- **Cyfrowy atrament**: <xref:System.Windows.Controls.InkCanvas> i <xref:System.Windows.Controls.InkPresenter> .

- **Dokumenty**: <xref:System.Windows.Controls.DocumentViewer> , <xref:System.Windows.Controls.FlowDocumentPageViewer> , <xref:System.Windows.Controls.FlowDocumentReader> , <xref:System.Windows.Controls.FlowDocumentScrollViewer> i <xref:System.Windows.Controls.StickyNoteControl> .

- **Dane wejściowe**: <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.RichTextBox> i <xref:System.Windows.Controls.PasswordBox> .

- **Układ**:,,,,,,,,, <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Primitives.BulletDecorator> <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.GridSplitter> <xref:System.Windows.Controls.GroupBox> <xref:System.Windows.Controls.Panel> , <xref:System.Windows.Controls.Primitives.ResizeGrip> , <xref:System.Windows.Controls.Separator> , <xref:System.Windows.Controls.Primitives.ScrollBar> , <xref:System.Windows.Controls.ScrollViewer> , <xref:System.Windows.Controls.StackPanel> , <xref:System.Windows.Controls.Primitives.Thumb> , <xref:System.Windows.Controls.Viewbox> , <xref:System.Windows.Controls.VirtualizingStackPanel> , <xref:System.Windows.Window> i <xref:System.Windows.Controls.WrapPanel> .

- **Nośniki**: <xref:System.Windows.Controls.Image> , <xref:System.Windows.Controls.MediaElement> , i <xref:System.Windows.Controls.SoundPlayerAction> .

- **Menu**: <xref:System.Windows.Controls.ContextMenu> , <xref:System.Windows.Controls.Menu> , i <xref:System.Windows.Controls.ToolBar> .

- **Nawigacja**: <xref:System.Windows.Controls.Frame> , <xref:System.Windows.Documents.Hyperlink> , <xref:System.Windows.Controls.Page> , <xref:System.Windows.Navigation.NavigationWindow> , i <xref:System.Windows.Controls.TabControl> .

- **Wybór**: <xref:System.Windows.Controls.CheckBox> , <xref:System.Windows.Controls.ComboBox> , <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.RadioButton> , i <xref:System.Windows.Controls.Slider> .

- **Informacje o użytkowniku**:,,,,, <xref:System.Windows.Controls.AccessText> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.ProgressBar> <xref:System.Windows.Controls.Primitives.StatusBar> <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.ToolTip> .

## <a name="input-and-commanding"></a><a name="Input_And_Commanding"></a> Dane wejściowe i polecenia
 Kontrolki najczęściej wykrywają dane wejściowe użytkownika i reagują na nie. [System wprowadzania WPF](https://msdn.microsoft.com/library/ms754010\(v=vs.100\).aspx) używa zdarzeń bezpośrednich i kierowanych do obsługi wprowadzania tekstu, zarządzania fokusem i pozycjonowania myszy.

 Aplikacje często mają złożone wymagania wejściowe. WPF udostępnia [system poleceń](https://msdn.microsoft.com/library/ms752308\(v=vs.100\).aspx) , który oddziela działania wprowadzane przez użytkownika z kodu, który odpowiada na te akcje.

## <a name="layout"></a><a name="Layout"></a> Wyglądu
 Podczas tworzenia interfejsu użytkownika można rozmieścić kontrolki według lokalizacji i rozmiaru w celu utworzenia układu. Kluczowym wymaganiem dowolnego układu jest dostosowanie do zmian rozmiaru okna i ustawień wyświetlania. Zamiast wymuszania pisania kodu w celu dostosowania układu w tych okolicznościach, WPF udostępnia system układu pierwszej klasy.

 Podstawą układu systemu jest Pozycjonowanie względne, które zwiększa możliwość dostosowania do zmieniania okna i warunków wyświetlania. Ponadto system układu zarządza negocjacją między kontrolkami w celu określenia układu. Negocjowanie jest procesem dwuetapowym: najpierw formant informuje swój element nadrzędny o lokalizacji i rozmiarze wymaganym przez program. następnie element nadrzędny informuje o tym, jakie miejsce może mieć.

 System układu jest narażony na kontrolki podrzędne za pomocą podstawowych klas WPF. W przypadku typowych układów, takich jak siatki, układania i dokowania, WPF zawiera kilka kontrolek układu:

- <xref:System.Windows.Controls.Canvas>: Formanty podrzędne zapewniają własny układ.

- <xref:System.Windows.Controls.DockPanel>: Kontrolki podrzędne są wyrównane do krawędzi panelu.

- <xref:System.Windows.Controls.Grid>: Kontrolki podrzędne są pozycjonowane według wierszy i kolumn.

- <xref:System.Windows.Controls.StackPanel>: Kontrolki podrzędne są ułożone pionowo lub poziomo.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: Formanty podrzędne są zwirtualizowane i ułożone w jednym wierszu, który jest w poziomie lub w pionie.

- <xref:System.Windows.Controls.WrapPanel>: Formanty podrzędne są umieszczane w kolejności od lewej do prawej i zawijane do następnego wiersza, gdy istnieje więcej kontrolek w bieżącym wierszu niż zezwala na miejsce.

  Poniższy przykład używa <xref:System.Windows.Controls.DockPanel> do układania kilku <xref:System.Windows.Controls.TextBox> kontrolek.

  [!code-xml[IntroToWPFSnippets#LayoutMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/LayoutWindow.xaml#layoutmarkup)]

  <xref:System.Windows.Controls.DockPanel>Pozwala <xref:System.Windows.Controls.TextBox> formantom podrzędnym na poinformowanie o tym, jak je rozmieścić. W tym celu <xref:System.Windows.Controls.DockPanel> implementuje Właściwość implementującą <xref:System.Windows.Controls.DockPanel.Dock%2A> elementy podrzędne formantów, aby umożliwić każdemu z nich Określanie stylu dokowania.

> [!NOTE]
> Właściwość, która jest implementowana przez formant nadrzędny do użycia przez formanty podrzędne, jest konstrukcja WPF o nazwie [dołączona właściwość](https://msdn.microsoft.com/library/ms749011\(v=vs.100\).aspx).

 Poniższy rysunek przedstawia wynik znacznika XAML w poprzednim przykładzie.

 ![Strona DockPanel](../designers/media/wpfintrofigure11.png "WPFIntroFigure11")

## <a name="data-binding"></a><a name="Data_Binding"></a> Powiązanie danych
 Większość aplikacji jest tworzonych w celu zapewnienia użytkownikom możliwości wyświetlania i edytowania danych. W przypadku aplikacji WPF można przechowywać dane i uzyskiwać do nich dostęp za pomocą technologii, takich jak SQL Server i ADO .NET. Po uzyskaniu dostępu do danych i załadowaniu ich do zarządzanych obiektów aplikacji, rozpocznie się działanie dla aplikacji WPF. Zasadniczo obejmuje to dwie rzeczy:

1. Kopiowanie danych z zarządzanych obiektów do kontrolek, w których można wyświetlać i edytować dane.

2. Zagwarantowanie, że zmiany wprowadzone do danych za pomocą kontrolek są kopiowane z powrotem do obiektów zarządzanych.

   Aby uprościć tworzenie aplikacji, funkcja WPF udostępnia aparat powiązań danych w celu automatycznego wykonania tych kroków. Jednostką podstawową aparatu powiązań danych jest <xref:System.Windows.Data.Binding> Klasa, której zadanie ma powiązać kontrolkę (obiekt docelowy powiązania) z obiektem danych (Źródło powiązania). Ta relacja jest zilustrowana na poniższej ilustracji.

   ![Podstawowy diagram powiązań danych](../designers/media/databindingmostbasic.png "DataBindingMostBasic")

   Poniższy przykład ilustruje sposób powiązania z <xref:System.Windows.Controls.TextBox> wystąpieniem `Person` obiektu niestandardowego. `Person`Implementacja jest pokazana w poniższym kodzie.

   [!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/Person.cs#personclasscode)]
   [!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/Person.vb#personclasscode)]

   Następujące znaczniki wiążą <xref:System.Windows.Controls.TextBox> się z wystąpieniem `Person` obiektu niestandardowego.

   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP1](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup1)]
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP2](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup2)]
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP3](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup3)]

   [!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml.cs#databindingcodebehind)]
   [!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/DataBindingWindow.xaml.vb#databindingcodebehind)]

   W tym przykładzie `Person` Klasa jest tworzona w kodzie i jest ustawiana jako kontekst danych dla `DataBindingWindow` . W znaczniku <xref:System.Windows.Controls.TextBox.Text%2A> Właściwość <xref:System.Windows.Controls.TextBox> jest powiązana z `Person.Name` właściwością (przy użyciu `{Binding ... }` składni języka XAML ""). Ten kod XAML informuje WPF, aby powiązać <xref:System.Windows.Controls.TextBox> formant z `Person` obiektem, który jest przechowywany we <xref:System.Windows.FrameworkElement.DataContext%2A> Właściwości okna.

   Aparat powiązań danych WPF zapewnia dodatkową pomoc techniczną, która obejmuje walidację, sortowanie, filtrowanie i grupowanie. Ponadto powiązanie danych obsługuje używanie szablonów danych do tworzenia niestandardowego interfejsu użytkownika dla powiązanych danych, gdy interfejs użytkownika wyświetlany przez standardowe formanty WPF nie jest odpowiedni.

   Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx).

## <a name="graphics"></a><a name="Graphics"></a> Elementów
 WPF wprowadza bogaty, skalowalny i elastyczny zestaw funkcji graficznych, które mają następujące zalety:

- **Niezależna od rozdzielczości i grafika niezależna od urządzenia**. Podstawowa jednostka miary w systemie grafiki WPF to niezależna od urządzenia piksel, czyli 1/1/96 cala, niezależnie od rzeczywistej rozdzielczości ekranu, a także podstawą renderowania niezależną od rozdzielczości i niezależną od urządzenia. Każdy piksel niezależny od urządzenia automatycznie skaluje się w celu dopasowania do ustawienia DPI systemu, w którym jest renderowane.

- **Ulepszona precyzja**. System współrzędnych WPF jest mierzony przy użyciu liczb zmiennoprzecinkowych o podwójnej precyzji, a nie pojedynczej precyzji. Przekształcenia i wartości przejrzystości są również wyrażone jako podwójne precyzja. WPF obsługuje również szeroką gamę kolorów (scRGB) i zapewnia zintegrowaną obsługę zarządzania danymi wejściowymi z różnych przestrzeni kolorów.

- **Zaawansowana obsługa grafiki i animacji**. WPF upraszcza programowanie grafiki przez zarządzanie scenami animacji. nie trzeba martwić się o przetwarzanie sceny, pętle renderowania i interpolację liniową. Ponadto WPF zapewnia obsługę testowania trafień i pełną obsługę składania Alpha.

- **Przyspieszenie sprzętowe**. System grafiki WPF wykorzystuje sprzęt graficzny do zminimalizowania użycia procesora CPU.

### <a name="2-d-shapes"></a>Kształty 2-D
 WPF udostępnia bibliotekę wspólnych, rysowanych w wektorach kształtów 2-D, takich jak prostokąty i wielokropek, które są wyświetlane na poniższej ilustracji.

 ![Wielokropek i prostokąty](../designers/media/wpfintrofigure4.PNG "WPFIntroFigure4")

 Interesująca możliwość tworzenia kształtów to nie tylko do wyświetlania; kształty implementują wiele funkcji, których oczekujesz od kontrolek, w tym dane wejściowe z klawiatury i myszy. W poniższym przykładzie pokazano <xref:System.Windows.UIElement.MouseUp> zdarzenie, które jest <xref:System.Windows.Shapes.Ellipse> obsługiwane.

 [!code-xml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml#handleellipsemouseupeventmarkup)]

 [!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml.cs#handleellipsemouseupeventcodebehind)]
 [!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/EllipseEventHandlingWindow.xaml.vb#handleellipsemouseupeventcodebehind)]

 Na poniższej ilustracji przedstawiono, co jest generowane przez poprzedni kod.

 ![Okno z tekstem "&#33; wielokropka"](../designers/media/wpfintrofigure12.png "WPFIntroFigure12")

 Aby uzyskać więcej informacji, zobacz temat [kształty i podstawowe Rysowanie w programie WPF — Omówienie](https://msdn.microsoft.com/library/ms747393\(v=vs.100\).aspx).

### <a name="2-d-geometries"></a>Geometrie 2-D
 Kształty 2-D udostępniane przez WPF obejmują standardowy zestaw kształtów podstawowych. Jednak może być konieczne utworzenie niestandardowych kształtów w celu ułatwienia projektowania dostosowanego interfejsu użytkownika. W tym celu WPF udostępnia geometrie. Na poniższej ilustracji przedstawiono użycie geometrie do utworzenia niestandardowego kształtu, który może być rysowany bezpośrednio, używany jako pędzel lub używany do wycinania innych kształtów i kontrolek.

 <xref:System.Windows.Shapes.Path> obiekty mogą służyć do rysowania zamkniętych lub otwartych kształtów, wielu kształtów, a nawet kształtów zakrzywionych.

 <xref:System.Windows.Media.Geometry> obiekty mogą służyć do przycinania, testowania trafień i renderowania danych graficznych 2-D.

 ![Różne zastosowania ścieżki](../designers/media/wpfintrofigure5.PNG "WPFIntroFigure5")

 Aby uzyskać więcej informacji, zobacz [geometria — Omówienie](https://msdn.microsoft.com/library/ms751808\(v=vs.100\).aspx)

### <a name="2-d-effects"></a>Efekty 2-D
 Podzbiór możliwości WPF 2-D zawiera efekty wizualne, takie jak gradienty, mapy bitowe, rysunki, malowanie przy użyciu filmów wideo, rotacja, skalowanie i pochylanie. Są one osiągane przy użyciu pędzli; na poniższej ilustracji przedstawiono kilka przykładów.

 ![Ilustracja przedstawiająca różne pędzle](../designers/media/wpfintrofigure6.PNG "WPFIntroFigure6")

 Aby uzyskać więcej informacji, zobacz [Omówienie pędzli WPF](https://msdn.microsoft.com/library/aa970904\(v=vs.100\).aspx).

### <a name="3-d-rendering"></a>Renderowanie 3-D
 WPF obejmuje również funkcje renderowania 3-D, które integrują się z grafikami 2-d, umożliwiając tworzenie bardziej atrakcyjnych i interesujących interfejsów użytkownika. Na przykład na poniższej ilustracji przedstawiono obrazy 2-D renderowane na kształtach trójwymiarowych.

 ![Zrzut ekranu przedstawiający przykładowy Visual3D](../designers/media/wpfintrofigure13.png "WPFIntroFigure13")

 Aby uzyskać więcej informacji, zobacz temat [Omówienie grafiki trójwymiarowej](https://msdn.microsoft.com/library/ms747437\(v=vs.100\).aspx).

## <a name="animation"></a><a name="Animation"></a> Odtwarzania
 Obsługa animacji WPF pozwala zwiększyć, wstrząsać, obracać i zanikać kontrolki, aby tworzyć interesujące przejścia stron i nie tylko. Można animować większość klas WPF, nawet klas niestandardowych. Na poniższej ilustracji przedstawiono prostą animację w działaniu.

 ![Obrazy animowanego modułu](../designers/media/wpfintrofigure7.png "WPFIntroFigure7")

 Aby uzyskać więcej informacji, zobacz [Omówienie animacji](https://msdn.microsoft.com/library/ms752312\(v=vs.100\).aspx).

## <a name="media"></a><a name="Media"></a> Multimedialny
 Jednym ze sposobów przekazywania rozbudowanej zawartości jest użycie multimediów audiowizualnych. WPF zapewnia specjalną obsługę obrazów, wideo i audio.

### <a name="images"></a>Obrazy
 Obrazy są wspólne dla większości aplikacji, a WPF oferuje kilka sposobów ich używania. Na poniższej ilustracji przedstawiono interfejs użytkownika z polem listy zawierającym obrazy miniatur. Po wybraniu miniatury obraz zostanie wyświetlony w pełnym rozmiarze.

 ![Obrazy miniatur i obraz pełnego rozmiaru&#45;](../designers/media/wpfintrofigure8.PNG "WPFIntroFigure8")

 Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia obrazu](https://msdn.microsoft.com/library/ms748873\(v=vs.100\).aspx).

### <a name="video-and-audio"></a>Wideo i audio
 <xref:System.Windows.Controls.MediaElement>Kontrolka jest w stanie odtwarzać wideo i dźwięk, a jest wystarczająco elastyczna, aby była podstawą dla niestandardowego odtwarzacza multimedialnego. Poniższe oznakowanie XAML implementuje odtwarzacz multimedialny.

 [!code-xml[IntroToWPFSnippets#MediaElementMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/MediaElementWindow.xaml#mediaelementmarkup)]

 Okno na poniższej ilustracji pokazuje <xref:System.Windows.Controls.MediaElement> kontrolkę w akcji.

 ![Kontrolka MediaElement z dźwiękiem i wideo](../designers/media/wpfintrofigure1.png "WPFIntroFigure1")

 Aby uzyskać więcej informacji, zobacz [Omówienie grafiki, animacji i nośnika WPF](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx).

## <a name="text-and-typography"></a><a name="Text_and_Typography"></a> Tekst i Typografia
 Aby ułatwić renderowanie tekstu o wysokiej jakości, WPF oferuje następujące funkcje:

- Obsługa czcionek OpenType.

- Ulepszenia technologii ClearType.

- Wysoka wydajność, która wykorzystuje przyspieszenie sprzętowe.

- Integracja tekstu z multimediami, grafiką i animacją.

- Obsługa czcionek międzynarodowych i mechanizmów powrotu.

  Jako Demonstracja integracji tekstu z grafiką na poniższej ilustracji przedstawiono sposób stosowania dekoracji tekstu.

  ![Tekst z różnymi dekoracjami tekstu](../designers/media/wpfintrofigure23.png "WPFIntroFigure23")

  Aby uzyskać więcej informacji, zobacz [Typografia w Windows Presentation Foundation](https://msdn.microsoft.com/library/ms742190\(v=vs.100\).aspx).

## <a name="customizing-wpf-applications"></a><a name="WPF_Customization"></a> Dostosowywanie aplikacji WPF
 Do tego momentu zaobserwowano podstawowe bloki konstrukcyjne WPF na potrzeby tworzenia aplikacji. Model aplikacji jest używany do hostowania i dostarczania zawartości aplikacji, która składa się głównie z kontrolek. Aby uprościć rozmieszczenie formantów w interfejsie użytkownika i upewnić się, że rozmieszczenie jest zachowywane na początku zmian rozmiaru okna i ustawień wyświetlania, należy użyć systemu układu WPF. Ponieważ większość aplikacji pozwala użytkownikom na współdziałanie z danymi, należy użyć powiązania danych, aby zmniejszyć pracę integracji interfejsu użytkownika z danymi. Aby wzmocnić wygląd aplikacji, należy użyć kompleksowego zakresu grafiki, animacji i pomocy technicznej multimedialnej zapewnianej przez WPF.

 Często jednak podstawowe informacje nie są wystarczające do tworzenia naprawdę odrębnego i wizualnego środowiska użytkownika. Standardowe formanty WPF mogą nie zostać zintegrowane z żądanym wyglądem aplikacji. Dane mogą nie być wyświetlane w najbardziej efektywny sposób. Ogólne środowisko użytkownika aplikacji może nie być odpowiednie dla domyślnego wyglądu i sposobu działania motywów systemu Windows. Na wiele sposobów Technologia prezentacji wymaga rozszerzalności wizualizacji tak samo, jak w przypadku dowolnego innego rodzaju rozszerzalności.

 Z tego powodu WPF oferuje różne mechanizmy tworzenia unikatowych środowisk użytkowników, w tym bogaty model zawartości dla formantów, wyzwalaczy, szablonów formantów i danych, stylów, zasobów interfejsu użytkownika i motywów i karnacji.

### <a name="content-model"></a>Model zawartości
 Głównym celem większości formantów WPF jest wyświetlenie zawartości. W WPF typ i liczba elementów, które mogą stanowić zawartość kontrolki, jest określany jako *model zawartości*kontrolki. Niektóre kontrolki mogą zawierać pojedynczy element i typ zawartości; na przykład zawartość a <xref:System.Windows.Controls.TextBox> jest wartością ciągu, która jest przypisana do <xref:System.Windows.Controls.TextBox.Text%2A> właściwości. Poniższy przykład ustawia zawartość <xref:System.Windows.Controls.TextBox> .

 [!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup1)]
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup2)]
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup3)]

 Na poniższej ilustracji przedstawiono rezultat.

 ![Formant TextBox zawierający tekst.](../designers/media/wpfintrofigure21.png "WPFIntroFigure21")

 Inne kontrolki, jednak mogą zawierać wiele elementów różnych typów zawartości; zawartość obiektu <xref:System.Windows.Controls.Button> , określonego przez <xref:System.Windows.Controls.ContentControl.Content%2A> Właściwość, może zawierać różne elementy, takie jak kontrolki układu, tekst, obrazy i kształty. W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Button> zawartość obejmującą, a, a <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Border> i <xref:System.Windows.Controls.MediaElement> .

 [!code-xml[IntroToWPFSnippets#ButtonContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup1)]
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup2)]
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup3)]

 Na poniższej ilustracji przedstawiono zawartość tego przycisku.

 ![Przycisk, który zawiera wiele typów zawartości](../designers/media/wpfintrofigure22.png "WPFIntroFigure22")

 Aby uzyskać więcej informacji o rodzaju zawartości obsługiwanej przez różne kontrolki, zobacz artykuł [model zawartości WPF](https://msdn.microsoft.com/library/bb613548\(v=vs.100\).aspx).

### <a name="triggers"></a>Wyzwalacze
 Chociaż głównym celem znacznika języka XAML jest zaimplementowanie wyglądu aplikacji, można również użyć języka XAML do implementacji niektórych aspektów zachowania aplikacji. Przykładem jest użycie wyzwalaczy do zmiany wyglądu aplikacji w oparciu o Interakcje użytkownika. Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx).

### <a name="control-templates"></a>Szablony kontrolek
 Domyślne interfejsy użytkownika dla formantów WPF są zwykle zbudowane z innych formantów i kształtów. Na przykład <xref:System.Windows.Controls.Button> składa się z obu <xref:Microsoft.Windows.Themes.ButtonChrome> formantów i <xref:System.Windows.Controls.ContentPresenter> . <xref:Microsoft.Windows.Themes.ButtonChrome>Zapewnia standardowy wygląd przycisku, podczas gdy <xref:System.Windows.Controls.ContentPresenter> wyświetla zawartość przycisku, jak określono przez <xref:System.Windows.Controls.ContentControl.Content%2A> Właściwość.

 Czasami domyślny wygląd formantu może być incongruent z ogólnym wyglądem aplikacji. W takim przypadku można użyć, <xref:System.Windows.Controls.ControlTemplate> Aby zmienić wygląd interfejsu użytkownika kontrolki bez zmiany jego zawartości i zachowania.

 Na przykład poniższy przykład pokazuje, jak zmienić wygląd elementu przy <xref:System.Windows.Controls.Button> użyciu <xref:System.Windows.Controls.ControlTemplate> .

 [!code-xml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml#buttoncontroltemplatewindowmarkup)]

 [!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml.cs#buttoncontroltemplatewindowcodebehind)]
 [!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/ControlTemplateButtonWindow.xaml.vb#buttoncontroltemplatewindowcodebehind)]

 W tym przykładzie interfejs użytkownika przycisku domyślnego został zastąpiony <xref:System.Windows.Shapes.Ellipse> , który ma ciemne niebieskie obramowanie i jest wypełniany przy użyciu <xref:System.Windows.Media.RadialGradientBrush> . <xref:System.Windows.Controls.ContentPresenter>Kontrolka wyświetla zawartość <xref:System.Windows.Controls.Button> , "kliknij mnie!" Gdy <xref:System.Windows.Controls.Button> zostanie kliknięty, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie jest nadal wywoływane w ramach <xref:System.Windows.Controls.Button> domyślnego zachowania formantu. Wyniki są pokazane na poniższym rysunku.

 ![Przycisk eliptyczne i drugie okno](../designers/media/wpfintrofigure2.png "WPFIntroFigure2")

### <a name="data-templates"></a>Szablony danych
 Natomiast szablon kontrolki umożliwia określenie wyglądu kontrolki, szablon danych pozwala określić wygląd zawartości kontrolki. Szablony danych są często używane do ulepszania sposobu wyświetlania powiązanych danych. Na poniższej ilustracji przedstawiono domyślny wygląd dla elementu, <xref:System.Windows.Controls.ListBox> który jest powiązany z kolekcją `Task` obiektów, gdzie każde zadanie ma nazwę, opis i priorytet.

 ![Pole listy z wyglądem domyślnym](../designers/media/wpfintrofigure18.png "WPFIntroFigure18")

 Domyślnym wyglądem jest to, czego oczekujesz od <xref:System.Windows.Controls.ListBox> . Jednak domyślny wygląd każdego zadania zawiera tylko nazwę zadania. Aby wyświetlić nazwę, opis i priorytet zadania, <xref:System.Windows.Controls.ListBox> należy zmienić domyślny wygląd elementów listy powiązanej formantu przy użyciu <xref:System.Windows.DataTemplate> . Poniższy kod XAML definiuje takie <xref:System.Windows.DataTemplate> , który jest stosowany do każdego zadania przy użyciu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> atrybutu.

 [!code-xml[IntroToWPFSnippets#DataTemplateMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup1)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup2)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup3)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup4)]

 Poniższy rysunek przedstawia efekt tego kodu.

 ![Pole listy korzystające z szablonu danych](../designers/media/wpfintrofigure19.png "WPFIntroFigure19")

 Zwróć uwagę, że <xref:System.Windows.Controls.ListBox> zachowano swoje zachowanie i ogólny wygląd; tylko wygląd zawartości wyświetlanej w polu listy został zmieniony.

 Aby uzyskać więcej informacji, zobacz [tworzenia szablonów danych — omówienie](https://msdn.microsoft.com/library/ms742521\(v=vs.100\).aspx).

### <a name="styles"></a>Style
 Style umożliwiają deweloperom i projektantom ujednolicenie się z konkretnym wyglądem produktu. WPF oferuje model silnego stylu, podstawę, która jest <xref:System.Windows.Style> elementem. Poniższy przykład tworzy styl, który ustawia kolor tła dla każdego <xref:System.Windows.Controls.Button> w oknie do `Orange` .

 [!code-xml[IntroToWPFSnippets#StyleMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup1)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup2)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup3)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup4)]

 Ponieważ ten styl jest przeznaczony <xref:System.Windows.Controls.Button> dla wszystkich kontrolek, styl jest automatycznie stosowany do wszystkich przycisków w oknie, jak pokazano na poniższej ilustracji.

 ![Dwa pomarańczowe przyciski](../designers/media/wpfintrofigure20.png "WPFIntroFigure20")

 Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx).

### <a name="resources"></a>Zasoby
 Kontrolki w aplikacji powinny korzystać z tego samego wyglądu, które mogą zawierać dowolne elementy z czcionek i kolorów tła, które umożliwiają kontrolowanie szablonów, szablonów danych i stylów. Możesz użyć obsługi platformy WPF do zasobów interfejsu użytkownika, aby hermetyzować te zasoby w jednej lokalizacji do ponownego użycia.

 W poniższym przykładzie zdefiniowano typowy kolor tła, który jest udostępniany przez <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Label> .

 [!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup1)]
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup2)]
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup3)]

 Ten przykład implementuje zasób koloru tła za pomocą `Window.Resources` elementu właściwości. Ten zasób jest dostępny dla wszystkich elementów podrzędnych <xref:System.Windows.Window> . Istnieje wiele zakresów zasobów, w tym następujące, wymienione w kolejności, w jakiej zostały rozwiązane:

1. Indywidualny formant (przy użyciu dziedziczonej <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> Właściwości).

2. A <xref:System.Windows.Window> lub a <xref:System.Windows.Controls.Page> (również przy użyciu dziedziczonej <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> Właściwości).

3. <xref:System.Windows.Application>A (za pomocą <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> Właściwości).

   Różne zakresy zapewniają elastyczność w odniesieniu do sposobu definiowania i udostępniania zasobów.

   Alternatywnie do bezpośredniego kojarzenia zasobów z określonym zakresem, można spakować jeden lub więcej zasobów przy użyciu oddzielnego, do którego można <xref:System.Windows.ResourceDictionary> odwoływać się w innych częściach aplikacji. Na przykład poniższy przykład definiuje domyślny kolor tła w słowniku zasobów.

   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup1)]
   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup2)]

   Poniższy przykład odwołuje się do słownika zasobów zdefiniowanego w poprzednim przykładzie, tak aby był współużytkowany przez aplikację.

   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup1)]
   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup2)]

   Zasoby i słowniki zasobów są podstawą obsługi technologii WPF dla motywów i skórek.

   Aby uzyskać więcej informacji, zobacz [Omówienie zasobów](https://msdn.microsoft.com/library/ms750613\(v=vs.100\).aspx).

### <a name="custom-controls"></a>Formanty niestandardowe
 Mimo że WPF udostępnia obsługę dostosowywania, można napotkać sytuacje, w których istniejące formanty WPF nie spełniają wymagań aplikacji lub użytkowników. Może się tak zdarzyć, gdy:

- Nie można utworzyć wymaganego interfejsu użytkownika przez dostosowanie wyglądu i sposobu działania istniejących implementacji WPF.

- Wymagane zachowanie nie jest obsługiwane (lub nie jest obsługiwane w łatwy sposób) przez istniejące implementacje WPF.

  W tym momencie można jednak skorzystać z jednego z trzech modeli WPF, aby utworzyć nową kontrolkę. Każdy model jest przeznaczony dla określonego scenariusza i wymaga, aby formant niestandardowy dziedziczył od określonej klasy bazowej WPF. Trzy modele są wymienione tutaj:

- **Model kontroli użytkownika**. Kontrolka niestandardowa dziedziczy z <xref:System.Windows.Controls.UserControl> i składa się z co najmniej jednej innej kontrolki.

- **Model sterowania**. Kontrolka niestandardowa dziedziczy z <xref:System.Windows.Controls.Control> i służy do kompilowania implementacji, które oddzielają ich zachowanie od ich wyglądu przy użyciu szablonów, podobnie jak większość formantów WPF. Wyprowadzanie z programu <xref:System.Windows.Controls.Control> umożliwia większą swobodę tworzenia niestandardowego interfejsu użytkownika niż kontrolki użytkownika, ale może wymagać większego nakładu pracy.

- **Model elementu struktury**. Kontrolka niestandardowa pochodzi od <xref:System.Windows.FrameworkElement> momentu zdefiniowania jego wyglądu przy użyciu logiki renderowania niestandardowego (nie szablonów).

  Poniższy przykład przedstawia niestandardową kontrolkę Up/Down, która pochodzi od <xref:System.Windows.Controls.UserControl> .

  [!code-xml[IntroToWPFSnippets#UserControlMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml#usercontrolmarkup)]

  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind1)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind1)]
  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind2)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind2)]

 Następny przykład ilustruje kod XAML, który jest wymagany do włączenia kontrolki użytkownika do <xref:System.Windows.Window> .

 [!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup1)]
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup2)]
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup3)]

 Na poniższej ilustracji przedstawiono `NumericUpDown` kontrolkę hostowaną w elemencie <xref:System.Windows.Window> .

 ![Niestandardowy element UserControl](../designers/media/wpfintrofigure3.png "WPFIntroFigure3")

 Aby uzyskać więcej informacji na temat kontrolek niestandardowych, zobacz temat [Tworzenie kontroli — Omówienie](https://msdn.microsoft.com/library/ms745025\(v=vs.100\).aspx).

## <a name="wpf-best-practices"></a><a name="WPF_Best_Practices"></a> Najlepsze rozwiązania dotyczące WPF
 Podobnie jak w przypadku dowolnej platformy programistycznej, WPF można używać na wiele sposobów w celu osiągnięcia żądanego wyniku. W celu upewnienia się, że aplikacje WPF zapewniają wymagane środowisko użytkownika i są ogólnie zgodne z wymaganiami odbiorców, zalecane są najlepsze rozwiązania dotyczące ułatwień dostępu, globalizacji i lokalizacji oraz wydajności. Aby uzyskać więcej informacji, zobacz następujące informacje:

- [Najlepsze rozwiązania dotyczące ułatwień dostępu](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx) Najlepsze rozwiązania dotyczące ułatwień dostępu

- [Przegląd Lokalizacja i globalizacja WPF](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)

- [Optymalizacja wydajności aplikacji WPF](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)

- [Zabezpieczenia Windows Presentation Foundation](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)

## <a name="summary"></a><a name="Summary"></a> Podsumowanie
 WPF to kompleksowa Technologia prezentacji służąca do tworzenia różnorodnych wizualnie atrakcyjnych aplikacji klienckich. W tym wprowadzeniu przedstawiono najważniejsze funkcje platformy WPF.

 Następnym krokiem jest skompilowanie aplikacji WPF.

 Podczas kompilowania można wrócić do tego wprowadzenia, aby odświeżyć w najważniejszych funkcjach i znaleźć odwołania do bardziej szczegółowych informacji na temat funkcji uwzględnionych w tym wprowadzeniu.

## <a name="see-also"></a>Zobacz też
 [Wprowadzenie za pomocą platformy WPF](../designers/getting-started-with-wpf.md) [Twórz nowoczesne aplikacje klasyczne przy użyciu Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md) [Windows Presentation Foundation](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx)
