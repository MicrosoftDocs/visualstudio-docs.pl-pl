---
title: Wprowadzenie do WPF
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- csharp
- vb
ms.workload:
- multiple
ms.openlocfilehash: f26558a8e8d7e8446e3a992b7555116b5712c364
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924455"
---
# <a name="wpf-overview"></a>Omówienie podsystemu WPF

Windows Presentation Foundation (WPF) umożliwia tworzenie aplikacji klienckich dla komputerów z systemem Windows przy użyciu wizualnie atrakcyjnych środowisk użytkownika.

![Przykład interfejsu użytkownika dla opieki zdrowotnej firmy Contoso](../designers/media/wpfintrofigure24.png)

Rdzeń WPF to mechanizm renderowania niezależny od rozdzielczości i oparty na wektorach, który jest zbudowany w celu wykorzystania nowoczesnego sprzętu graficznego. WPF rozszerza rdzeń z kompleksowym zestawem funkcji programistycznych dla aplikacji, które obejmują Extensible Application Markup Language (XAML), kontrolki, powiązanie danych, układ, grafiki 2D i 3D, animacje, style, szablony, dokumenty, multimedia, tekst i typografii. WPF jest częścią platformy .NET, dzięki czemu można tworzyć aplikacje, które zawierają inne elementy interfejsu API platformy .NET.

Ten przegląd jest przeznaczony dla nowych elementów i obejmuje kluczowe możliwości i koncepcje WPF.

## <a name="program-with-wpf"></a>Program z WPF

WPF istnieje jako podzbiór typów .NET, które są (dla większości części) znajdujących się w <xref:System.Windows> przestrzeni nazw. Jeśli wcześniej skompilowano aplikacje z platformą .NET przy użyciu technologii zarządzanych, takich jak ASP.NET i Windows Forms, podstawowe środowisko programistyczne WPF powinno być znane. Tworzenie wystąpień klas, Ustawianie właściwości, metody wywoływania i obsługa zdarzeń przy użyciu ulubionego języka programowania .NET, takiego jak C# lub Visual Basic.

WPF zawiera dodatkowe konstrukcje programistyczne, które rozszerzają właściwości i zdarzenia: [właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview) i [zdarzenia kierowane](/dotnet/framework/wpf/advanced/routed-events-overview).

## <a name="markup-and-code-behind"></a>Znaczniki i kod w tle

WPF umożliwia tworzenie aplikacji przy użyciu zarówno *znaczników* , jak i *kodu*, dzięki czemu deweloperzy ASP.NET powinni znać. Zwykle używasz znacznika XAML do zaimplementowania wyglądu aplikacji przy użyciu zarządzanych języków programowania (związanych z kodem), aby zaimplementować jego zachowanie. Takie rozdzielenie wyglądu i zachowania ma następujące zalety:

- Koszty związane z programowaniem i konserwacją są ograniczone, ponieważ znaczniki specyficzne dla wyglądu nie są ściśle powiązane z kodem specyficznym dla zachowania.

- Programowanie jest wydajniejsze, ponieważ projektanci mogą zaimplementować wygląd aplikacji jednocześnie dla deweloperów, którzy implementują zachowanie aplikacji.

- [Globalizacja i lokalizacja](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview) dla aplikacji WPF jest uproszczona.

### <a name="markup"></a>Komórka

XAML jest językiem znaczników opartym na języku XML, który implementuje wygląd aplikacji deklaratywnie. Zwykle jest ona używana do tworzenia okien, okien dialogowych, stron i kontrolek użytkownika oraz do wypełniania formantów, kształtów i grafiki.

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

W tym języku XAML definiuje okno i przycisk przy użyciu `Window` odpowiednio elementów i. `Button` Każdy element jest skonfigurowany z atrybutami, takimi `Window` jak `Title` atrybut elementu, aby określić tekst paska tytułu okna. W czasie wykonywania WPF konwertuje elementy i atrybuty, które są zdefiniowane w znacznikach do wystąpień klas WPF. Na przykład `Window` element jest konwertowany na wystąpienie klasy, <xref:System.Windows.Window> której <xref:System.Windows.Window.Title%2A> właściwość jest wartością `Title` atrybutu.

Na poniższej ilustracji przedstawiono interfejs użytkownika, który jest definiowany przez kod XAML w poprzednim przykładzie.

![Okno zawierające przycisk](../designers/media/wpfintrofigure10.png)

Ponieważ XAML jest oparty na języku XML, tworzony przez siebie interfejs użytkownika jest montowany w hierarchii elementów zagnieżdżonych znanych jako [drzewo elementów](/dotnet/framework/wpf/advanced/trees-in-wpf). Drzewo elementu zawiera logiczny i intuicyjny sposób tworzenia interfejsów użytkownika i zarządzania nimi.

### <a name="code-behind"></a>Związane z kodem

Głównym zachowaniem aplikacji jest zaimplementowanie funkcji, która reaguje na interakcje użytkowników, w tym obsługę zdarzeń (na przykład kliknięcie menu, paska narzędzi lub przycisku) i wywołanie logiki biznesowej i logiki dostępu do danych w odpowiedzi. W WPF to zachowanie jest zaimplementowane w kodzie, który jest skojarzony ze znacznikiem. Ten typ kodu jest znany jako kod. Poniższy przykład pokazuje zaktualizowany znacznik z poprzedniego przykładu i kodu.

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

W tym przykładzie w kodzie jest implementowana Klasa, która pochodzi od <xref:System.Windows.Window> klasy. Ten `x:Class` atrybut służy do kojarzenia znacznika z klasą związaną z kodem. `InitializeComponent`jest wywoływany z konstruktora klasy związanej z kodem, aby scalić interfejs użytkownika, który jest zdefiniowany w adjustacji z klasą powiązanymi z kodem. (`InitializeComponent` jest generowany podczas tworzenia aplikacji, co oznacza, że nie trzeba jej zaimplementować ręcznie). Kombinacja `x:Class` i`InitializeComponent` upewnij się, że implementacja została prawidłowo zainicjowana za każdym razem, gdy zostanie utworzona. Klasa związany z kodem także implementuje procedurę obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia przycisku. Gdy przycisk zostanie kliknięty, program obsługi zdarzeń wyświetli okno komunikatu, wywołując <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> metodę.

Poniższy rysunek przedstawia wynik po kliknięciu przycisku.

![Element MessageBox](../designers/media/wpfintrofigure25.png)

## <a name="controls"></a>Formanty

Środowiska użytkownika, które są dostarczane przez model aplikacji, są konstruowanymi kontrolkami. W WPF *Kontrola* jest terminem parasol, który ma zastosowanie do kategorii klas WPF, które są hostowane w oknie lub na stronie, mają interfejs użytkownika i implementuje pewne zachowanie.

Aby uzyskać więcej informacji, [](/dotnet/framework/wpf/controls/index)Zobacz Controls.

### <a name="wpf-controls-by-function"></a>Formanty WPF według funkcji

Wbudowane kontrolki WPF są wymienione tutaj.

- **Przyciski**: <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Primitives.RepeatButton>.

- **Wyświetlanie danych**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, i <xref:System.Windows.Controls.TreeView>.

- **Wyświetlanie i wybór daty**: <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker>.

- **Okna dialogowe**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>i. <xref:Microsoft.Win32.SaveFileDialog>

- **Cyfrowy atrament**: <xref:System.Windows.Controls.InkCanvas> i <xref:System.Windows.Controls.InkPresenter>.

- **Dokumenty**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader> ,i<xref:System.Windows.Controls.StickyNoteControl>. <xref:System.Windows.Controls.FlowDocumentScrollViewer>

- **Dane wejściowe** <xref:System.Windows.Controls.TextBox>: <xref:System.Windows.Controls.RichTextBox>, i <xref:System.Windows.Controls.PasswordBox>.

- **Układ**: <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Primitives.BulletDecorator> ,<xref:System.Windows.Controls.Canvas>, ,<xref:System.Windows.Controls.GridView>,,,,,, ,<xref:System.Windows.Controls.Primitives.ResizeGrip>, ,<xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.GridSplitter> <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.GroupBox> <xref:System.Windows.Controls.Primitives.ScrollBar>  <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, ,,<xref:System.Windows.Controls.Primitives.Thumb>, i .<xref:System.Windows.Controls.WrapPanel> <xref:System.Windows.Controls.Viewbox> <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Window>

- Nośniki <xref:System.Windows.Controls.Image>: <xref:System.Windows.Controls.MediaElement>,, <xref:System.Windows.Controls.SoundPlayerAction>i.

- **Menu**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, i <xref:System.Windows.Controls.ToolBar>.

- **Nawigacja**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, ,<xref:System.Windows.Controls.Page>, i<xref:System.Windows.Controls.TabControl>. <xref:System.Windows.Navigation.NavigationWindow>

- **Wybór**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, ,<xref:System.Windows.Controls.ListBox>, i<xref:System.Windows.Controls.Slider>. <xref:System.Windows.Controls.RadioButton>

- **Informacje o**użytkowniku <xref:System.Windows.Controls.Label>: <xref:System.Windows.Controls.Primitives.Popup> ,,<xref:System.Windows.Controls.ProgressBar>,,, i<xref:System.Windows.Controls.ToolTip>. <xref:System.Windows.Controls.AccessText> <xref:System.Windows.Controls.Primitives.StatusBar> <xref:System.Windows.Controls.TextBlock>

## <a name="input-and-commands"></a>Dane wejściowe i polecenia

Kontrolki najczęściej wykrywają dane wejściowe użytkownika i reagują na nie. [System wprowadzania WPF](/dotnet/framework/wpf/advanced/input-overview) używa zdarzeń bezpośrednich i kierowanych do obsługi wprowadzania tekstu, zarządzania fokusem i pozycjonowania myszy.

Aplikacje często mają złożone wymagania wejściowe. WPF udostępnia [system poleceń](/dotnet/framework/wpf/advanced/commanding-overview) , który oddziela działania wprowadzane przez użytkownika od kodu, który odpowiada na te akcje.

## <a name="layout"></a>Układ

Podczas tworzenia interfejsu użytkownika można rozmieścić kontrolki według lokalizacji i rozmiaru w celu utworzenia układu. Kluczowym wymaganiem dowolnego układu jest dostosowanie do zmian rozmiaru okna i ustawień wyświetlania. Zamiast wymuszania pisania kodu w celu dostosowania układu w tych okolicznościach, WPF udostępnia system układu pierwszej klasy.

Podstawą układu systemu jest Pozycjonowanie względne, które zwiększa możliwość dostosowania do zmieniania okna i warunków wyświetlania. Ponadto system układu zarządza negocjacją między kontrolkami w celu określenia układu. Negocjowanie jest procesem dwuetapowym: najpierw formant informuje swój element nadrzędny o lokalizacji i rozmiarze wymaganym przez program. następnie element nadrzędny informuje o tym, jakie miejsce może mieć.

System układu jest narażony na kontrolki podrzędne za pomocą podstawowych klas WPF. W przypadku typowych układów, takich jak siatki, układania i dokowania, WPF zawiera kilka kontrolek układu:

- <xref:System.Windows.Controls.Canvas>: Formanty podrzędne zapewniają własny układ.

- <xref:System.Windows.Controls.DockPanel>: Kontrolki podrzędne są wyrównane do krawędzi panelu.

- <xref:System.Windows.Controls.Grid>: Formanty podrzędne są rozmieszczone według wierszy i kolumn.

- <xref:System.Windows.Controls.StackPanel>: Kontrolki podrzędne są ułożone pionowo lub poziomo.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: Formanty podrzędne są zwirtualizowane i ułożone w jednym wierszu, który jest w poziomie lub w pionie.

- <xref:System.Windows.Controls.WrapPanel>: Formanty podrzędne są umieszczane w kolejności od lewej do prawej i zawijane do następnego wiersza, gdy istnieje więcej kontrolek w bieżącym wierszu niż zezwala na miejsce.

Poniższy przykład używa <xref:System.Windows.Controls.DockPanel> do układania kilku <xref:System.Windows.Controls.TextBox> kontrolek.

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_1.xaml)]

Pozwala formantom podrzędnym <xref:System.Windows.Controls.TextBox> na poinformowanie o tym, jak je rozmieścić. <xref:System.Windows.Controls.DockPanel> W tym celu `Dock` implementujezałączonąwłaściwość,którajestudostępnionakontrolkompodrzędnym,abyumożliwićkażdemuznichOkreślaniestyludokowania.<xref:System.Windows.Controls.DockPanel>

> [!NOTE]
> Właściwość, która jest implementowana przez formant nadrzędny do użycia przez formanty podrzędne, jest konstrukcja WPF o nazwie [dołączona właściwość](/dotnet/framework/wpf/advanced/attached-properties-overview).

Poniższy rysunek przedstawia wynik znacznika XAML w poprzednim przykładzie.

![Strona DockPanel](../designers/media/wpfintrofigure11.png)

## <a name="data-binding"></a>Powiązanie danych

Większość aplikacji jest tworzonych w celu zapewnienia użytkownikom możliwości wyświetlania i edytowania danych. W przypadku aplikacji WPF można przechowywać dane i uzyskiwać do nich dostęp za pomocą technologii, takich jak SQL Server i ADO .NET. Po uzyskaniu dostępu do danych i załadowaniu ich do zarządzanych obiektów aplikacji, rozpocznie się działanie dla aplikacji WPF. Zasadniczo obejmuje to dwie rzeczy:

1. Kopiowanie danych z zarządzanych obiektów do kontrolek, w których można wyświetlać i edytować dane.

2. Zagwarantowanie, że zmiany wprowadzone do danych za pomocą kontrolek są kopiowane z powrotem do obiektów zarządzanych.

Aby uprościć tworzenie aplikacji, funkcja WPF udostępnia aparat powiązań danych w celu automatycznego wykonania tych kroków. Jednostką podstawową aparatu powiązań danych jest <xref:System.Windows.Data.Binding> Klasa, której zadanie ma powiązać kontrolkę (obiekt docelowy powiązania) z obiektem danych (Źródło powiązania). Ta relacja jest zilustrowana na poniższej ilustracji:

![Podstawowy diagram powiązań danych](../designers/media/databindingmostbasic.png)

W następnym przykładzie pokazano, jak powiązać <xref:System.Windows.Controls.TextBox> z wystąpieniem obiektu niestandardowego. `Person` `Person` Implementacja jest pokazana w poniższym kodzie:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/VisualBasic/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/CSharp/introduction-to-wpf_2.cs)]

Następujące znaczniki wiążą <xref:System.Windows.Controls.TextBox> się z wystąpieniem obiektu niestandardowego `Person` .

```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_6.cs)]

W tym przykładzie `Person` Klasa jest tworzona w kodzie i jest ustawiana jako kontekst danych `DataBindingWindow`dla. W znaczniku <xref:System.Windows.Controls.TextBox.Text%2A> Właściwość <xref:System.Windows.Controls.TextBox> jest powiązana `Person.Name` z właściwością (przy użyciu składni języka XAML`{Binding ... }`""). Ten kod XAML informuje WPF, aby <xref:System.Windows.Controls.TextBox> powiązać formant `Person` z obiektem <xref:System.Windows.FrameworkElement.DataContext%2A> , który jest przechowywany we właściwości okna.

Aparat powiązań danych WPF zapewnia dodatkową pomoc techniczną, która obejmuje walidację, sortowanie, filtrowanie i grupowanie. Ponadto powiązanie danych obsługuje używanie szablonów danych do tworzenia niestandardowego interfejsu użytkownika dla powiązanych danych, gdy interfejs użytkownika wyświetlany przez standardowe formanty WPF nie jest odpowiedni.

Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="graphics"></a>Grafika

WPF wprowadza bogaty, skalowalny i elastyczny zestaw funkcji graficznych, które mają następujące zalety:

- Niezależna od **rozdzielczości i grafika niezależna od urządzenia**. Podstawowa jednostka miary w systemie grafiki WPF to piksel niezależny od urządzenia, czyli 1/1/96 cala, niezależnie od rzeczywistej rozdzielczości ekranu, a także podstawą renderowania niezależną od rozdzielczości i niezależną od urządzenia. Każdy piksel niezależny od urządzenia automatycznie skaluje się w celu dopasowania do ustawienia DPI systemu, w którym jest renderowane.

- **Ulepszona precyzja**. System współrzędnych WPF jest mierzony przy użyciu liczb zmiennoprzecinkowych o podwójnej precyzji, a nie pojedynczej precyzji. Przekształcenia i wartości przejrzystości są również wyrażone jako podwójne precyzja. WPF obsługuje również szeroką gamę kolorów (scRGB) i zapewnia zintegrowaną obsługę zarządzania danymi wejściowymi z różnych przestrzeni kolorów.

- **Zaawansowana obsługa grafiki i animacji**. WPF upraszcza programowanie grafiki przez zarządzanie scenami animacji. nie trzeba martwić się o przetwarzanie sceny, pętle renderowania i interpolację liniową. Ponadto WPF zapewnia obsługę testowania trafień i pełną obsługę składania Alpha.

- **Przyspieszenie sprzętowe**. System grafiki WPF wykorzystuje sprzęt graficzny do zminimalizowania użycia procesora CPU.

### <a name="2d-shapes"></a>kształty 2D

WPF udostępnia bibliotekę wspólnych kształtów 2D rysowanych za pomocą wektorów, takich jak prostokąty i wielokropek, które są wyświetlane na poniższej ilustracji:

![Wielokropek i prostokąty](../designers/media/wpfintrofigure4.PNG)

Interesująca możliwość tworzenia kształtów to nie tylko do wyświetlania; kształty implementują wiele funkcji, których oczekujesz od kontrolek, w tym dane wejściowe z klawiatury i myszy. W poniższym przykładzie pokazano <xref:System.Windows.UIElement.MouseUp> zdarzenie, <xref:System.Windows.Shapes.Ellipse> które jest obsługiwane.

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_8.cs)]

Na poniższej ilustracji przedstawiono, co jest generowane przez poprzedni kod.

![Okno z tekstem "wielokropek&#33;"](../designers/media/wpfintrofigure12.png)

Aby uzyskać więcej informacji, zobacz temat [kształty i podstawowe Rysowanie w programie WPF — Omówienie](/dotnet/framework/wpf/data/data-binding-overview).

### <a name="2d-geometries"></a>2D geometrie

Kształty 2D udostępniane przez WPF obejmują standardowy zestaw kształtów podstawowych. Jednak może być konieczne utworzenie niestandardowych kształtów w celu ułatwienia projektowania dostosowanego interfejsu użytkownika. W tym celu WPF udostępnia geometrie. Na poniższej ilustracji przedstawiono użycie geometrie do utworzenia niestandardowego kształtu, który może być rysowany bezpośrednio, używany jako pędzel lub używany do wycinania innych kształtów i kontrolek.

<xref:System.Windows.Shapes.Path>obiekty mogą służyć do rysowania zamkniętych lub otwartych kształtów, wielu kształtów, a nawet kształtów zakrzywionych.

<xref:System.Windows.Media.Geometry>obiekty mogą służyć do przycinania, testowania trafień i renderowania danych graficznych 2D.

![Różne zastosowania ścieżki](../designers/media/wpfintrofigure5.png)

Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](/dotnet/framework/wpf/graphics-multimedia/geometry-overview).

### <a name="2d-effects"></a>efekty 2D

Podzbiór możliwości WPF 2D obejmuje efekty wizualne, takie jak gradienty, mapy bitowe, rysunki, malowanie przy użyciu filmów wideo, obracanie, skalowanie i pochylanie. Są one osiągane przy użyciu pędzli; na poniższej ilustracji przedstawiono kilka przykładów.

![Ilustracja przedstawiająca różne pędzle](../designers/media/wpfintrofigure6.png)

Aby uzyskać więcej informacji, zobacz [Omówienie pędzli WPF](/dotnet/framework/wpf/graphics-multimedia/wpf-brushes-overview).

### <a name="3d-rendering"></a>Renderowanie 3W

WPF obejmuje również funkcje renderowania 3W, które integrują się z grafikami 2-d, umożliwiając tworzenie bardziej atrakcyjnych i interesujących interfejsów użytkownika. Na przykład na poniższej ilustracji przedstawiono obrazy 2D renderowane na kształtach 3W.

![Zrzut ekranu przedstawiający przykładowy Visual3D](../designers/media/wpfintrofigure13.png)

Aby uzyskać więcej informacji, zobacz [grafika 3D — Omówienie](/dotnet/framework/wpf/graphics-multimedia/3-d-graphics-overview).

## <a name="animation"></a>Animacja

Obsługa animacji WPF pozwala zwiększyć, wstrząsać, obracać i zanikać kontrolki, aby tworzyć interesujące przejścia stron i nie tylko. Można animować większość klas WPF, nawet klas niestandardowych. Na poniższej ilustracji przedstawiono prostą animację w działaniu.

![Obrazy animowanego modułu](../designers/media/wpfintrofigure7.png)

Aby uzyskać więcej informacji, zobacz [Omówienie animacji](/dotnet/framework/wpf/graphics-multimedia/animation-overview).

## <a name="media"></a>Multimedialny

Jednym ze sposobów przekazywania rozbudowanej zawartości jest użycie multimediów audiowizualnych. WPF zapewnia specjalną obsługę obrazów, wideo i audio.

### <a name="images"></a>Obrazy

Obrazy są wspólne dla większości aplikacji, a WPF oferuje kilka sposobów ich używania. Na poniższej ilustracji przedstawiono interfejs użytkownika z polem listy zawierającym obrazy miniatur. Po wybraniu miniatury obraz zostanie wyświetlony w pełnym rozmiarze.

![Obrazy miniatur i obraz o&#45;pełnym rozmiarze](../designers/media/wpfintrofigure8.png)

Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia obrazu](/dotnet/framework/wpf/graphics-multimedia/imaging-overview).

### <a name="video-and-audio"></a>Wideo i audio

<xref:System.Windows.Controls.MediaElement> Kontrolka jest w stanie odtwarzać wideo i dźwięk, a jest wystarczająco elastyczna, aby była podstawą dla niestandardowego odtwarzacza multimedialnego. Poniższe oznakowanie XAML implementuje odtwarzacz multimedialny.

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_9.xaml)]

Okno na poniższej ilustracji pokazuje <xref:System.Windows.Controls.MediaElement> kontrolkę w akcji.

![Kontrolka MediaElement z dźwiękiem i wideo](../designers/media/wpfintrofigure1.png)

Aby uzyskać więcej informacji, zobacz [grafika i multimedia](/dotnet/framework/wpf/graphics-multimedia).

## <a name="text-and-typography"></a>Tekst i Typografia

Aby ułatwić renderowanie tekstu o wysokiej jakości, WPF oferuje następujące funkcje:

- Obsługa czcionek OpenType.

- Ulepszenia technologii ClearType.

- Wysoka wydajność, która wykorzystuje przyspieszenie sprzętowe.

- Integracja tekstu z multimediami, grafiką i animacją.

- Obsługa czcionek międzynarodowych i mechanizmów powrotu.

Jako Demonstracja integracji tekstu z grafiką na poniższej ilustracji przedstawiono sposób stosowania dekoracji tekstu.

![Tekst z różnymi dekoracjami tekstu](../designers/media/wpfintrofigure23.png)

Aby uzyskać więcej informacji, zobacz [Typografia w Windows Presentation Foundation](/dotnet/framework/wpf/advanced/typography-in-wpf).

## <a name="customize-wpf-apps"></a>Dostosuj aplikacje WPF

Do tego momentu zaobserwowano podstawowe bloki konstrukcyjne WPF na potrzeby tworzenia aplikacji. Model aplikacji jest używany do hostowania i dostarczania zawartości aplikacji, która składa się głównie z kontrolek. Aby uprościć rozmieszczenie formantów w interfejsie użytkownika i upewnić się, że rozmieszczenie jest zachowywane na początku zmian rozmiaru okna i ustawień wyświetlania, należy użyć systemu układu WPF. Ze względu na to, że większość aplikacji pozwala użytkownikom na współdziałanie z danymi, należy użyć powiązania danych, aby ograniczyć pracę integracji interfejsu użytkownika z danymi. Aby wzmocnić wygląd aplikacji, należy użyć kompleksowego zakresu grafiki, animacji i pomocy technicznej multimedialnej zapewnianej przez WPF.

Często jednak podstawowe informacje nie są wystarczające do tworzenia naprawdę odrębnego i wizualnego środowiska użytkownika. Standardowe formanty WPF mogą nie zostać zintegrowane z żądanym wyglądem aplikacji. Dane mogą nie być wyświetlane w najbardziej efektywny sposób. Ogólne środowisko użytkownika aplikacji może nie być odpowiednie dla domyślnego wyglądu i sposobu działania motywów systemu Windows. Na wiele sposobów Technologia prezentacji wymaga rozszerzalności wizualizacji tak samo, jak każdy inny typ rozszerzalności.

Z tego powodu WPF oferuje różne mechanizmy tworzenia unikatowych środowisk użytkowników, w tym bogaty model zawartości dla formantów, wyzwalaczy, szablonów formantów i danych, stylów, zasobów interfejsu użytkownika i motywów i karnacji.

### <a name="content-model"></a>Model zawartości

Głównym celem większości formantów WPF jest wyświetlenie zawartości. W WPF typ i liczba elementów, które mogą stanowić zawartość kontrolki, jest określany jako *model zawartości*kontrolki. Niektóre kontrolki mogą zawierać pojedynczy element i typ zawartości; na przykład zawartość a <xref:System.Windows.Controls.TextBox> jest wartością ciągu, która jest przypisana <xref:System.Windows.Controls.TextBox.Text%2A> do właściwości. Poniższy przykład ustawia zawartość <xref:System.Windows.Controls.TextBox>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

Na poniższej ilustracji przedstawiono wynik.

![Formant TextBox zawierający tekst.](../designers/media/wpfintrofigure21.png)

Inne kontrolki, jednak mogą zawierać wiele elementów różnych typów zawartości; zawartość <xref:System.Windows.Controls.Button>obiektu, określonego <xref:System.Windows.Controls.ContentControl.Content%2A> przez właściwość, może zawierać różne elementy, takie jak kontrolki układu, tekst, obrazy i kształty. W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Button> zawartość <xref:System.Windows.Controls.DockPanel>obejmującą, <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Border>a, a i <xref:System.Windows.Controls.MediaElement>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

Na poniższej ilustracji przedstawiono zawartość tego przycisku.

![Przycisk, który zawiera wiele typów zawartości](../designers/media/wpfintrofigure22.png)

Aby uzyskać więcej informacji o rodzaju zawartości obsługiwanej przez różne kontrolki, zobacz artykuł [model zawartości WPF](/dotnet/framework/wpf/controls/wpf-content-model).

### <a name="triggers"></a>Wyzwalacze

Chociaż głównym celem znacznika języka XAML jest zaimplementowanie wyglądu aplikacji, można również użyć języka XAML do implementacji niektórych aspektów zachowania aplikacji. Przykładem jest użycie wyzwalaczy do zmiany wyglądu aplikacji w oparciu o Interakcje użytkownika. Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="control-templates"></a>Szablony kontrolek

Domyślne interfejsy użytkownika dla formantów WPF są zwykle zbudowane z innych formantów i kształtów. Na przykład <xref:System.Windows.Controls.Button> składa się z obu <xref:Microsoft.Windows.Themes.ButtonChrome> formantów i <xref:System.Windows.Controls.ContentPresenter> . Zapewnia standardowy wygląd przycisku, <xref:System.Windows.Controls.ContentPresenter> podczas gdy wyświetla zawartość przycisku <xref:System.Windows.Controls.ContentControl.Content%2A> , jak określono przez właściwość. <xref:Microsoft.Windows.Themes.ButtonChrome>

Czasami domyślny wygląd formantu może być incongruent z ogólnym wyglądem aplikacji. W takim przypadku można użyć <xref:System.Windows.Controls.ControlTemplate> , aby zmienić wygląd interfejsu użytkownika kontrolki bez zmiany jego zawartości i zachowania.

Na przykład poniższy przykład pokazuje, jak zmienić wygląd elementu <xref:System.Windows.Controls.Button> przy <xref:System.Windows.Controls.ControlTemplate>użyciu.

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_17.vb)]

W tym przykładzie interfejs użytkownika przycisku domyślnego został zastąpiony <xref:System.Windows.Shapes.Ellipse> , który ma ciemne niebieskie obramowanie i jest wypełniany <xref:System.Windows.Media.RadialGradientBrush>przy użyciu. Kontrolka wyświetla zawartość <xref:System.Windows.Controls.Button>, "kliknij mnie!" <xref:System.Windows.Controls.ContentPresenter> Gdy zostanie kliknięty <xref:System.Windows.Controls.Primitives.ButtonBase.Click> , zdarzenie jest nadal <xref:System.Windows.Controls.Button> wywoływane w ramach domyślnego zachowania formantu. <xref:System.Windows.Controls.Button> Wyniki są pokazane na poniższym rysunku:

![Przycisk eliptyczne i drugie okno](../designers/media/wpfintrofigure2.png)

### <a name="data-templates"></a>Szablony danych

Natomiast szablon kontrolki umożliwia określenie wyglądu kontrolki, szablon danych pozwala określić wygląd zawartości kontrolki. Szablony danych są często używane do ulepszania sposobu wyświetlania powiązanych danych. Na poniższej ilustracji przedstawiono domyślny wygląd dla elementu <xref:System.Windows.Controls.ListBox> , który jest powiązany z `Task` kolekcją obiektów, gdzie każde zadanie ma nazwę, opis i priorytet.

![Pole listy z wyglądem domyślnym](../designers/media/wpfintrofigure18.png)

Domyślnym wyglądem jest to, czego oczekujesz od <xref:System.Windows.Controls.ListBox>. Jednak domyślny wygląd każdego zadania zawiera tylko nazwę zadania. Aby wyświetlić nazwę, opis i priorytet zadania, należy zmienić domyślny wygląd <xref:System.Windows.Controls.ListBox> elementów listy powiązanej formantu przy <xref:System.Windows.DataTemplate>użyciu. Poniższy kod XAML definiuje takie <xref:System.Windows.DataTemplate>, który jest stosowany do każdego zadania przy <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> użyciu atrybutu.

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

Poniższy rysunek przedstawia efekt tego kodu.

![Pole listy, które używa szablonu danych](../designers/media/wpfintrofigure19.png)

Zwróć uwagę, <xref:System.Windows.Controls.ListBox> że zachowano swoje zachowanie i ogólny wygląd; tylko wygląd zawartości wyświetlanej w polu listy został zmieniony.

Aby uzyskać więcej informacji, zobacz [tworzenia szablonów danych — omówienie](/dotnet/framework/wpf/data/data-templating-overview).

### <a name="styles"></a>Style

Style umożliwiają deweloperom i projektantom ujednolicenie się z konkretnym wyglądem produktu. WPF oferuje model silnego stylu, podstawę, która jest <xref:System.Windows.Style> elementem. Poniższy przykład tworzy styl, który ustawia kolor tła dla każdego <xref:System.Windows.Controls.Button> w oknie do. `Orange`

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

Ponieważ ten styl jest przeznaczony <xref:System.Windows.Controls.Button> dla wszystkich kontrolek, styl jest automatycznie stosowany do wszystkich przycisków w oknie, jak pokazano na poniższej ilustracji:

![Dwa pomarańczowe przyciski](../designers/media/wpfintrofigure20.png)

Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="resources"></a>Zasoby

Kontrolki w aplikacji powinny korzystać z tego samego wyglądu, które mogą zawierać dowolne elementy z czcionek i kolorów tła, które umożliwiają kontrolowanie szablonów, szablonów danych i stylów. Możesz użyć obsługi platformy WPF do zasobów interfejsu użytkownika, aby hermetyzować te zasoby w jednej lokalizacji do ponownego użycia.

W poniższym przykładzie zdefiniowano typowy kolor tła, który jest udostępniany <xref:System.Windows.Controls.Button> przez <xref:System.Windows.Controls.Label>i.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

Ten przykład implementuje zasób koloru tła za pomocą `Window.Resources` elementu właściwości. Ten zasób jest dostępny dla wszystkich elementów podrzędnych <xref:System.Windows.Window>. Istnieje wiele zakresów zasobów, w tym następujące, wymienione w kolejności, w jakiej zostały rozwiązane:

1. Indywidualny formant (przy użyciu dziedziczonej <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> właściwości).

2. A <xref:System.Windows.Window> lub a <xref:System.Windows.Controls.Page> (również przy użyciu dziedziczonej <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> właściwości).

3. <xref:System.Windows.Application> A<xref:System.Windows.Application.Resources%2A?displayProperty=fullName> (za pomocą właściwości).

Różne zakresy zapewniają elastyczność w odniesieniu do sposobu definiowania i udostępniania zasobów.

Alternatywnie do bezpośredniego kojarzenia zasobów z określonym zakresem, można spakować jeden lub więcej zasobów przy użyciu oddzielnego <xref:System.Windows.ResourceDictionary> , do którego można odwoływać się w innych częściach aplikacji. Na przykład poniższy przykład definiuje domyślny kolor tła w słowniku zasobów.

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

Poniższy przykład odwołuje się do słownika zasobów zdefiniowanego w poprzednim przykładzie, tak aby był współużytkowany przez aplikację.

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

Zasoby i słowniki zasobów są podstawą obsługi technologii WPF dla motywów i skórek.

Aby uzyskać więcej informacji, zobacz [zasoby](/dotnet/framework/wpf/advanced/xaml-resources).

### <a name="custom-controls"></a>Kontrolki niestandardowe

Mimo że WPF udostępnia obsługę dostosowywania, można napotkać sytuacje, w których istniejące formanty WPF nie spełniają wymagań aplikacji lub użytkowników. Może się tak zdarzyć, gdy:

- Nie można utworzyć wymaganego interfejsu użytkownika przez dostosowanie wyglądu i sposobu działania istniejących implementacji WPF.

- Wymagane zachowanie nie jest obsługiwane (lub nie jest obsługiwane w łatwy sposób) przez istniejące implementacje WPF.

W tym momencie można jednak skorzystać z jednego z trzech modeli WPF, aby utworzyć nową kontrolkę. Każdy model jest przeznaczony dla określonego scenariusza i wymaga, aby formant niestandardowy dziedziczył od określonej klasy bazowej WPF. Trzy modele są wymienione tutaj:

- **Model kontroli użytkownika**. Kontrolka niestandardowa <xref:System.Windows.Controls.UserControl> dziedziczy z i składa się z co najmniej jednej innej kontrolki.

- **Model sterowania**. Kontrolka niestandardowa <xref:System.Windows.Controls.Control> dziedziczy z i służy do kompilowania implementacji, które oddzielają ich zachowanie od ich wyglądu przy użyciu szablonów, podobnie jak większość formantów WPF. Wyprowadzanie z <xref:System.Windows.Controls.Control> programu umożliwia większą swobodę tworzenia niestandardowego interfejsu użytkownika niż kontrolki użytkownika, ale może wymagać większego nakładu pracy.

- **Model elementu struktury**. Kontrolka niestandardowa <xref:System.Windows.FrameworkElement> pochodzi od momentu zdefiniowania jego wyglądu przy użyciu logiki renderowania niestandardowego (nie szablonów).

Poniższy przykład przedstawia niestandardową kontrolkę Up/Down, która pochodzi <xref:System.Windows.Controls.UserControl>od.

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/CSharp/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/VisualBasic/introduction-to-wpf_34.vb)]

Następny przykład ilustruje kod XAML, który jest wymagany do włączenia kontrolki użytkownika do <xref:System.Windows.Window>.

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_37.xaml)]

Na poniższej ilustracji przedstawiono `NumericUpDown` kontrolkę hostowaną <xref:System.Windows.Window>w elemencie.

![Niestandardowy element UserControl](../designers/media/wpfintrofigure3.png)

Aby uzyskać więcej informacji na temat kontrolek niestandardowych, zobacz temat [Tworzenie kontroli — Omówienie](/dotnet/framework/wpf/controls/control-authoring-overview).

## <a name="wpf-best-practices"></a>Najlepsze rozwiązania dotyczące WPF

Podobnie jak w przypadku dowolnej platformy programistycznej, WPF można używać na wiele sposobów w celu osiągnięcia żądanego wyniku. W celu upewnienia się, że aplikacje WPF zapewniają wymagane środowisko użytkownika i są ogólnie zgodne z wymaganiami odbiorców, zalecane są najlepsze rozwiązania dotyczące ułatwień dostępu, globalizacji i lokalizacji oraz wydajności. Aby uzyskać więcej informacji, zobacz:

- [Ułatwienia dostępu](/dotnet/framework/ui-automation/accessibility-best-practices)
- [Globalizacja i lokalizacja WPF](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview)
- [Wydajność aplikacji WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Zabezpieczenia WPF](/dotnet/framework/wpf/security-wpf)

## <a name="next-steps"></a>Następne kroki

Przeglądamy najważniejsze funkcje platformy WPF. Teraz czas na skompilowanie pierwszej aplikacji WPF.

> [!div class="nextstepaction"]
> [Przewodnik: Moja pierwsza aplikacja klasyczna WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)

## <a name="see-also"></a>Zobacz także

- [Rozpoczynanie pracy z aparatem WPF](../designers/getting-started-with-wpf.md)
- [Windows Presentation Foundation](/dotnet/framework/wpf/index)
- [Zasoby społeczności WPF](/dotnet/framework/wpf/getting-started/community-feedback)