---
title: Punkty rozszerzenia usługi językowej i edytora | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bb086eb99e4b8128c04f62f9b370eb2eab8fa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703057"
---
# <a name="language-service-and-editor-extension-points"></a>Punkty rozszerzenia usługi językowej i edytora
Edytor zawiera punkty rozszerzenia, które można rozszerzać jako części składników Managed Extensibility Framework (MEF), w tym większość funkcji usługi językowej. Są to główne kategorie punktów rozszerzenia:

- Typy zawartości

- Typy klasyfikacji i formaty klasyfikacji

- Marginesy i paski przewijania

- Tagi

- Zakończeń

- Procesory myszy

- Porzuć procedury obsługi

- Opcje

- IntelliSense

## <a name="extend-content-types"></a>Rozwiń typy zawartości
 Typy zawartości to definicje rodzajów tekstu obsługiwane przez Edytor, na przykład "text", "Code" lub "CSharp". Należy zdefiniować nowy typ zawartości przez zadeklarowanie zmiennej typu <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> i nadanie nowej zawartości typu unikatowej nazwy. Aby zarejestrować typ zawartości z edytorem, należy wyeksportować go wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> jest nazwą typu zawartości.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> jest nazwą typu zawartości, z którego pochodzi ten typ zawartości. Typ zawartości może dziedziczyć z wielu innych typów zawartości.

  Ponieważ <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Klasa jest zapieczętowana, można wyeksportować ją bez parametru typu.

  W poniższym przykładzie przedstawiono atrybuty eksportu w definicji typu zawartości.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Typy zawartości mogą być oparte na zerowych lub więcej istniejących typach zawartości. Są to typy wbudowane:

- Any: podstawowy typ zawartości. Elementy nadrzędne wszystkich typów zawartości.

- Text: typ podstawowy dla zawartości bez projekcji. Dziedziczy po "any".

- Zwykły tekst: dla tekstu niezwiązanego z kodem. Dziedziczy po "text".

- Kod: dla kodu dowolnego rodzaju. Dziedziczy po "text".

- Obojętny: wyklucza tekst z dowolnego rodzaju obsługi. Do tekstu tego typu zawartości nigdy nie zostanie zastosowane żadne rozszerzenie.

- Projekcja: dla zawartości buforów projekcji. Dziedziczy po "any".

- IntelliSense: dla zawartości IntelliSense. Dziedziczy po "text".

- Sighelp: Pomoc dotycząca podpisu. Dziedziczy po "IntelliSense".

- Sighelp-doc: Dokumentacja pomocy dotyczącej podpisu. Dziedziczy po "IntelliSense".

  Są to niektóre typy zawartości zdefiniowane przez program Visual Studio i niektóre Języki, które są obsługiwane w programie Visual Studio:

- Podstawowe

- C/C++

- ConsoleOutput

- CSharp

- CSS

- WEWNĘTRZNY

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  Aby odnaleźć listę dostępnych typów zawartości, zaimportuj <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> , która przechowuje kolekcję typów zawartości dla edytora. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Aby skojarzyć typ zawartości z rozszerzeniem nazwy pliku, użyj <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> .

> [!NOTE]
> W programie Visual Studio rozszerzenia nazw plików są rejestrowane przy użyciu <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> pakietu usługi językowej. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>Kojarzy typ zawartości MEF z rozszerzeniem nazwy pliku, który został zarejestrowany w ten sposób.

 Aby wyeksportować rozszerzenie nazwy pliku do definicji typu zawartości, należy uwzględnić następujące atrybuty:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Określa rozszerzenie nazwy pliku.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: określa typ zawartości.

  Ponieważ <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Klasa jest zapieczętowana, można wyeksportować ją bez parametru typu.

  Poniższy przykład pokazuje eksportowanie atrybutów rozszerzenia nazwy pliku do definicji typu zawartości.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>Zarządza skojarzeniami między rozszerzeniami nazw plików a typami zawartości.

## <a name="extend-classification-types-and-classification-formats"></a>Rozszerzone typy klasyfikacji i formaty klasyfikacji
 Możesz użyć typów klasyfikacji do zdefiniowania rodzaju tekstu, dla którego chcesz zapewnić inną obsługę (na przykład Kolorowanie tekstu "słowo kluczowe" jako niebieskie i tekstu "komentarz" zielony). Definiowanie nowego typu klasyfikacji przez zadeklarowanie zmiennej typu <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> i nadanie jej unikatowej nazwy.

 Aby zarejestrować typ klasyfikacji w edytorze, należy wyeksportować ją wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa typu klasyfikacji.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: nazwa typu klasyfikacji, z którego dziedziczy ten typ klasyfikacji. Wszystkie typy klasyfikacji dziedziczą z "text", a typ klasyfikacji może dziedziczyć z wielu innych typów klasyfikacji.

  Ponieważ <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> Klasa jest zapieczętowana, można wyeksportować ją bez parametru typu.

  W poniższym przykładzie przedstawiono atrybuty eksportu w definicji typu klasyfikacji.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>Zapewnia dostęp do klasyfikacji standardowych. Wbudowane typy klasyfikacji obejmują:

- Opis

- "język naturalny" (pochodzi od "tekst")

- "Język formalny" (pochodzi od "tekst")

- "String" (pochodzi od "literal")

- "Character" (pochodzi od "literal")

- "numeryczne" (pochodny od "literal")

  Zestaw różnych typów błędów dziedziczy z <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> . Obejmują one następujące typy błędów:

- "błąd składniowy"

- "błąd kompilatora"

- "inny błąd"

- wyświetlania

  Aby odnaleźć listę dostępnych typów klasyfikacji, zaimportuj <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> , która przechowuje kolekcję typów klasyfikacji dla edytora. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Można zdefiniować definicję formatu klasyfikacji dla nowego typu klasyfikacji. Utwórz klasę z <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> i wyeksportuj ją z typem <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa formatu.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: Nazwa wyświetlana formatu.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: określa, czy format pojawia się na stronie **czcionki i kolory** okna dialogowego **Opcje** .

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: priorytet formatu. Prawidłowe wartości należą do <xref:Microsoft.VisualStudio.Text.Classification.Priority> .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: nazwa typu klasyfikacji, do którego jest mapowany ten format.

  W poniższym przykładzie przedstawiono atrybuty eksportu w definicji formatu klasyfikacji.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Aby odnaleźć listę dostępnych formatów, zaimportuj <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> , która przechowuje kolekcję formatów dla edytora. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Zwiększ marginesy i paski przewijania
 Marginesy i paski przewijania są elementami widoku głównego edytora oprócz samego widoku tekstu. Oprócz standardowych marginesów, które pojawiają się wokół widoku tekstu, można podać dowolną liczbę marginesów.

 Implementowanie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interfejsu w celu zdefiniowania marginesu. Aby utworzyć margines, należy również zaimplementować <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfejs.

 Aby zarejestrować dostawcę marginesu przy użyciu edytora, należy wyeksportować dostawcę wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa marginesu.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność, w której jest wyświetlany margines względem innych marginesów.

   Są to wbudowane marginesy:

  - "Pasek przewijania w poziomie WPF"

  - "Pionowy pasek przewijania WPF"

  - "Margines numeru linii WPF"

    Poziome marginesy, które mają atrybut Order, `After="Wpf Horizontal Scrollbar"` są wyświetlane poniżej wbudowanego marginesu, a poziome marginesy, które mają atrybut kolejności, `Before ="Wpf Horizontal Scrollbar"` są wyświetlane powyżej wbudowanego marginesu. Prawe pionowe marginesy, które mają atrybut Order () `After="Wpf Vertical Scrollbar"` są wyświetlane po prawej stronie paska przewijania. Lewe marginesy pionowe, których atrybut Order `After="Wpf Line Number Margin"` jest wyświetlany po lewej stronie marginesu numeru wiersza (jeśli jest widoczny).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: rodzaj marginesu (lewy, prawy, górny lub dolny).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "Code"), dla której margines jest prawidłowy.

  Poniższy przykład pokazuje eksport atrybutów dla dostawcy marginesu dla marginesu, który pojawia się po prawej stronie marginesu numeru wiersza.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Rozwiń Tagi
 Tagi są sposobem kojarzenia danych z różnymi rodzajami tekstu. W wielu przypadkach skojarzone dane są wyświetlane jako efekt wizualny, ale nie wszystkie Tagi mają wizualną prezentację. Można zdefiniować własny rodzaj tagu przez implementację <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Należy również zaimplementować <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> , aby udostępnić Tagi dla danego zestawu tekstu, i <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> Aby zapewnić moduł tagujący. Należy wyeksportować dostawcę moduł tagujący wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "Code"), dla której tag jest prawidłowy.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: rodzaj tagu.

  W poniższym przykładzie przedstawiono atrybuty eksportu dostawcy moduł tagujący.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> następujących rodzajów tagów są wbudowane:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: skojarzone z <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: skojarzone z typami błędów.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: skojarzone z modułem definiowania układu.

  > [!NOTE]
  > Aby zapoznać się z przykładem <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> , Zobacz definicję HighlightWordTag w [przewodniku: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: skojarzone z regionami, które mogą być rozwijane lub zwijane w ramach konspektu.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: określa miejsce, w którym jest zajmowane w widoku tekstu. Aby uzyskać więcej informacji na temat wynegocjowania obszarów, zobacz następującą sekcję.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: zapewnia automatyczne odstępy i rozmiary dla definiowania układu.

  Aby znaleźć i użyć tagów dla buforów i widoków, zaimportuj <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> lub <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> , która daje <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> żądany typ. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Tagi i MarkerFormatDefinitions
 Można zwiększyć klasę, <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> Aby zdefiniować wygląd znacznika. Należy wyeksportować klasę (jako <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> ) z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa używana do odwoływania się do tego formatu

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: powoduje, że format pojawia się w interfejsie użytkownika

  W Konstruktorze należy zdefiniować nazwę wyświetlaną i wygląd znacznika. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> definiuje kolor wypełnienia i <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> definiuje kolor obramowania. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>Jest to lokalizowalna Nazwa definicji formatu.

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

 Aby zastosować tę definicję formatu do tagu, należy odwołać się do nazwy, którą ustawisz w atrybucie nazwy klasy (a nie nazwy wyświetlanej).

> [!NOTE]
> Aby zapoznać się z przykładem <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> , zobacz Klasa HighlightWordFormatDefinition w [instruktażu: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Poszerzenie modułów definiowania układu
 Elementy definiowania układu definiują efekty wizualne, które można dodać do tekstu wyświetlanego w widoku tekstu lub do samego widoku tekstu. Możesz zdefiniować własny moduł definiowania układu jako dowolny typ <xref:System.Windows.UIElement> .

 W klasie zakończenia należy zadeklarować <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> . Aby zarejestrować warstwę definiowania układu, należy wyeksportować ją wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa definiowania układu.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność definiowania układu w odniesieniu do innych warstw zakończenia. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definiuje cztery warstwy domyślne: zaznaczenie, obramowanie, karetka i tekst.

  W poniższym przykładzie przedstawiono atrybuty eksportu dla definicji warstwy definiowania układu.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Należy utworzyć drugą klasę, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> i obsługuje swoje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> zdarzenie, tworząc Tworzenie modułu definiowania układu. Należy wyeksportować tę klasę wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "Code"), dla której jest prawidłowym modułem definiowania układu.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: rodzaj widoku tekstu, dla którego jest prawidłowy ten moduł definiowania układu. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> zawiera zestaw wstępnie zdefiniowanych ról widoku tekstu. Na przykład <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> jest używany głównie do wyświetlania tekstu plików. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> służy do wyświetlania widoków tekstowych, które użytkownik może edytować lub nawigować przy użyciu myszy i klawiatury. Przykłady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> widoków to widok tekstu edytora i okno **dane wyjściowe** .

  Poniższy przykład pokazuje eksportowanie atrybutów dostawcy zakończenia.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Wynegocjowanie odstępu jest takie, że zajmuje miejsce na tym samym poziomie co tekst. Aby utworzyć ten rodzaj definiowania, należy zdefiniować klasę tagu, która dziedziczy z <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> , która definiuje ilość miejsca, w którym zajmowany jest moduł definiowania układu.

 Podobnie jak w przypadku wszystkich zakończenia, należy wyeksportować definicję warstwy definiowania układu.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Aby utworzyć wystąpienie dla wynegocjowania przestrzeni, należy utworzyć klasę, która implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , oprócz klasy, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (podobnie jak w przypadku innych rodzajów elementów definiowania).

 Aby zarejestrować dostawcę moduł tagujący, należy wyeksportować go wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "Code"), dla której jest prawidłowy moduł definiowania układu.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: rodzaj widoku tekstu, dla którego ten tag lub znacznik jest prawidłowy. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> zawiera zestaw wstępnie zdefiniowanych ról widoku tekstu. Na przykład <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> jest używany głównie do wyświetlania tekstu plików. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> służy do wyświetlania widoków tekstowych, które użytkownik może edytować lub nawigować przy użyciu myszy i klawiatury. Przykłady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> widoków to widok tekstu edytora i okno **dane wyjściowe** .

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: rodzaj zdefiniowanego tagu lub definiowania. Należy dodać sekundę <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> dla <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  W poniższym przykładzie pokazano eksport atrybutów dostawcy moduł tagujący w celu wynegocjowania odstępu.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Rozszerzanie procesorów myszy
 Możesz dodać obsługę specjalną dla danych wejściowych myszy. Utwórz klasę, która dziedziczy po <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> i Zastąp zdarzenia myszy dla danych wejściowych, które chcesz obsłużyć. Należy również zaimplementować <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> w drugiej klasie i wyeksportować ją wraz z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> określeniem rodzaju zawartości (na przykład "text" lub "Code"), dla której program obsługi myszy jest prawidłowy.

 Poniższy przykład przedstawia atrybuty eksportu dla dostawcy procesora myszy.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Rozwiń procedury obsługi upuszczania
 Można dostosować zachowanie procedur upuszczania dla określonych rodzajów tekstu przez utworzenie klasy implementującej <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> i drugiej klasy implementującej <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> procedurę obsługi upuszczania. Należy wyeksportować procedurę obsługi Drop wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: format tekstu, dla którego ta procedura obsługi upuszczania jest prawidłowa. Następujące formaty są obsługiwane w kolejności priorytetu od najwyższego do najniższego:

  1. Dowolny format niestandardowy

  2. FileDrop

  3. EnhancedMetafile

  4. WaveAudio

  5. RIFF

  6. DIF

  7. Regionalne

  8. Palety

  9. PenData

  10. Serializable

  11. SymbolicLink

  12. Formatu

  13. XamlPackage

  14. TIFF

  15. Mapy

  16. Format

  17. MetafilePicture

  18. CSV

  19. System. String

  20. Format HTML

  21. UnicodeText

  22. OEMText

  23. Tekst

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa procedury obsługi upuszczania.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: porządkowanie procedury obsługi upuszczania przed lub po domyślnym obsłudze upuszczania. Domyślna procedura obsługi upuszczania dla programu Visual Studio nosi nazwę "DefaultFileDropHandler".

  W poniższym przykładzie przedstawiono atrybuty eksportu dla dostawcy obsługi upuszczania.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Rozszerzanie opcji edytora
 Można zdefiniować opcje, które będą prawidłowe tylko w określonym zakresie, na przykład w widoku tekstu. Edytor udostępnia ten zestaw wstępnie zdefiniowanych opcji: Opcje edytora, Opcje widoku i opcje widoku Windows Presentation Foundation (WPF). Te opcje można znaleźć w <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> , <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> i <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 Aby dodać nową opcję, należy utworzyć klasę z jednej z następujących klas definicji opcji:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Poniższy przykład pokazuje, jak wyeksportować definicję opcji, która ma wartość logiczną.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Rozszerzona funkcja IntelliSense
 Technologia IntelliSense jest ogólnym terminem dla grupy funkcji, które dostarczają informacje na temat strukturalnego tekstu i uzupełniania instrukcji. Te funkcje obejmują uzupełnianie instrukcji, pomoc dotyczącą podpisu, szybkie informacje i żarówki. Uzupełnianie instrukcji ułatwia użytkownikom prawidłowe wpisanie słowa kluczowego języka lub nazwy elementu członkowskiego. Pomoc dotycząca podpisu służy do wyświetlania podpisu lub podpisów dla metody, która właśnie została wpisana przez użytkownika. Szybkie informacje wyświetla pełny podpis dla nazwy typu lub elementu członkowskiego, gdy wskaźnik myszy jest na nim włączony. Żarówka zapewnia dodatkowe akcje dla pewnych identyfikatorów w niektórych kontekstach, na przykład zmiany nazwy wszystkich wystąpień zmiennej po zmianie nazwy jednego wystąpienia.

 Projektowanie funkcji IntelliSense jest znacznie takie samo we wszystkich przypadkach:

- *Broker* IntelliSense jest odpowiedzialny za cały proces.

- *Sesja* IntelliSense reprezentuje sekwencję zdarzeń między wyzwalaniem prezentera a zatwierdzeniem lub anulowaniem zaznaczenia. Sesja jest zazwyczaj wyzwalana przez określonego gestu użytkownika.

- *Kontroler* IntelliSense jest odpowiedzialny za decydowanie o tym, kiedy sesja powinna się rozpocząć i zakończyć. Decyduje również o tym, kiedy informacje powinny być zatwierdzone i kiedy sesja powinna zostać anulowana.

- *Źródło* IntelliSense zapewnia zawartość i decyduje o najlepszej zgodności.

- *Prezenter* IntelliSense jest odpowiedzialny za wyświetlanie zawartości.

  W większości przypadków Zalecamy dostarczenie co najmniej źródła i kontrolera. Możesz również podać prezentera, jeśli chcesz dostosować ekran.

### <a name="implement-an-intellisense-source"></a>Implementowanie źródła IntelliSense
 Aby dostosować źródło, należy zaimplementować jeden (lub więcej) następujących interfejsów źródłowych:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> został uznany za przestarzały <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 Ponadto należy zaimplementować dostawcę tego samego rodzaju:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> został uznany za przestarzały <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 Należy wyeksportować dostawcę wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa źródła.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "Code"), do której ma zastosowanie źródło.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność wyświetlania źródła (w odniesieniu do innych źródeł).

- W poniższym przykładzie przedstawiono atrybuty eksportu dla dostawcy źródłowego uzupełniania.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Aby uzyskać więcej informacji na temat implementowania źródeł IntelliSense, zobacz następujące przewodniki:

- [Przewodnik: wyświetlanie etykietek narzędzi sekcji szybkich informacji](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Przewodnik: Wyświetlanie pomocy dotyczącej podpisu](../extensibility/walkthrough-displaying-signature-help.md)

- [Przewodnik: Wyświetlanie instrukcji wyświetlania](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementowanie kontrolera IntelliSense
 Aby dostosować kontroler, należy zaimplementować <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interfejs. Ponadto należy zaimplementować dostawcę kontrolera wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa kontrolera.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "Code"), do której stosuje się kontroler.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność, w jakiej kontroler powinien zostać wyświetlony (w odniesieniu do innych kontrolerów).

  Poniższy przykład przedstawia atrybuty eksportu dla dostawcy kontrolera uzupełniania.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Więcej informacji o korzystaniu z kontrolerów IntelliSense można znaleźć w następujących przewodnikach:

- [Przewodnik: wyświetlanie etykietek narzędzi sekcji szybkich informacji](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
