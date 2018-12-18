---
title: Usługi językowej i edytora punkty rozszerzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0bcbef5094bd12392b7ea79865e1d28e2934a11e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743583"
---
# <a name="language-service-and-editor-extension-points"></a>Punkty rozszerzeń usługi językowej i edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor umożliwia punktów rozszerzeń, rozszerzających jako części składowe Managed Extensibility Framework (MEF), w tym większość funkcji usługi języka. Poniżej przedstawiono kategorie punktu rozszerzenia główne:  
  
-   Typy zawartości  
  
-   Typy klasyfikacji i formatów klasyfikacji  
  
-   Marginesy i paski przewijania  
  
-   Znaczniki  
  
-   Zakończeń  
  
-   Procesory myszy  
  
-   Listy programów obsługi  
  
-   Opcje  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>Rozszerzanie typów zawartości  
 Typy zawartości są definicje rodzaje tekstu obsługiwane przez edytor, na przykład, "text", "code" lub "CSharp". Definiowanie nowego typu zawartości przez zadeklarowanie zmiennej typu <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> podając unikatową nazwę nowego typu zawartości. Aby zarejestrować typ zawartości za pomocą edytora, należy go wyeksportować wraz z następującymi atrybutami:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> jest nazwą typu zawartości.  
  
- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> jest nazwą typu zawartości, z którego pochodzi ten typ zawartości. Typ zawartości może dziedziczyć z wieloma typami zawartości.  
  
  Ponieważ <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> klasa jest zapieczętowany, możesz wyeksportować go w przypadku braku parametrów typu.  
  
  Poniższy przykład pokazuje atrybuty eksportu w definicji typu zawartości.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Typy zawartości może bazować na zero lub więcej istniejących typów zawartości. Są to typy wbudowane:  
  
- Dowolny: podstawowego typu zawartości. Element nadrzędny dla wszystkich typów zawartości.  
  
- Tekst: podstawowy typ zawartości bez rzutowania. Dziedziczy po "dowolne".  
  
- Zwykły tekst: dla tekstu bez kodu. Dziedziczy po "text".  
  
- Kod: kod wszelkiego rodzaju. Dziedziczy po "text".  
  
- Obojętny: pomija tekst dowolnego rodzaju obsługi. Tekst tego typu zawartości nigdy nie będzie miała każde rozszerzenie stosowane do niego.  
  
- Projekcja: dla zawartość buforów projekcji. Dziedziczy po "dowolne".  
  
- IntelliSense: Aby uzyskać zawartość funkcji IntelliSense. Dziedziczy po "text".  
  
- Sighelp: pomocy dotyczącej sygnatur. Dziedziczy po "intellisense".  
  
- Sighelp-doc: Dokumentacja pomocy podpisu. Dziedziczy po "intellisense".  
  
  Poniżej przedstawiono niektóre typy zawartości, które są zdefiniowane przez program Visual Studio, a niektóre języki, które są hostowane w programie Visual Studio:  
  
- Podstawowy  
  
- C/C++  
  
- ConsoleOutput  
  
- CSharp  
  
- CSS  
  
- ENC  
  
- FindResults  
  
- F#  
  
- HTML  
  
- JScript  
  
- XAML  
  
- XML  
  
  Aby zobaczyć listę dostępnych typów zawartości, należy go zaimportować <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, który przechowuje kolekcję typów zawartości dla edytora. Poniższy kod importuje tej usługi, jako właściwość.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Aby skojarzyć typ zawartości z rozszerzeniem nazwy pliku, należy użyć <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  W programie Visual Studio, rozszerzenia nazw plików są zarejestrowane przy użyciu <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> w pakiecie usługi języka. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Kojarzy MEF typu zawartości z rozszerzeniem nazwy pliku, który został zarejestrowany w ten sposób.  
  
 Aby wyeksportować rozszerzenie nazwy pliku do definicji typu zawartości, musi zawierać następujące atrybuty:  
  
- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Określa rozszerzenie nazwy pliku.  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Określa typ zawartości.  
  
  Ponieważ <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> klasa jest zapieczętowany, możesz wyeksportować go w przypadku braku parametrów typu.  
  
  Poniższy przykład pokazuje atrybuty eksportu na rozszerzenie nazwy pliku do definicji typu zawartości.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> Zarządza skojarzeń rozszerzeń nazw plików i typy zawartości.  
  
## <a name="extending-classification-types-and-classification-formats"></a>Rozszerzanie typy klasyfikacji i klasyfikacji formatów  
 Typy klasyfikacji można użyć do definiowania rodzaje tekstu, dla którego chcesz zapewnić obsługę różnych (np. kolorowanie zielony niebieski tekst "— słowo kluczowe" i tekst "comment"). Definiowanie nowego typu klasyfikacji przez zadeklarowanie zmiennej typu <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> i unikatową nazwę.  
  
 Aby zarejestrować typ klasyfikacji, za pomocą edytora, należy go wyeksportować wraz z następującymi atrybutami:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa typu klasyfikacji.  
  
- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: Nazwa typu klasyfikacji, z której dziedziczy ten typ klasyfikacji. Wszystkie typy klasyfikacji dziedziczą "text", a typ klasyfikacji mogą dziedziczyć z wielu innych typów klasyfikacji.  
  
  Ponieważ <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> klasa jest zapieczętowany, możesz wyeksportować go w przypadku braku parametrów typu.  
  
  Poniższy przykład pokazuje atrybuty eksportu w definicji typu klasyfikacji.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> Zapewnia dostęp do standardowego klasyfikacji. Typy wbudowane klasyfikacji obejmują one:  
  
- "text"  
  
- "" języka naturalnego (pochodzi od klasy "text")  
  
- "język formalne" (pochodzi od klasy "text")  
  
- "string" (pochodzi od klasy "literal")  
  
- "character" (pochodzi od klasy "literal")  
  
- "numeryczny" (pochodzi od klasy "literal")  
  
  Zestaw typów inny błąd dziedziczyć <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Ulepszenia obejmują następujące typy błędów:  
  
- "Błąd składniowy"  
  
- "błąd kompilatora"  
  
- "inny błąd"  
  
- "ostrzeżenie"  
  
  Aby dowiedzieć się lista dostępnych typów klasyfikacji, należy zaimportować <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, przechowuje kolekcję typów klasyfikacji dla edytora. Poniższy kod importuje tej usługi, jako właściwość.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Definicja formatu klasyfikacji można zdefiniować nowego typu klasyfikacji. Wyprowadzić klasę z <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> i wyeksportuj go z typem <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, wraz z następującymi atrybutami:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa formatu.  
  
- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: Nazwa wyświetlana w formacie.  
  
- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Określa, czy format pojawia się na **czcionki i kolory** strony **opcje** okno dialogowe.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: priorytet format. Prawidłowe wartości to od <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: wpisz nazwę klasyfikacji, aby jest mapowany tego formatu.  
  
  Poniższy przykład pokazuje atrybuty eksportu w definicji formatu klasyfikacji.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Aby zobaczyć listę dostępnych formatów, należy go zaimportować <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, przechowuje kolekcję formatów dla edytora. Poniższy kod importuje tej usługi, jako właściwość.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>Rozszerzanie marginesy i paski przewijania  
 Marginesy i paski przewijania są elementami Widok główny Edytor oprócz samego widoku tekstu. Możesz podać dowolną liczbę marginesy oprócz standardowych marginesy, które pojawiają się wokół widoku tekstu.  
  
 Implementowanie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interfejs zdefiniowanie margines. Należy także zaimplementować <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfejs do tworzenia na marginesie.  
  
 Aby zarejestrować dostawcę margines, za pomocą edytora, należy wyeksportować dostawcy wraz z następującymi atrybutami:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa marginesu.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność, w którym jest wyświetlana margines, względem inne marginesy.  
  
   Poniżej przedstawiono wbudowane marginesy:  
  
  - "Wpf poziomy pasek przewijania."  
  
  - "Wpf pionowy pasek przewijania."  
  
  - "Margines numeru wiersza Wpf"  
  
    Marginesy poziomej, mających atrybut kolejności `After="Wpf Horizontal Scrollbar"` są wyświetlone poniżej margines wbudowanych i poziomy marginesy, mających atrybut kolejności `Before ="Wpf Horizontal Scrollbar"` są wyświetlane powyżej wbudowanych margines. Kliknij prawym przyciskiem myszy marginesów pionowych, które mają atrybut kolejności `After="Wpf Vertical Scrollbar"` są wyświetlane z prawej strony paska przewijania. LEFT marginesów pionowych, które mają atrybut kolejności `After="Wpf Line Number Margin"` pojawiają się po lewej stronie margines numer wiersza (jeśli jest ona widoczna).  
  
- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: typ margines (lewo, prawo, top lub bottom).  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla którego Twoja marginesu jest prawidłowy.  
  
  Poniższy przykład pokazuje atrybuty eksportu przez dostawcę margines na marginesie, na którym jest wyświetlany po prawej stronie na marginesie numeru wiersza.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Rozszerzenie znaczników  
 Tagi są sposobu kojarzenia danych z różnymi rodzajami tekstu. W wielu przypadkach powiązane dane jest wyświetlany jako efekt wizualny, ale nie wszystkie znaczniki mają wizualnej prezentacji. Można zdefiniować własne rodzaj tag implementując <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Należy także zaimplementować <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> zapewnienie tagi dla danego zestawu zakresy tekstu i <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> zapewnienie moduł tagujący. Należy wyeksportować dostawcy moduł tagujący wraz z następującymi atrybutami:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla którego tag jest prawidłowy.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: typ znacznika.  
  
  Poniższy przykład pokazuje atrybuty eksportu przez dostawcę moduł tagujący.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TagType(typeof(TestTag))]  
internal class TestTaggerProvider : ITaggerProvider  
```  
  
 Wbudowane są następujące rodzaje tagu:  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: skojarzone z <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: skojarzone z błędami.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: skojarzone z zakończeń.  
  
  > [!NOTE]
  >  Na przykład <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, zobacz definicję HighlightWordTag w [przewodnik: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md).  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: skojarzone z regionów, które mogą być rozwijane czy zwijane w tworzenie konspektu.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definiuje miejsce zajmuje zakończeń w widoku tekstu. Aby uzyskać więcej informacji na temat negocjowania miejsca zakończeń sekcji.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: oferuje automatyczne odstępy i rozmiarów zakończeń.  
  
  Aby znaleźć i za pomocą tagów dla buforów i widoków, zaimportuj <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> lub <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, które dają <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> żądanego typu. Poniższy kod importuje tej usługi, jako właściwość.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Znaczniki i MarkerFormatDefinitions  
 Możesz rozszerzyć <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> klasy w celu określenia jej wyglądu znacznika. Należy wyeksportować klasy (jako <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) z następującymi atrybutami:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa używana do odwoływać się do tego formatu  
  
- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: powoduje to, że format są wyświetlane w interfejsie użytkownika  
  
  W Konstruktorze można zdefiniować nazwę wyświetlaną i wyglądu znacznika. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> Określa kolor wypełnienia i <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> Określa kolor obramowania. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> Jest możliwa do zlokalizowania nazwę definicji formatu.  
  
  Oto przykład definicji formatu:  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 Aby zastosować tę definicję format tagu, należy odwoływać się do nazwy, ustawione w atrybucie nazwa klasy (nie nazwę wyświetlaną).  
  
> [!NOTE]
>  Na przykład <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, zobacz opis klasy HighlightWordFormatDefinition w [przewodnik: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extending-adornments"></a>Rozszerzanie zakończeń  
 Zakończeń zdefiniować efektów wizualnych, które można dodać w celu tekst, który jest wyświetlany w widoku tekstu lub w tekście wyświetlić sam. Można zdefiniować własne zakończeń jako dowolny typ <xref:System.Windows.UIElement>.  
  
 W klasie zakończeń, należy zadeklarować <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Aby zarejestrować warstwą zakończeń, należy go wyeksportować wraz z następującymi atrybutami:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa zakończeń.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: porządkowanie zakończeń w odniesieniu do innych warstw zakończeń. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definiuje cztery warstwy domyślne: wybór, tworzenie konspektu, karetki i tekst.  
  
  Poniższy przykład pokazuje atrybuty eksportu w definicji warstwy zakończeń.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Należy utworzyć druga klasa, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> i obsługuje jej <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> zdarzeń przez utworzenie wystąpienia zakończeń. Należy wyeksportować tej klasy, wraz z następującymi atrybutami:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla którego zakończeń jest prawidłowy.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: typ widoku tekstu, dla którego ten zakończeń jest prawidłowy. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> ma ustawioną tekstu wstępnie zdefiniowanego widoku ról. Na przykład <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> jest używany głównie dla widoków tekstu z plików. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> jest używana w widokach tekstu, czy użytkownik może edytować lub nawigować przy użyciu myszy i klawiatury. Przykłady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> widoki są widoku edytora tekstu i **dane wyjściowe** okna.  
  
  Poniższy przykład pokazuje atrybuty eksportu dla dostawcy zakończeń.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Negocjowanie miejsca zakończeń to taki, który zajmuje miejsce na tym samym poziomie jako tekst. Aby utworzyć ten rodzaj zakończeń, należy zdefiniować klasę tag, który dziedziczy z <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, która określa ilość miejsca na zajmuje zakończeń.  
  
 Podobnie jak w przypadku wszystkich zakończeń, możesz wyeksportować definicję warstwy zakończeń.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Do utworzenia wystąpienia zakończeń negocjowania miejsca, należy utworzyć klasę, która implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, oprócz klasy, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (tak jak inne rodzaje zakończeń).  
  
 Aby zarejestrować dostawcę moduł tagujący, należy go wyeksportować wraz z następującymi atrybutami:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla którego Twoja zakończeń jest prawidłowy.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: typ widoku tekstu, dla których ten tag lub zakończeń są prawidłowe. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> ma ustawioną tekstu wstępnie zdefiniowanego widoku ról. Na przykład <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> jest używany głównie dla widoków tekstu z plików. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> jest używana w widokach tekstu, czy użytkownik może edytować lub nawigować przy użyciu myszy i klawiatury. Przykłady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> widoki są widoku edytora tekstu i **dane wyjściowe** okna.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: rodzaj tag lub zakończeń, które zostały zdefiniowane. Należy dodać drugi <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> dla <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
  Poniższy przykład pokazuje atrybuty eksportu dla dostawcy moduł tagujący tagu zakończeń negocjowania miejsca.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Rozszerzanie procesorów myszy  
 Możesz dodać specjalna obsługa myszy dane wejściowe. Utwórz klasę, która dziedziczy z <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> i Zastąp zdarzenia myszy na dane wejściowe, które ma obsługiwać. Należy także zaimplementować <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> klasy sekundę i wyeksportuj go razem z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , który określa rodzaj zawartości (na przykład "text" lub "code"), dla którego programu obsługi myszy jest prawidłowy.  
  
 Poniższy przykład pokazuje atrybuty eksportu przez dostawcę procesora myszy.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Rozszerzanie listy programów obsługi  
 Można dostosować zachowanie bezpośredniej obsługi dla różnych rodzajów tekstu, tworząc klasę, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> i druga klasa, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> do utworzenia programu obsługi listy. Należy wyeksportować obsługi listy wraz z następującymi atrybutami:  
  
- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: format tekstu, dla którego ten program obsługi listy jest prawidłowy. Następujące formaty są obsługiwane w kolejności priorytetu od najwyższego do najniższego:  
  
  1.  Dowolny niestandardowy format  
  
  2.  FileDrop  
  
  3.  EnhancedMetafile  
  
  4.  WaveAudio  
  
  5.  RIFF  
  
  6.  DIF  
  
  7.  Regionalne  
  
  8.  Paleta  
  
  9. PenData  
  
  10. Możliwy do serializacji  
  
  11. SymbolicLink  
  
  12. XAML  
  
  13. XamlPackage  
  
  14. TIFF  
  
  15. Mapy bitowej  
  
  16. Dib  
  
  17. MetafilePicture  
  
  18. CSV  
  
  19. System.String  
  
  20. HTML Format  
  
  21. UnicodeText  
  
  22. OEMText  
  
  23. Tekst  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa procedury obsługi listy.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: porządkowanie obsługi listy przed lub po listy domyślny program obsługi. Domyślny program obsługi listy dla programu Visual Studio ma nazwę "DefaultFileDropHandler".  
  
  Poniższy przykład pokazuje atrybuty eksportu przez dostawcę obsługi listy.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Rozszerzenie Opcje edytora  
 Można zdefiniować opcje, które mają obowiązywać tylko w określonym zakresie, na przykład, w widoku tekstu. Edytor umożliwia ten zestaw wstępnie zdefiniowanych opcji: Opcje edytora, opcje wyświetlania i opcje wyświetlania Windows Presentation Foundation (WPF). Te opcje można znaleźć w <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, i <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Aby dodać nową opcję, należy wyprowadzić klasę z jednego z tych klas definicji opcji:  
  
- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
  Poniższy przykład pokazuje, jak do wyeksportowania definicji opcji, która ma wartość typu Boolean.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>Rozszerzanie funkcji IntelliSense  
 Funkcja IntelliSense jest ogólnym terminem dla grupy, funkcji, które zawierają informacje o tekst ze strukturą i uzupełnianie instrukcji. Funkcje te obejmują uzupełniania instrukcji, pomocy dotyczącej sygnatur, szybkie informacje i żarówki. Uzupełnianie instrukcji pomaga użytkownikom poprawnie wpisz nazwę elementu członkowskiego lub słowo kluczowe języka. Pomocy dotyczącej sygnatur Wyświetla podpis lub podpisów dla metody, która właśnie został wpisany przez użytkownika. Szybkie informacje wyświetlają pełną podpisu dla nazwy typu lub elementu członkowskiego, gdy wskaźnik myszy opiera się na nim. Ikona żarówki zapewniają dodatkowe akcje dla niektórych identyfikatorów w pewnych kontekstach, na przykład, zmiana nazwy wszystkie wystąpienia zmiennej po zmianie nazwy jedno wystąpienie.  
  
 Projekt funkcję mechanizmu IntelliSense jest bardzo podobne do we wszystkich przypadkach:  
  
- Funkcja IntelliSense *brokera* jest odpowiedzialny za cały proces.  
  
- Funkcja IntelliSense *sesji* reprezentuje sekwencję zdarzeń między wyzwolenie Prezenter i committal lub anulowanie zaznaczenia. Sesja jest zazwyczaj wyzwalany przez niektóre gestu użytkownika.  
  
- Funkcja IntelliSense *kontrolera* odpowiada decydujące o tym, kiedy sesja powinna rozpoczęcia i zakończenia. Także decyduje, gdy informacje powinny być zatwierdzone i po sesji powinna zostać anulowana.  
  
- Funkcja IntelliSense *źródła* udostępnia zawartość i decyduje o najlepsze dopasowanie.  
  
- Funkcja IntelliSense *prezentera* odpowiada za wyświetlanie zawartości.  
  
  W większości przypadków firma Microsoft zaleca, aby zapewnić co najmniej jeden źródłowy i kontroler. Można również dołączyć Prelegenci, jeśli chcesz dostosować wyświetlanie.  
  
### <a name="implementing-an-intellisense-source"></a>Implementowanie źródłowego IntelliSense  
 Aby dostosować źródła, należy zaimplementować jedną (lub więcej) z następujących interfejsów źródła:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> przestarzała zastąpiona ceną <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Ponadto należy zaimplementować dostawcę tego samego rodzaju:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> przestarzała zastąpiona ceną <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Należy wyeksportować dostawcy wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa źródła.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), do której stosują się źródła.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność, w źródle powinny wyświetlania (w odniesieniu do innych źródeł).  
  
-   Poniższy przykład pokazuje atrybuty eksportu na ukończenie dostawcy źródła.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Aby uzyskać więcej informacji o implementowaniu źródeł IntelliSense zobacz następujące instruktaże:  
  
 [Przewodnik: wyświetlanie etykietek narzędzi SzybkieInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Przewodnik: wyświetlanie pomocy dotyczącej sygnatur](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Przewodnik: wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Wdrażanie kontrolera IntelliSense  
 Aby dostosować kontrolerem, należy zaimplementować <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interfejsu. Ponadto należy zaimplementować dostawcę kontrolera wraz z następującymi atrybutami:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa kontrolera.  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), do której stosują się kontrolera.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność kontroler powinien (w odniesieniu do innych kontrolerów).  
  
  Poniższy przykład pokazuje atrybuty eksportu przez dostawcę kontrolera ukończenia.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Aby uzyskać więcej informacji o korzystaniu z funkcji IntelliSense kontrolerów zobacz następujące instruktaże:  
  
 [Przewodnik: wyświetlanie etykietek narzędzi SzybkieInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

