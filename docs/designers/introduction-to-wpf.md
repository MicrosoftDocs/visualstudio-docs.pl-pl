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
ms.openlocfilehash: d15f0e8e5c5cbdac5a130804977adf90385adfe1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093686"
---
# <a name="wpf-overview"></a>Omówienie podsystemu WPF

Windows Presentation Foundation (WPF) pozwala tworzyć aplikacje dla Windows klient stacjonarny wizualnie olśniewających graficznie środowisk użytkownika.

![Przykładowy interfejs użytkownika z branży opieki zdrowotnej firmy Contoso](../designers/media/wpfintrofigure24.png)

Podstawowe WPF jest aparat renderowania niezależne od rozdzielczości i wektorowej, który został opracowany pod kątem zalet sprzęt graficzny modern. WPF rozszerza core przy użyciu kompleksowych funkcji tworzenia aplikacji, które obejmują Extensible Application Markup Language (XAML), kontrolek, powiązanie danych, układ, grafiki 2D i 3D, animacji, stylów, szablony, dokumentów, nośnika, tekstu, a Typografia. WPF znajduje się na platformie .NET Framework, dzięki czemu możesz tworzyć aplikacje, które zawierają inne elementy w bibliotece klas programu .NET Framework.

W tym omówieniu jest przeznaczony dla nowych osób i opisano kluczowe funkcje i pojęcia dotyczące środowiska WPF.

## <a name="program-with-wpf"></a>Program przy użyciu platformy WPF

WPF istnieje jako podzbiór typów programu .NET Framework, które znajdują się w większości przypadków w <xref:System.Windows> przestrzeni nazw. Jeśli aplikacje zostały wcześniej utworzony za pomocą .NET Framework przy użyciu technologii zarządzanych, takich jak ASP.NET i Windows Forms, WPF podstawowe środowisko programowania należy się zapoznać; Możesz utworzyć wystąpienia klasy, ustaw właściwości, metody wywołania i zdarzenia uchwyt, za pomocą platformy .NET ulubiony język programowania, takich jak C# lub Visual Basic.

WPF obejmuje dodatkowych narzędzi programistycznych, które podnoszą właściwości i zdarzenia: [właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview) i [zdarzenia trasowanego](/dotnet/framework/wpf/advanced/routed-events-overview).

## <a name="markup-and-code-behind"></a>Znaczniki i związane z kodem

WPF umożliwia tworzenie aplikacji przy użyciu zarówno *znaczników* i *związanym z kodem*, środowisko, które ASP.NET deweloperzy powinni zapoznać się. Zazwyczaj przy użyciu znaczników XAML wyglądu aplikacji podczas używania zarządzanego języków programowania (związane z kodem) w celu zaimplementować jego zachowanie. To oddzielenie wygląd i zachowanie ma następujące zalety:

- Koszty tworzenia i konserwacji są ograniczone, ponieważ specyficzne dla wyglądu znacznika nie jest ściśle powiązany z kodu specyficznego dla zachowania.

- Programowanie jest bardziej wydajne, ponieważ projektantów można zaimplementować wygląd aplikacji równocześnie z deweloperów, którzy wdrażają zachowaniu aplikacji.

- [Globalizacja i lokalizacja](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview) dla WPF jest uproszczony w aplikacji.

### <a name="markup"></a>Kod znaczników

XAML jest językiem znaczników oparty na formacie XML, który implementuje wygląd aplikacji deklaratywnie. Zazwyczaj służy do tworzenia systemu windows, okna dialogowe, strony i kontrolki użytkownika i wypełnianie formantów, kształty i grafiki.

W poniższym przykładzie użyto XAML, aby zaimplementować wygląd okna, który zawiera jeden przycisk.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

W szczególności ten XAML definiuje okno i przycisk za pomocą `Window` i `Button` elementów, odpowiednio. Każdy element jest skonfigurowany z atrybutami, takich jak `Window` elementu `Title` atrybutu, aby określić tekst paska tytułu okna. W czasie wykonywania WPF konwertuje elementy i atrybuty, które są zdefiniowane w znaczników do wystąpień klas WPF. Na przykład `Window` element jest konwertowany na wystąpienie <xref:System.Windows.Window> klasy, których <xref:System.Windows.Window.Title%2A> właściwość ma wartość `Title` atrybutu.

Na poniższej ilustracji przedstawiono interfejs użytkownika (UI), który jest definiowany przez XAML w poprzednim przykładzie.

![Okno które zawiera przycisk](../designers/media/wpfintrofigure10.png)

Ponieważ XAML jest oparty na formacie XML, interfejs użytkownika, który tworzą z nią jest składany w hierarchii zagnieżdżonej elementów nazywanych [drzewo elementów](/dotnet/framework/wpf/advanced/trees-in-wpf). Drzewo elementów zawiera logiczne i intuicyjny sposób tworzenia i zarządzania nimi interfejsów użytkownika.

### <a name="code-behind"></a>Związane z kodem

Główne zachowanie aplikacji jest do implementacji funkcji, który odpowiada na interakcję użytkownika, w tym obsługa zdarzeń (na przykład, klikając pozycję menu, pasek narzędzi lub przycisk) i wywoływania logika biznesowa i logika dostępu do danych w odpowiedzi. W środowisku WPF to zachowanie jest zaimplementowana w kodzie, który jest skojarzony z kodu znaczników. Tego rodzaju kod jest znany jako związany z kodem. Poniższy przykład pokazuje zaktualizowane znaczników z poprzedniego przykładu i związanymi z kodem.

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

W tym przykładzie kodu powiązanego implementuje klasę, która pochodzi od klasy <xref:System.Windows.Window> klasy. `x:Class` Atrybut jest używany do skojarzenia z kodu znaczników przy użyciu klasy CodeBehind. `InitializeComponent` jest wywoływana z konstruktora klasy CodeBehind do scalenia interfejs użytkownika, który jest zdefiniowany w znacznikach z klasą CodeBehind. (`InitializeComponent` zostanie wygenerowany podczas kompilowania aplikacji, dlatego nie trzeba zaimplementować go ręcznie.) Kombinacja `x:Class` i `InitializeComponent` upewnij się, że implementacji poprawnie zainicjować po każdym utworzeniu. Klasy związane z kodem implementuje również program obsługi zdarzeń dla przycisku <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń. Po kliknięciu przycisku program obsługi zdarzeń wyświetli okno wiadomości przez wywołanie metody <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> metody.

Na poniższej ilustracji przedstawiono wyniki, po kliknięciu przycisku.

![Komunikat MessageBox](../designers/media/wpfintrofigure25.png)

## <a name="controls"></a>Formanty

Środowiska użytkownika, które są dostarczane przez ten model aplikacji są skonstruowane formanty. W środowisku WPF *kontroli* jest ogólny termin, który ma zastosowanie do kategorii klas WPF, które są hostowane w dowolnym oknie lub strony, mają interfejs użytkownika i wdrożenia niektóre zachowania.

Aby uzyskać więcej informacji, zobacz [formantów](/dotnet/framework/wpf/controls/index).

### <a name="wpf-controls-by-function"></a>Formanty WPF według kategorii

Poniżej przedstawiono wbudowanych kontrolek WPF.

- **Przyciski**: <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Primitives.RepeatButton>.

- **Wyświetlanie danych**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, i <xref:System.Windows.Controls.TreeView>.

- **Data, wyświetlanie i wybór**: <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker>.

- **Okna dialogowe**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, i <xref:Microsoft.Win32.SaveFileDialog>.

- **Cyfrowy atrament**: <xref:System.Windows.Controls.InkCanvas> i <xref:System.Windows.Controls.InkPresenter>.

- **Dokumenty**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, i <xref:System.Windows.Controls.StickyNoteControl>.

- **Dane wejściowe**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, i <xref:System.Windows.Controls.PasswordBox>.

- **Układ**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, i <xref:System.Windows.Controls.WrapPanel>.

- **Nośnik**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, i <xref:System.Windows.Controls.SoundPlayerAction>.

- **Menu**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, i <xref:System.Windows.Controls.ToolBar>.

- **Nawigacja**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, i <xref:System.Windows.Controls.TabControl>.

- **Wybór**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, i <xref:System.Windows.Controls.Slider>.

- **Informacje o użytkowniku**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, i <xref:System.Windows.Controls.ToolTip>.

## <a name="input-and-commands"></a>Dane wejściowe i polecenia

Formanty w większości przypadków wykrywanie oraz reagowanie na dane wejściowe użytkownika. [System wprowadzania WPF](/dotnet/framework/wpf/advanced/input-overview) używa zarówno bezpośrednich, jak i routingiem zdarzeń do obsługi wprowadzania tekstu, funkcje zarządzania i położenie myszy.

Aplikacje mają często złożone wymagania danych wejściowych. WPF zapewnia [polecenia system](/dotnet/framework/wpf/advanced/commanding-overview) oddzielający akcje dane wejściowe użytkownika z kodu, który odpowiada na te akcje.

## <a name="layout"></a>Układ

Podczas tworzenia interfejsu użytkownika można zorganizować kontrolkom zorganizowanych według lokalizacji i rozmiaru w celu utworzenia układu. Najważniejszym wymaganiem, wszelkie układu jest dostosowania do zmiany rozmiaru okna i wyświetlić ustawienia. Zamiast wymuszania, pisanie kodu w celu dostosowania układu w tych okolicznościach, WPF zapewnia system najwyższej jakości, rozszerzalne układu dla Ciebie.

Podstawa system układu jest położenie względne, co zwiększa możliwości dostosowanie do zmieniających się okna i wyświetlania warunków. Ponadto system układu zarządza negocjacji między kontrolkami do określania układu. Negocjowanie jest procesem dwuetapowym: najpierw kontrolki informuje jego obiektu nadrzędnego, jakie lokalizacji i rozmiaru wymaga; Po drugie nadrzędny informuje kontrolki miejsca, które może mieć.

System układu jest narażony na formantów podrzędnych za pomocą klasy bazowe WPF. W przypadku typowych układów, takich jak siatki, układanie i dokowanie WPF zawiera kilka formantów układu:

- <xref:System.Windows.Controls.Canvas>: Formanty podrzędne zawierają własne układu.

- <xref:System.Windows.Controls.DockPanel>: Formanty podrzędne są wyrównane do krawędzi panelu.

- <xref:System.Windows.Controls.Grid>: Formanty podrzędne są rozmieszczane według wierszy i kolumn.

- <xref:System.Windows.Controls.StackPanel>: Formanty podrzędne są ułożone poziomo lub pionowo.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: Formanty podrzędne są zwirtualizowane i rozmieszczone na pojedynczej linii poziomej lub pionowej.

- <xref:System.Windows.Controls.WrapPanel>: Formanty podrzędne są rozmieszczone w kolejności od lewej do prawej i zawinięty do następnego wiersza, gdy istnieją więcej kontrolek w bieżącym wierszu, niż pozwala miejsca.

W poniższym przykładzie użyto <xref:System.Windows.Controls.DockPanel> układ kilka <xref:System.Windows.Controls.TextBox> kontrolki.

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_1.xaml)]

<xref:System.Windows.Controls.DockPanel> Umożliwia podrzędne <xref:System.Windows.Controls.TextBox> formantów stwierdzenie, sposobu ich rozmieszczenia. Aby to zrobić, <xref:System.Windows.Controls.DockPanel> implementuje `Dock` dołączona właściwość, która jest widoczna do formantów podrzędnych, aby umożliwić każdej z nich, aby określić styl dokowania.

> [!NOTE]
> Wywołuje się, właściwość, która jest implementowany przez kontrolki nadrzędnej, używany przez formanty podrzędne to konstrukcja WPF [dołączona właściwość](/dotnet/framework/wpf/advanced/attached-properties-overview).

Na poniższej ilustracji przedstawiono wynik znaczników XAML w poprzednim przykładzie.

![Strona DockPanel](../designers/media/wpfintrofigure11.png)

## <a name="data-binding"></a>Powiązanie danych

Większość aplikacji są tworzone użytkownikom sposób wyświetlić i edytować dane. Dla aplikacji WPF praca, przechowywania i uzyskiwania dostępu do danych jest już udostępniane na potrzeby technologii, takich jak SQL Server oraz obiektów ADO .NET. Po dane są dostępne, a następnie ładowane do aplikacji zarządzanych obiektów, rozpoczyna się trudną pracę dla aplikacji WPF. Obejmuje to zasadniczo dwie rzeczy:

1. Kopiowanie danych z obiektów zarządzanych w formantach, gdzie można wyświetlane i edytowane dane.

2. Zapewnienie, że zmiany wprowadzone w danych za pomocą formantów są kopiowane do obiektów zarządzanych.

Aby uprościć tworzenie aplikacji, WPF zapewnia aparat powiązania danych, aby automatycznie wykonać następujące kroki. Jednostki podstawowe aparat wiązanie danych jest <xref:System.Windows.Data.Binding> klasy, których zadaniem jest do wiązania kontrolki (cel wiążący) obiektu danych (źródło wiążące). Ta relacja jest zilustrowany przez poniższej ilustracji:

![Diagram podstawowego powiązania danych](../designers/media/databindingmostbasic.png)

Następny przykład pokazuje, jak powiązać <xref:System.Windows.Controls.TextBox> do wystąpienia klasy niestandardowej `Person` obiektu. `Person` Implementację przedstawiono w poniższym kodzie:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/VisualBasic/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/CSharp/introduction-to-wpf_2.cs)]

Następujące znaczniki wiąże <xref:System.Windows.Controls.TextBox> do wystąpienia klasy niestandardowej `Person` obiektu.

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

W tym przykładzie `Person` klasa zostanie uruchomiony w związanym z kodem i jest ustawiony jako kontekst danych dla `DataBindingWindow`. W znaczniku <xref:System.Windows.Controls.TextBox.Text%2A> właściwość <xref:System.Windows.Controls.TextBox> jest powiązany z `Person.Name` właściwości (przy użyciu "`{Binding ... }`" Składnia XAML). Ta XAML informuje WPF można powiązać <xref:System.Windows.Controls.TextBox> kontrolę `Person` obiekt, który jest przechowywany w <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości okna.

Aparat powiązanie danych WPF zapewnia dodatkową obsługę, która obejmuje sprawdzanie poprawności, sortowanie, filtrowanie i grupowanie. Ponadto powiązań danych obsługuje dane szablonów do tworzenia niestandardowego interfejsu użytkownika dla powiązanych danych, gdy nie jest odpowiedni interfejs użytkownika wyświetlany przez standardowych kontrolek WPF.

Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="graphics"></a>Grafika

WPF wprowadza rozbudowane, skalowalny i elastyczny zestaw funkcje grafiki, które mają następujące korzyści:

- **Niezależne od rozdzielczości i niezależny od urządzenia grafiki**. Podstawowa jednostka miary w systemie grafiki WPF jest piksel niezależnych od urządzenia, czyli 1/96 cala, niezależnie od tego, rzeczywista rozdzielczość ekranu i stanowi podstawę do renderowania niezależne od rozdzielczości i niezależny od urządzenia. Piksele niezależne od urządzenia, która jest automatycznie skalowany aby dopasować ustawienie punktów na cal (dpi) systemu, które powoduje renderowanie na.

- **Ulepszone dokładności**. System współrzędnych WPF jest mierzony z liczby zmiennoprzecinkowe podwójnej precyzji niż pojedynczej precyzji. Przekształcenia i nieprzezroczystość wartości również są wyrażane jako podwójnej precyzji. WPF również obsługuje szeroka gama kolorów (scRGB) i obsługuje zintegrowane zarządzanie danych wejściowych z różnych przestrzeni kolorów.

- **Zaawansowana obsługa grafiki i animacje**. WPF upraszcza programowanie grafiki, umożliwiając zarządzanie sceny animacji dla Ciebie; nie ma potrzeby martwić się o interpolacji warianty punktowego, renderowanie pętli i przetwarzania sceny. Ponadto WPF zapewnia obsługę testowania trafień i alfa składania.

- **Przyspieszanie sprzętowe**. System grafiki WPF wykorzystuje sprzęt graficzny w celu zminimalizowania użycia procesora CPU.

### <a name="2d-shapes"></a>2D kształtów

WPF zawiera bibliotekę typowych wektor 2D kształtów rysowanych, takich jak prostokąty i elipsy, które są wyświetlane na poniższej ilustracji:

![Wielokropki i prostokąty](../designers/media/wpfintrofigure4.PNG)

Interesujące możliwość kształtów jest, że nie są one tylko do wyświetlania; kształty zaimplementować wiele funkcji, których można oczekiwać od formantów, w tym klawiatury i myszy. W poniższym przykładzie przedstawiono <xref:System.Windows.UIElement.MouseUp> zdarzenia <xref:System.Windows.Shapes.Ellipse> jest obsługiwany.

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_8.cs)]

Na poniższej ilustracji pokazano, co jest generowany przez poprzedniego kodu.

![Okno z tekstem "kliknięto przycisk wielokropka&#33;"](../designers/media/wpfintrofigure12.png)

Aby uzyskać więcej informacji, zobacz [kształty i podstawowe Rysowanie w WPF — Przegląd](/dotnet/framework/wpf/data/data-binding-overview).

### <a name="2d-geometries"></a>2D geometrii

Kształty 2D, dostarczone przez WPF obejmują standardowy zestaw podstawowych kształtów. Jednak może być konieczne utworzenie kształty niestandardowe, aby ułatwić projektowanie interfejsu użytkownika. W tym celu WPF zapewnia geometrii. Na poniższym rysunku pokazano użycie geometrii, tworząc kształt niestandardowy, które mogą być rysowane bezpośrednio, używane jako pędzla lub umożliwia obcina inne kształty i kontrolek.

<xref:System.Windows.Shapes.Path> obiekty może służyć do rysowania kształtów zamknięty lub otwarte, wielu kształtów i nawet krzywych kształtów.

<xref:System.Windows.Media.Geometry> obiekty może służyć do wycinka testowania trafień i renderowania danych grafiki 2D.

![Różne przypadki użycia ścieżki](../designers/media/wpfintrofigure5.png)

Aby uzyskać więcej informacji, zobacz [Przegląd Geometria](/dotnet/framework/wpf/graphics-multimedia/geometry-overview).

### <a name="2d-effects"></a>Efekty 2D

Niektóre funkcje 2D WPF zawiera efekty wizualne, takie jak gradientów, mapy bitowe, rysunki, malowanie przy użyciu wideo, obracanie, skalowanie i pochylanie. Te są wszystkie wykonywane przy użyciu pędzli; na poniższej ilustracji przedstawiono kilka przykładów.

![Ilustracja różnych pędzli](../designers/media/wpfintrofigure6.png)

Aby uzyskać więcej informacji, zobacz [WPF pędzle Przegląd](/dotnet/framework/wpf/graphics-multimedia/wpf-brushes-overview).

### <a name="3d-rendering"></a>W renderingu 3D

WPF zawiera także możliwości renderowania 3W, które integrują się z grafika 2-d, aby umożliwić tworzenie atrakcyjnych i bardziej interesujące interfejsy użytkownika. Na przykład na poniższej ilustracji przedstawiono obrazów 2D renderowane 3W kształtów.

![Zrzut ekranu przedstawiający przykład Visual3D](../designers/media/wpfintrofigure13.png)

Aby uzyskać więcej informacji, zobacz [grafiki 3D — Przegląd](/dotnet/framework/wpf/graphics-multimedia/3-d-graphics-overview).

## <a name="animation"></a>Animacja

WPF animacji pomocy technicznej pozwala utworzyć formanty zwiększania, potrząśnij, pokrętła i zanikanie, aby utworzyć interesujące strony przejścia i nie tylko. Można animować większość klas WPF, nawet niestandardowych klas. Na poniższej ilustracji przedstawiono prostej animacji w akcji.

![Obrazy modułu animowane](../designers/media/wpfintrofigure7.png)

Aby uzyskać więcej informacji, zobacz [Przegląd animacja](/dotnet/framework/wpf/graphics-multimedia/animation-overview).

## <a name="media"></a>Nośnik

Jest jednym ze sposobów w celu przekazania sformatowanej zawartości przy użyciu nośnika audiowizualnych. WPF obsługuje specjalne obrazy, wideo i audio.

### <a name="images"></a>Obrazy

Obrazy są wspólne dla większości aplikacji, a WPF oferuje kilka sposobów, aby umożliwić ich używanie. Na poniższej ilustracji przedstawiono interfejs użytkownika z pola listy, który zawiera obrazy miniatur. Po wybraniu jednej z miniatur obraz jest wyświetlany w pełnym rozmiarze.

![Obrazy miniatur i pełne&#45;rozmiaru obrazu](../designers/media/wpfintrofigure8.png)

Aby uzyskać więcej informacji, zobacz [Przegląd obrazowanie](/dotnet/framework/wpf/graphics-multimedia/imaging-overview).

### <a name="video-and-audio"></a>Audio i wideo

<xref:System.Windows.Controls.MediaElement> Formantu może odtwarzać audio i wideo, i jest wystarczająco elastyczny, aby stanowić podstawę dla niestandardowych media player. Następujący kod XAML implementuje odtwarzacz multimediów.

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_9.xaml)]

Okno w poniższy rysunek przedstawia <xref:System.Windows.Controls.MediaElement> kontroli w działaniu.

![Formant MediaElement z audio i wideo](../designers/media/wpfintrofigure1.png)

Aby uzyskać więcej informacji, zobacz [grafika i multimedia](/dotnet/framework/wpf/graphics-multimedia).

## <a name="text-and-typography"></a>Tekst i typografii

W celu ułatwienia renderowanie tekstu wysokiej jakości, WPF, oferuje następujące funkcje:

- Obsługa czcionek OpenType.

- Ulepszenia ClearType.

- O wysokiej wydajności, który wykorzystuje przyspieszanie sprzętowe.

- Integracja tekstu za pomocą nośników, grafiki i animacje.

- Międzynarodowe czcionki mechanizmów obsługi i działania rezerwowego.

Jako pokaz integracji tekstu z grafiki na poniższej ilustracji przedstawiono aplikację ozdobniki tekstu.

![Tekst z różnych dekoracje tekstu](../designers/media/wpfintrofigure23.png)

Aby uzyskać więcej informacji, zobacz [typografii w oprogramowaniu Windows Presentation Foundation](/dotnet/framework/wpf/advanced/typography-in-wpf).

## <a name="customize-wpf-apps"></a>Dostosowywanie aplikacji WPF

Do tej pory przedstawiono podstawowe bloki konstrukcyjne WPF do tworzenia aplikacji. Model aplikacji umożliwia hostowanie i dostarczać zawartość aplikacji, która składa się głównie z formantów. Aby uprościć rozmieszczenie kontrolek w interfejsie użytkownika i upewnij się, że układ jest obsługiwana w przypadku zmiany rozmiaru okna i wyświetlić ustawienia, użyjesz system układu WPF. Ponieważ większość aplikacji pozwoli użytkownikom na interakcję z danymi, umożliwia powiązanie danych Zmniejsz ilość pracy integracji interfejsu użytkownika z danymi. Aby poprawić wygląd aplikacji, należy użyć kompleksowego zakresu grafiki, animacji i media pomoc techniczna jest świadczona przez WPF.

Często jednak podstawowe informacje nie są wystarczające do tworzenia i zarządzania naprawdę odrębne i niezrównane wizualnie środowiska użytkownika. Standardowych kontrolek WPF nie może zintegrować z pożądany wygląd aplikacji. Dane mogą nie być wyświetlane w najefektywniejszy sposób. Środowisko użytkownika ogólną aplikacji może nie być odpowiednie do domyślnego wyglądu i działania Windows motywów. Na wiele sposobów prezentacji technologiczne rozszerzeń programu visual jak dowolny inny typ rozszerzalności.

Z tego powodu WPF zawiera szereg mechanizmów do tworzenia środowisk unikatowych użytkowników, w tym sformatowanego model zawartości kontrolki, wyzwalacze, kontroli i szablony danych, style, zasoby interfejsu użytkownika i motywy i skórki.

### <a name="content-model"></a>Model zawartości

Głównym celem większości kontrolek WPF jest do wyświetlania zawartości. W środowisku WPF typu i liczby elementów, które mogą stanowić zawartość kontrolki jest nazywany formantu *model zawartości*. Niektóre kontrolki mogą zawierać jeden element i typu zawartości; na przykład zawartość <xref:System.Windows.Controls.TextBox> jest wartość ciągu, która jest przypisana do <xref:System.Windows.Controls.TextBox.Text%2A> właściwości. W poniższym przykładzie ustawiono zawartość <xref:System.Windows.Controls.TextBox>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

Na poniższej ilustracji przedstawiono wyniki.

![Formant pola tekstowego, który zawiera tekst](../designers/media/wpfintrofigure21.png)

Jednak inne kontrolki, może zawierać wiele elementów różnych typów zawartości; zawartość <xref:System.Windows.Controls.Button>, określony przez <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości mogą zawierać różne elementy, takie jak układ kontrolki, tekst, obrazy i kształty. W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Button> z zawartością, która obejmuje <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>, a <xref:System.Windows.Controls.MediaElement>.

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

Aby uzyskać więcej informacji na temat rodzajów zawartości, który jest obsługiwany przez różne formanty, zobacz [model zawartości WPF](/dotnet/framework/wpf/controls/wpf-content-model).

### <a name="triggers"></a>Wyzwalacze

Mimo że głównym celem znaczników XAML do zaimplementowania wygląd aplikacji umożliwia także XAML do zaimplementowania niektóre aspekty zachowania aplikacji. Przykładem jest użycie wyzwalaczy, aby zmienić wygląd aplikacji na podstawie interakcji użytkownika. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="control-templates"></a>Szablony kontrolek

Domyślne interfejsów użytkownika dla kontrolek WPF zwykle są konstruowane na podstawie innych formantów i kształtów. Na przykład <xref:System.Windows.Controls.Button> składa się z obu <xref:Microsoft.Windows.Themes.ButtonChrome> i <xref:System.Windows.Controls.ContentPresenter> kontrolki. <xref:Microsoft.Windows.Themes.ButtonChrome> Zawiera przycisk standardowy wygląd, podczas gdy <xref:System.Windows.Controls.ContentPresenter> Wyświetla zawartość przycisku zgodnie z <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości.

Czasami może być incongruent ogólnego wyglądu aplikacji domyślny wygląd kontrolki. W takim przypadku można użyć <xref:System.Windows.Controls.ControlTemplate> zmieniać wygląd kontrolki interfejsu użytkownika bez wprowadzania zmian w jej zawartości i zachowania.

Na przykład, poniższy przykład pokazuje, jak zmienić wygląd <xref:System.Windows.Controls.Button> przy użyciu <xref:System.Windows.Controls.ControlTemplate>.

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_17.vb)]

W tym przykładzie został zastąpiony domyślnym interfejsem użytkownika przycisk <xref:System.Windows.Shapes.Ellipse> który ma ciemny niebieskie obramowanie i jest wypełniony przy użyciu <xref:System.Windows.Media.RadialGradientBrush>. <xref:System.Windows.Controls.ContentPresenter> Kontrolka Wyświetla zawartość <xref:System.Windows.Controls.Button>, "Kliknij mnie!" Gdy <xref:System.Windows.Controls.Button> po kliknięciu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie jest zgłaszane w dalszym ciągu jako część <xref:System.Windows.Controls.Button> kontrolki zachowanie domyślne. Wynik jest wyświetlany na poniższej ilustracji:

![Eliptyczny przycisk i drugie okno](../designers/media/wpfintrofigure2.png)

### <a name="data-templates"></a>Szablony danych

Natomiast szablon kontrolki umożliwia określenie wyglądu formantu, szablon danych umożliwia określenie wyglądu formantu zawartości. Szablony danych są często używane do zwiększenia jak powiązane dane jest wyświetlany. Poniższa ilustracja przedstawia domyślny wygląd <xref:System.Windows.Controls.ListBox> , jest powiązana z kolekcją `Task` obiektów, w którym każde zadanie ma nazwę, opis i priorytet.

![Pole listy z domyślny wygląd](../designers/media/wpfintrofigure18.png)

Domyślny wygląd to, czego można oczekiwać, od <xref:System.Windows.Controls.ListBox>. Jednakże domyślny wygląd każde zadanie zawiera tylko nazwę zadania. Aby wyświetlić nazwę zadania, opis i priorytet domyślny wygląd <xref:System.Windows.Controls.ListBox> elementów listy powiązane kontrolki należy zmienić przy użyciu <xref:System.Windows.DataTemplate>. Następujące XAML definiuje takie <xref:System.Windows.DataTemplate>, których są stosowane do każdego zadania przy użyciu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> atrybutu.

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

Na poniższej ilustracji przedstawiono wpływ ten kod.

![Pola listy, który używa szablonu danych](../designers/media/wpfintrofigure19.png)

Należy pamiętać, że <xref:System.Windows.Controls.ListBox> została zachowana jego zachowania i wyglądu ogólny; zmienił się tylko na wygląd zawartości są wyświetlane w polu listy.

Aby uzyskać więcej informacji, zobacz [Przegląd szablonowanie danych](/dotnet/framework/wpf/data/data-templating-overview).

### <a name="styles"></a>Style

Style Włącz deweloperów i projektantów do standaryzacji na określonym wygląd swojego produktu. WPF udostępnia model silne stylu, to podstawę <xref:System.Windows.Style> elementu. Poniższy przykład tworzy styl, który ustawia kolor tła dla każdego <xref:System.Windows.Controls.Button> na okno, aby `Orange`.

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

Ponieważ ten styl jest przeznaczony dla wszystkich <xref:System.Windows.Controls.Button> kontrolek, stylów jest automatycznie stosowany do wszystkich przycisków w oknie, jak pokazano na poniższej ilustracji:

![Dwa przyciski pomarańczowy](../designers/media/wpfintrofigure20.png)

Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="resources"></a>Zasoby

Kontrolki w aplikacji powinny mieć tego samego wygląd, który może zawierać żadnych z czcionki i kolory tła, w celu kontrolowania szablonów, szablony danych i style. Do hermetyzacji tych zasobów w obrębie jednej lokalizacji do ponownego wykorzystania, można użyć w WPF Obsługa zasoby interfejsu użytkownika.

W poniższym przykładzie zdefiniowano wspólnej kolor tła, który jest współużytkowany przez <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Label>.

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

W tym przykładzie implementuje zasób koloru tła przy użyciu `Window.Resources` elementu właściwości. Ten zasób jest dostępny dla wszystkich obiektów podrzędnych <xref:System.Windows.Window>. Istnieje wiele zasobów zakresy, w tym następujące czynności, wymienione w kolejności, w którym są one rozwiązane:

1. Poszczególnych kontrolek (przy użyciu dziedziczonego <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> właściwości).

2. A <xref:System.Windows.Window> lub <xref:System.Windows.Controls.Page> (również przy użyciu dziedziczonego <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> właściwości).

3. <xref:System.Windows.Application> (Przy użyciu <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> właściwości).

Różne zakresy zapewnia elastyczność w odniesieniu do sposobu, w którym do definiowania i udostępniać swoje zasoby.

Zamiast bezpośrednio kojarzenie zasobów z określonego zakresu, można spakować jeden lub więcej zasobów za pomocą oddzielnego <xref:System.Windows.ResourceDictionary> , może być przywoływany w innych częściach aplikacji. Na przykład w poniższym przykładzie zdefiniowano domyślny kolor tła w słowniku zasobów.

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

 Poniższy przykład odwołuje się do słownika zasobów, zdefiniowane w poprzednim przykładzie, dzięki czemu jest udostępniany przez aplikację.

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

Zasoby i słowniki zasobów są podstawą Obsługa platformy WPF dla motywów i skórki.

Aby uzyskać więcej informacji, zobacz [zasobów](/dotnet/framework/wpf/advanced/xaml-resources).

### <a name="custom-controls"></a>Kontrolki niestandardowe

Mimo że WPF oferuje obsługę dostosowania, możesz napotkać sytuacje, gdzie istniejących kontrolek WPF nie spełnia wymagań aplikacji i jej użytkownikach. Taka sytuacja może wystąpić jeśli:

- Nie można utworzyć interfejsu użytkownika, która jest wymagana przez dostosowanie wyglądu i działania istniejących implementacji WPF.

- Zachowanie, która jest wymagana jest nieobsługiwane lub nie jest obsługiwana przez istniejących implementacji WPF.

W tym momencie, możesz korzystać z zalet jeden z trzech modele WPF, aby utworzyć nową kontrolkę. Każdy model jest przeznaczony dla konkretnego scenariusza i wymaga niestandardową kontrolkę pochodzić z klasy bazowej konkretnego WPF. Poniżej przedstawiono trzy modele:

- **Model kontroli użytkownika**. Formant niestandardowy jest pochodną <xref:System.Windows.Controls.UserControl> i składa się z co najmniej jedną kontrolkę.

- **Model sterowania**. Formant niestandardowy jest pochodną <xref:System.Windows.Controls.Control> i jest używany do tworzenia implementacji, które oddzielić ich zachowania z ich wygląd przy użyciu szablonów, podobnie jak w większości kontrolek WPF. Wyprowadzanie z <xref:System.Windows.Controls.Control> umożliwia większą swobodę do tworzenia niestandardowego interfejsu użytkownika kontrolki użytkownika, ale mogą wymagać więcej nakładu pracy.

- **Model elementu Framework**. Formant niestandardowy jest pochodną <xref:System.Windows.FrameworkElement> po jego wygląd jest definiowany przez niestandardowe renderowanie logic (nie szablonów).

Poniższy przykład pokazuje niestandardowy liczbowe w górę/dół formant, który pochodzi od klasy <xref:System.Windows.Controls.UserControl>.

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/CSharp/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/VisualBasic/introduction-to-wpf_34.vb)]

Następny przykład ilustruje XAML, potrzebnego do dołączyć kontrolki użytkownika do <xref:System.Windows.Window>.

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_37.xaml)]

Poniższy rysunek przedstawia `NumericUpDown` sterowania hostowaną w <xref:System.Windows.Window>.

![Niestandardowe UserControl](../designers/media/wpfintrofigure3.png)

Aby uzyskać więcej informacji na temat kontrolek niestandardowych, zobacz [kontroli Przegląd autorstwa](/dotnet/framework/wpf/controls/control-authoring-overview).

## <a name="wpf-best-practices"></a>Najlepsze rozwiązania w WPF

Podobnie jak w przypadku dowolnej platformy programowania WPF można na wiele sposobów, aby osiągnąć oczekiwany rezultat. Jako sposób zapewnienia, że Twoje WPF aplikacji zapewniają środowisko użytkownika wymagane i spełniać odbiorców ogólnie rzecz biorąc, są zalecane najlepsze rozwiązania dotyczące ułatwień dostępu, globalizacji i lokalizacji i wydajności. Aby uzyskać więcej informacji, zobacz:

- [Ułatwienia dostępu](/dotnet/framework/ui-automation/accessibility-best-practices)
- [Lokalizacja i globalizacja WPF](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview)
- [Wydajność aplikacji WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Zabezpieczenia WPF](/dotnet/framework/wpf/security-wpf)

## <a name="next-steps"></a>Następne kroki

Omówiono kluczowe funkcje WPF. Teraz nadszedł czas, aby utworzyć pierwszą aplikację programu WPF.

> [!div class="nextstepaction"]
> [Przewodnik: Moja pierwsza aplikacja pulpitu WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)

## <a name="see-also"></a>Zobacz także

- [Rozpoczynanie pracy z aparatem WPF](../designers/getting-started-with-wpf.md)
- [Windows Presentation Foundation](/dotnet/framework/wpf/index)
- [Zasoby społeczności WPF](/dotnet/framework/wpf/getting-started/community-feedback)