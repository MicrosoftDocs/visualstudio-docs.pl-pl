---
title: Punkty rozszerzenia usługi językowej i edytora | Microsoft Docs
description: Dowiedz się więcej o punktach rozszerzenia w Visual Studio kodu, który można rozszerzyć, w tym o większości funkcji usługi językowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 293851f1f3e72508a9bc119fb7551b0118ab2a9b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903150"
---
# <a name="language-service-and-editor-extension-points"></a>Punkty rozszerzenia usługi językowej i edytora
Edytor udostępnia punkty rozszerzeń, które można rozszerzać Managed Extensibility Framework części składowych (MEF), w tym większość funkcji usługi językowej. Są to główne kategorie punktów rozszerzenia:

- Typy zawartości

- Typy klasyfikacji i formaty klasyfikacji

- Marginesy i paski przewijania

- Tagi

- Ozdoby

- Procesory myszy

- Upuszczanie programów obsługi

- Opcje

- IntelliSense

## <a name="extend-content-types"></a>Rozszerzanie typów zawartości
 Typy zawartości to definicje rodzajów tekstu obsługiwanych przez edytor, na przykład "text", "code" lub "CSharp". Nowy typ zawartości definiuje się, deklarując zmienną typu i nadając nowemu <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> typowi zawartości unikatową nazwę. Aby zarejestrować typ zawartości w edytorze, wyeksportuj go wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> to nazwa typu zawartości.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> to nazwa typu zawartości, z którego pochodzi ten typ zawartości. Typ zawartości może dziedziczyć z wielu innych typów zawartości.

  Ponieważ klasa <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> jest zapieczętowana, można ją wyeksportować bez parametru typu.

  W poniższym przykładzie przedstawiono atrybuty eksportu dla definicji typu zawartości.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Typy zawartości mogą być oparte na zero lub większej liczby istniejących typów zawartości. Są to typy wbudowane:

- Dowolne: podstawowy typ zawartości. Element nadrzędny wszystkich innych typów zawartości.

- Tekst: podstawowy typ zawartości bez projekcji. Dziedziczy z "any".

- Zwykły tekst: w przypadku tekstu bez kodu. Dziedziczy z "text".

- Kod: dla kodu wszelkiego rodzaju. Dziedziczy z "text".

- Inert: wyklucza tekst z obsługi dowolnego rodzaju. Tekst tego typu zawartości nigdy nie będzie mieć żadnego rozszerzenia.

- Projekcja: dla zawartości buforów projekcji. Dziedziczy z "any".

- Intellisense: do zawartości funkcji IntelliSense. Dziedziczy z "text".

- Sighelp: pomoc przy podpisie. Dziedziczy z funkcji "intellisense".

- Sighelp-doc: dokumentacja pomocy dotyczącej sygnatur. Dziedziczy z funkcji "intellisense".

  Są to niektóre typy zawartości, które są zdefiniowane przez Visual Studio i niektóre języki, które są hostowane w Visual Studio:

- Podstawowa

- C/C++

- ConsoleOutput (KonsolaDysput)

- Csharp

- CSS

- Enc

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  Aby odnaleźć listę dostępnych typów zawartości, zaimportuj typ , który przechowuje <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> kolekcję typów zawartości dla edytora. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Aby skojarzyć typ zawartości z rozszerzeniem nazwy pliku, <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> użyj .

> [!NOTE]
> W Visual Studio rozszerzenia nazw plików są rejestrowane przy użyciu narzędzia <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> w pakiecie usługi językowej. Typ zawartości MEF jest kojarzony z rozszerzeniem nazwy pliku, <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> które zostało zarejestrowane w ten sposób.

 Aby wyeksportować rozszerzenie nazwy pliku do definicji typu zawartości, należy uwzględnić następujące atrybuty:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: określa rozszerzenie nazwy pliku.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: określa typ zawartości.

  Ponieważ klasa <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> jest zapieczętowana, można ją wyeksportować bez parametru typu.

  W poniższym przykładzie przedstawiono eksportowanie atrybutów rozszerzenia nazwy pliku do definicji typu zawartości.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 Zarządza <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> skojarzeniami między rozszerzeniami nazw plików i typami zawartości.

## <a name="extend-classification-types-and-classification-formats"></a>Rozszerzanie typów klasyfikacji i formatów klasyfikacji
 Za pomocą typów klasyfikacji można definiować rodzaje tekstu, dla których ma być zapewniana inna obsługa (na przykład kolorowanie tekstu "słowo kluczowe" w kolorze niebieskim i tekst "komentarz" na zielono). Zdefiniuj nowy typ klasyfikacji, deklarując zmienną typu i nadając <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> jej unikatową nazwę.

 Aby zarejestrować typ klasyfikacji w edytorze, wyeksportuj go wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa typu klasyfikacji.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: nazwa typu klasyfikacji, z którego dziedziczy ten typ klasyfikacji. Wszystkie typy klasyfikacji dziedziczą po "tekście", a typ klasyfikacji może dziedziczyć z wielu innych typów klasyfikacji.

  Ponieważ klasa <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> jest zapieczętowana, można ją wyeksportować bez parametru typu.

  W poniższym przykładzie przedstawiono atrybuty eksportu definicji typu klasyfikacji.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 Zapewnia <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> dostęp do klasyfikacji standardowych. Wbudowane typy klasyfikacji obejmują następujące typy:

- "text"

- "język naturalny" (pochodzi od "tekstu")

- "język formalny" (pochodzi od "tekstu")

- "string" (pochodzi od "literału")

- "znak" (pochodzi od "literału")

- "numeryczne" (pochodzi od "literału")

  Zestaw różnych typów błędów dziedziczy z <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> . Obejmują one następujące typy błędów:

- "błąd składniowy"

- "błąd kompilatora"

- "inny błąd"

- "warning"

  Aby odnaleźć listę dostępnych typów klasyfikacji, zaimportuj program , który przechowuje <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> kolekcję typów klasyfikacji dla edytora. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Dla nowego typu klasyfikacji można zdefiniować definicję formatu klasyfikacji. Wyeksportuj klasę z klasy <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> o <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> typie , wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa formatu.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: nazwa wyświetlana formatu.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: określa, czy format jest wyświetlany na stronie **Czcionki i** kolory okna **dialogowego** Opcje.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: priorytet formatu. Prawidłowe wartości to <xref:Microsoft.VisualStudio.Text.Classification.Priority> z .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: nazwa typu klasyfikacji, na który jest mapowany ten format.

  W poniższym przykładzie pokazano atrybuty eksportu definicji formatu klasyfikacji.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Aby odnaleźć listę dostępnych formatów, zaimportuj , który przechowuje <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> kolekcję formatów dla edytora. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Rozszerzanie marginesów i pasków przewijania
 Marginesy i paski przewijania to oprócz samego widoku tekstowego główne elementy widoku edytora. Oprócz standardowych marginesów wyświetlanych wokół widoku tekstu można podać dowolną liczbę marginesów.

 Implementowanie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interfejsu w celu zdefiniowania marginesu. Należy również zaimplementować <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfejs, aby utworzyć margines.

 Aby zarejestrować dostawcę marginesów w edytorze, należy wyeksportować dostawcę wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa marginesu.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność, w jakiej jest wyświetlany margines, względem innych marginesów.

   Są to wbudowane marginesy:

  - "Poziomy pasek przewijania Wpf"

  - "Pionowy pasek przewijania Wpf"

  - "Wpf Line Number Margin"

    Poziome marginesy z atrybutem order są wyświetlane poniżej wbudowanego marginesu, a poziome marginesy z atrybutem order są wyświetlane powyżej `After="Wpf Horizontal Scrollbar"` `Before ="Wpf Horizontal Scrollbar"` wbudowanego marginesu. Prawe marginesy pionowe z atrybutem order są `After="Wpf Vertical Scrollbar"` wyświetlane po prawej stronie paska przewijania. Lewe marginesy pionowe z atrybutem order są wyświetlane z lewej strony marginesu numeru wiersza `After="Wpf Line Number Margin"` (jeśli jest widoczny).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: rodzaj marginesu (lewy, prawy, górny lub dolny).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla której margines jest prawidłowy.

  Poniższy przykład przedstawia atrybuty eksportu u dostawcy marginesów dla marginesu wyświetlanego po prawej stronie marginesu numeru wiersza.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Rozszerzanie tagów
 Tagi to sposób kojarzenia danych z różnymi rodzajami tekstu. W wielu przypadkach skojarzone dane są wyświetlane jako efekt wizualny, ale nie wszystkie tagi mają prezentację wizualną. Możesz zdefiniować własny rodzaj tagu, implementując <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Należy również zaimplementować element w celu zapewnienia tagów dla danego zestawu zakresów tekstu oraz element w celu <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> zapewnienia tagowania. Należy wyeksportować dostawcę tagowania wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla której tag jest prawidłowy.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: rodzaj tagu.

  W poniższym przykładzie pokazano atrybuty eksportu dostawcy tagów.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> Następujące rodzaje tagów są wbudowane:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: skojarzone z <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> elementem .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: skojarzone z typami błędów.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: skojarzone z definiowaniem układu.

  > [!NOTE]
  > Aby uzyskać przykładowy element <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> , zobacz definicję HighlightWordTag w [przewodniku: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: skojarzone z regionami, które można rozwinąć lub zwinąć w zwijaniu.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definiuje miejsce zajmowane przez definiowanie układu w widoku tekstowym. Aby uzyskać więcej informacji o układach negocjowania przestrzeni, zobacz następującą sekcję.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: zapewnia automatyczne odstępy i zmiany rozmiaru dla układu.

  Aby znaleźć i użyć tagów dla buforów i widoków, zaimportuj element lub , który <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> daje typ <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> żądanego typu. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Tagi i markerFormatDefinitions
 Klasę można <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> rozszerzyć w celu zdefiniowania wyglądu tagu. Należy wyeksportować klasę (jako <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> klasę )z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa używana do odwołania się do tego formatu

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: powoduje to, że format jest wyświetlany w interfejsie użytkownika

  W konstruktorze definiuje się nazwę wyświetlaną i wygląd tagu. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> Definiuje kolor wypełnienia i <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> kolor obramowania. Jest <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> to nazwa definicji formatu, która może być zlokalizowane.

  Poniżej przedstawiono przykład definicji formatu:

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

 Aby zastosować tę definicję formatu do tagu, odwołaj się do nazwy ustawionej w atrybutie name klasy (a nie nazwie wyświetlanej).

> [!NOTE]
> Aby uzyskać przykład klasy <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> , zobacz klasę HighlightWordFormatDefinition w [przewodniku: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Rozszerzanie układów
 Definiowanie efektów wizualnych, które można dodać do tekstu wyświetlanego w widoku tekstowym lub do samego widoku tekstu. Własne definiowanie układu można zdefiniować jako dowolny typ <xref:System.Windows.UIElement> obiektu .

 W klasie definiowania układu należy zadeklarować <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> element . Aby zarejestrować warstwę definiowania, wyeksportuj ją wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa układu.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność układu w odniesieniu do innych warstw definiowania układu. Klasa definiuje <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> cztery warstwy domyślne: Wybór, Wytyczynie, Cyka i Tekst.

  W poniższym przykładzie pokazano atrybuty eksportu w definicji warstwy definiowania układu.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Należy utworzyć drugą klasę, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> i obsługuje jej zdarzenie przez utworzenie wystąpienia <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> układu. Należy wyeksportować tę klasę wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla której definiowanie jest prawidłowe.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: rodzaj widoku tekstowego, dla którego to definiowanie jest prawidłowe. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> ma zestaw wstępnie zdefiniowanych ról widoku tekstowego. Na przykład jest <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> używany głównie w przypadku widoków tekstowych plików. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Jest używany w przypadku widoków tekstowych, które użytkownik może edytować lub nawigować za pomocą myszy i klawiatury. Przykładami <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> widoków są widok tekstowy edytora i **okno Dane** wyjściowe.

  W poniższym przykładzie pokazano atrybuty eksportu w dostawcy definiowania układu.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Układ negocjowania przestrzeni to taki, który zajmuje miejsce na tym samym poziomie co tekst. Aby utworzyć tego rodzaju definiowanie, należy zdefiniować klasę tagu, która dziedziczy z klasy , która definiuje ilość miejsca zajmowanego przez <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> definiowanie.

 Podobnie jak w przypadku wszystkich układów, należy wyeksportować definicję warstwy definiowania.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Aby utworzyć wystąpienia układu negocjowania przestrzeni, należy utworzyć klasę, która implementuje , oprócz klasy, która implementuje (podobnie jak w przypadku innych rodzajów <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> definiowania układów).

 Aby zarejestrować dostawcę tagowania, należy wyeksportować go wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla której twoje definiowanie jest prawidłowe.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: rodzaj widoku tekstowego, dla którego ten tag lub układ jest prawidłowy. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> ma zestaw wstępnie zdefiniowanych ról widoku tekstowego. Na przykład jest <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> używany głównie w przypadku widoków tekstowych plików. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Jest używany w przypadku widoków tekstowych, które użytkownik może edytować lub nawigować za pomocą myszy i klawiatury. Przykładami <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> widoków są widok tekstowy edytora i **okno Dane** wyjściowe.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: rodzaj zdefiniowanego tagu lub definiowania układu. Musisz dodać sekundę dla <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  W poniższym przykładzie pokazano atrybuty eksportu dostawcy tagów dla tagu układu negocjowania przestrzeni.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Rozszerzanie procesorów myszy
 Możesz dodać specjalną obsługę danych wejściowych myszy. Utwórz klasę dziedziczącą z <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> klasy i zastępującą zdarzenia myszy dla danych wejściowych, które mają być obsługiwane. Należy również zaimplementować klasę w drugiej klasie i wyeksportować ją wraz z wartością określającą rodzaj zawartości (na przykład <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> "tekst" lub "kod"), dla której program obsługi myszy <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> jest prawidłowy.

 W poniższym przykładzie pokazano atrybuty eksportu dostawcy procesora myszy.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Rozszerzanie obsługi upuszczania
 Możesz dostosować zachowanie programów obsługi upuszczania dla określonych rodzajów tekstu, tworząc klasę implementacyjną i drugą klasę, która implementuje w celu utworzenia procedury obsługi <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> upuszczania. Należy wyeksportować program obsługi drop wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: format tekstu, dla którego ta procedura obsługi drop jest prawidłowa. Następujące formaty są obsługiwane w kolejności priorytetów od najwyższego do najniższego:

  1. Dowolny format niestandardowy

  2. FileDrop

  3. EnhancedMetafile

  4. Waveaudio

  5. Riff

  6. Dif

  7. Regionalne

  8. Palety

  9. PenData

  10. Serializacji

  11. Link symboliczny

  12. Xaml

  13. Pakiet XamlPackage

  14. Tiff

  15. Bitmapy

  16. Dib

  17. MetafilePicture

  18. CSV

  19. System.string

  20. HTML Format

  21. Unicodetext

  22. OEMText

  23. Tekst

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa procedury obsługi drop.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność procedury obsługi upuszczania przed lub po domyślnej obsłudze upuszczania. Domyślna procedura obsługi drop dla Visual Studio nosi nazwę "DefaultFileDropHandler".

  W poniższym przykładzie pokazano atrybuty eksportu u dostawcy obsługi upuszczania.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Rozszerzanie opcji edytora
 Można zdefiniować opcje, które mają być prawidłowe tylko w określonym zakresie, na przykład w widoku tekstowym. Edytor udostępnia ten zestaw wstępnie zdefiniowanych opcji: opcje edytora, opcje wyświetlania i opcje Windows Presentation Foundation (WPF). Te opcje można znaleźć w <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> , <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> i <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 Aby dodać nową opcję, należy wyprowadzić klasę z jednej z tych klas definicji opcji:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  W poniższym przykładzie pokazano, jak wyeksportować definicję opcji, która ma wartość logiczną.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Rozszerzanie funkcji IntelliSense
 IntelliSense to ogólny termin dla grupy funkcji, które dostarczają informacji o tekście ustrukturyzowanym i uzupełnianiu instrukcji. Te funkcje obejmują uzupełnianie instrukcji, pomoc w podpisie, szybkie informacje i żarówki. Uzupełnianie instrukcji ułatwia użytkownikom poprawne wpisywanie słowa kluczowego języka lub nazwy członka. Pomoc w podpisie wyświetla podpis lub podpisy dla metody, która została właśnie wpisana przez użytkownika. Szybkie informacje — wyświetla pełny podpis dla typu lub nazwy członka, gdy myszy się na nim zajmą. Żarówka zapewnia dodatkowe akcje dla niektórych identyfikatorów w niektórych kontekstach, na przykład zmianę nazwy wszystkich wystąpień zmiennej po zmianie nazwy jednego wystąpienia.

 Projekt funkcji IntelliSense jest bardzo taki sam we wszystkich przypadkach:

- Za cały *proces odpowiada broker* funkcji IntelliSense.

- Sesja IntelliSense *reprezentuje* sekwencję zdarzeń między wyzwoleniem prezentera a zatwierdzeniem lub anulowaniem zaznaczenia. Sesja jest zwykle wyzwalana przez pewien gest użytkownika.

- Kontroler funkcji *IntelliSense* jest odpowiedzialny za podjęcie decyzji o tym, kiedy sesja powinna się rozpocząć i zakończyć. Decyduje również o tym, kiedy informacje powinny zostać zatwierdzone i kiedy należy anulować sesję.

- Źródło IntelliSense *dostarcza* zawartość i decyduje o najlepszym dopasowaniu.

- Prezenter *funkcji* IntelliSense jest odpowiedzialny za wyświetlanie zawartości.

  W większości przypadków zalecamy podanie co najmniej źródła i kontrolera. Jeśli chcesz dostosować ekran, możesz również podać prezentera.

### <a name="implement-an-intellisense-source"></a>Implementowanie źródła IntelliSense
 Aby dostosować źródło, należy zaimplementować co najmniej jeden z następujących interfejsów źródłowych:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> został przestarzały na rzecz <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 Ponadto należy zaimplementować dostawcę tego samego rodzaju:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> został przestarzały na rzecz <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 Należy wyeksportować dostawcę wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa źródła.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), której dotyczy źródło.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność, w jakiej powinno być wyświetlane źródło (w odniesieniu do innych źródeł).

- W poniższym przykładzie pokazano atrybuty eksportu dostawcy źródła uzupełniania.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Aby uzyskać więcej informacji na temat implementowania źródeł IntelliSense, zobacz następujące wskazówki:

- [Przewodnik: wyświetlanie etykietek narzędzi QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Przewodnik: wyświetlanie pomocy dotyczącej sygnatur](../extensibility/walkthrough-displaying-signature-help.md)

- [Przewodnik: uzupełnianie instrukcji wyświetlania](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementowanie kontrolera IntelliSense
 Aby dostosować kontroler, należy zaimplementować <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interfejs. Ponadto należy zaimplementować dostawcę kontrolera wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa kontrolera.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "tekst" lub "kod"), do której ma zastosowanie kontroler.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność, w jakiej powinien się pojawić kontroler (w odniesieniu do innych kontrolerów).

  W poniższym przykładzie pokazano atrybuty eksportu dostawcy kontrolera uzupełniania.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Aby uzyskać więcej informacji na temat korzystania z kontrolerów IntelliSense, zobacz następujące wskazówki:

- [Przewodnik: wyświetlanie etykietek narzędzi QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
