---
title: Punkty rozszerzeń usługi językowej i edytora | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703057"
---
# <a name="language-service-and-editor-extension-points"></a>Punkty rozszerzeń usługi językowej i edytora
Edytor udostępnia punkty rozszerzenia, które można rozszerzyć jako zarządzane struktury rozszerzalności (MEF) części składowych, w tym większość funkcji usługi języka. Są to główne kategorie punktów rozszerzenia:

- Typy zawartości

- Typy klasyfikacji i formaty klasyfikacji

- Marginesy i paski przewijania

- Tagi

- Ozdoby

- Procesory myszy

- Programy obsługi upuszczania

- Opcje

- IntelliSense

## <a name="extend-content-types"></a>Rozszerzanie typów zawartości
 Typy zawartości są definicje rodzajów tekstu obsługiwane przez edytora, na przykład "text", "code" lub "CSharp". Definiujesz nowy typ zawartości, deklarując zmienną typu <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> i nadając nowemu typowi zawartości unikatową nazwę. Aby zarejestrować typ zawartości w edytorze, wyeksportuj go wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>jest nazwą typu zawartości.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>jest nazwą typu zawartości, z której pochodzi ten typ zawartości. Typ zawartości może dziedziczyć z wielu innych typów zawartości.

  Ponieważ <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> klasa jest zapieczętowana, można ją wyeksportować bez parametru typu.

  W poniższym przykładzie przedstawiono atrybuty eksportu w definicji typu zawartości.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Typy zawartości mogą być oparte na zero lub więcej wcześniej istniejących typów zawartości. Są to wbudowane typy:

- Dowolny: podstawowy typ zawartości. Nadrzędny wszystkich innych typów zawartości.

- Tekst: podstawowy typ zawartości nieprosycyjnej. Dziedziczy po "any".

- Tekst zwykły: dla tekstu bez kodu. Dziedziczy po "tekście".

- Kod: dla kodu wszelkiego rodzaju. Dziedziczy po "tekście".

- Obojętny: wyklucza tekst z dowolnego rodzaju obsługi. Tekst tego typu zawartości nigdy nie będzie miał żadnych rozszerzeń.

- Projekcja: dla zawartości buforów projekcji. Dziedziczy po "any".

- Intellisense: dla zawartości IntelliSense. Dziedziczy po "tekście".

- Sighelp: pomoc podpisu. Dziedziczy po "intellisense".

- Sighelp-doc: dokumentacja pomocy podpisu. Dziedziczy po "intellisense".

  Są to niektóre typy zawartości, które są zdefiniowane przez program Visual Studio i niektóre języki, które są hostowane w programie Visual Studio:

- Podstawowy

- C/C++

- KonsolaOutput

- Csharp

- CSS

- Enc

- Znajdź Wyniki

- F#

- HTML

- JScript

- XAML

- XML

  Aby odkryć listę dostępnych typów zawartości, zaimportuj <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>program , który przechowuje kolekcję typów zawartości dla edytora. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Aby skojarzyć typ zawartości z <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>rozszerzeniem nazwy pliku, użyj programu .

> [!NOTE]
> W programie Visual Studio rozszerzenia nazw plików <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> są rejestrowane przy użyciu pakietu usługi języka. Kojarzy <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> typ zawartości MEF z rozszerzeniem nazwy pliku, który został zarejestrowany w ten sposób.

 Aby wyeksportować rozszerzenie nazwy pliku do definicji typu zawartości, należy dołączyć następujące atrybuty:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: określa rozszerzenie nazwy pliku.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: określa typ zawartości.

  Ponieważ <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> klasa jest zapieczętowana, można ją wyeksportować bez parametru typu.

  W poniższym przykładzie przedstawiono atrybuty eksportu w rozszerzeniu nazwy pliku do definicji typu zawartości.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 Zarządza <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> skojarzeniami między rozszerzeniami nazw plików a typami zawartości.

## <a name="extend-classification-types-and-classification-formats"></a>Rozszerzanie typów klasyfikacji i formatów klasyfikacji
 Typy klasyfikacji służy do definiowania rodzajów tekstu, dla których chcesz zapewnić inną obsługę (na przykład kolorowanie "słowa kluczowego" tekst niebieski i "komentarz" tekst zielony). Zdefiniuj nowy typ klasyfikacji, <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> deklarując zmienną typu i nadając jej unikatową nazwę.

 Aby zarejestrować typ klasyfikacji w edytorze, wyeksportuj go wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa typu klasyfikacji.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: nazwa typu klasyfikacji, z którego dziedziczy ten typ klasyfikacji. Wszystkie typy klasyfikacji dziedziczą po "tekście", a typ klasyfikacji może dziedziczyć z wielu innych typów klasyfikacji.

  Ponieważ <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> klasa jest zapieczętowana, można ją wyeksportować bez parametru typu.

  W poniższym przykładzie przedstawiono atrybuty eksportu w definicji typu klasyfikacji.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 Zapewnia <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> dostęp do standardowych klasyfikacji. Wbudowane typy klasyfikacji obejmują następujące typy:

- "tekst"

- "język naturalny" (pochodzi od "tekstu")

- "język formalny" (pochodzi od "tekstu")

- "string" (pochodzi od "literal")

- "character" (pochodzi od "literał")

- "numeryczny" (pochodzi od "literał")

  Zestaw różnych typów błędów <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>dziedziczyć z . Obejmują one następujące typy błędów:

- "błąd składniowy"

- "błąd kompilatora"

- "inny błąd"

- "ostrzeżenie"

  Aby odkryć listę dostępnych typów klasyfikacji, zaimportuj <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>program , który przechowuje kolekcję typów klasyfikacji dla edytora. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Można zdefiniować definicję formatu klasyfikacji dla nowego typu klasyfikacji. Wyprowadz klasę <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> i wyeksportuj ją z typem, <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa formatu.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: wyświetlana nazwa formatu.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: określa, czy format jest wyświetlany na stronie **Czcionki i kolory** w oknie dialogowym **Opcje.**

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: priorytet formatu. Prawidłowe wartości <xref:Microsoft.VisualStudio.Text.Classification.Priority>pochodzą od pliku .

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

 Aby odkryć listę dostępnych formatów, <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>zaimportuj program , który przechowuje kolekcję formatów dla edytora. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Rozszerzanie marginesów i pasków przewijania
 Marginesy i paski przewijania są głównymi elementami widoku edytora oprócz samego widoku tekstu. Oprócz standardowych marginesów wyświetlanych wokół widoku tekstu można podać dowolną liczbę marginesów.

 Zaimplementuj <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interfejs do definiowania marginesu. Należy również zaimplementować interfejs, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> aby utworzyć margines.

 Aby zarejestrować dostawcę marginesu w edytorze, należy wyeksportować dostawcę wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa marginesu.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność pojawiania się marginesu względem pozostałych marginesów.

   Są to wbudowane marginesy:

  - "Wpf Poziomy pasek przewijania"

  - "Pionowy pasek przewijania Wpf"

  - "Margines numeru wiersza WPF"

    Marginesy poziome, których `After="Wpf Horizontal Scrollbar"` atrybut zamówienia mają atrybut zamówienia, są wyświetlane poniżej wbudowanego `Before ="Wpf Horizontal Scrollbar"` marginesu, a marginesy poziome, których atrybut zamówienia mają atrybut zamówienia, są wyświetlane powyżej wbudowanego marginesu. Prawe pionowe marginesy, `After="Wpf Vertical Scrollbar"` których atrybut zamówienia ma atrybut zamówienia, są wyświetlane po prawej stronie paska przewijania. Lewe pionowe marginesy, `After="Wpf Line Number Margin"` których atrybut zamówienia ma, są wyświetlane po lewej stronie marginesu numeru wiersza (jeśli jest widoczny).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: rodzaj marginesu (lewy, prawy, górny lub dolny).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj treści (na przykład "tekst" lub "kod"), dla których margines jest ważny.

  W poniższym przykładzie przedstawiono atrybuty eksportu w dostawcy marginesu dla marginesu, który pojawia się po prawej stronie marginesu numeru wiersza.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Rozszerzanie znaczników
 Tagi są sposobem kojarzenia danych z różnymi rodzajami tekstu. W wielu przypadkach skojarzone dane są wyświetlane jako efekt wizualny, ale nie wszystkie tagi mają prezentację wizualną. Można zdefiniować własny rodzaj tagu, implementując <xref:Microsoft.VisualStudio.Text.Tagging.ITag>plik . Należy również <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> zaimplementować, aby zapewnić tagi dla <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> danego zestawu zakresów tekstu i, aby zapewnić tager. Musisz wyeksportować dostawcę znaczników wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj treści (na przykład "tekst" lub "kod"), dla których tag jest prawidłowy.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: rodzaj znacznika.

  W poniższym przykładzie przedstawiono atrybuty eksportu u dostawcy znaczników.

\<CodeContentPlaceHolder>8</CodeContentPlaceHolder> Następujące rodzaje tagów są wbudowane:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: związane z <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: skojarzone z typami błędów.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: związane z ozdobą.

  > [!NOTE]
  > Na przykład <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, zobacz HighlightWordTag definicji w [przewodniku: Wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: skojarzone z regionami, które można rozwinąć lub zwinąć w nakreśleniu.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definiuje przestrzeń zajmowaną przez ozdobę w widoku tekstowym. Aby uzyskać więcej informacji na temat ozdoby negocjacji przestrzeni, zobacz następującą sekcję.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: zapewnia automatyczne odstępy i rozmiary ozdabiania.

  Aby znaleźć i używać znaczników dla buforów <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>i widoków, <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> zaimportuj <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> lub , które dają żądany typ. Poniższy kod importuje tę usługę jako właściwość.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Znaczniki i znacznikformatDefinitions
 Można rozszerzyć <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> klasę, aby zdefiniować wygląd znacznika. Należy wyeksportować <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>klasę (jako)z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa użyta do odwołania się do tego formatu

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: powoduje to, że format pojawia się w interfejsie użytkownika

  W konstruktorze można zdefiniować nazwę wyświetlaną i wygląd znacznika. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>definiuje kolor wypełnienia i <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> definiuje kolor obramowania. Jest <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> zlokalizowana nazwa definicji formatu.

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

 Aby zastosować tę definicję formatu do znacznika, odwołaj się do nazwy ustawionej w atrybucie nazwa klasy (a nie w nazwie wyświetlanej).

> [!NOTE]
> Na przykład <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, zobacz HighlightWordFormatDefinition klasy w [przewodniku: Wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Rozszerzanie ozdób
 Ozdoby definiują efekty wizualne, które można dodać do tekstu wyświetlanego w widoku tekstowym lub do samego widoku tekstu. Można zdefiniować własne ozdoby jako dowolny <xref:System.Windows.UIElement>typ .

 W klasie ozdabiania należy <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>zadeklarować . Aby zarejestrować warstwę ozdabianie, wyeksportuj ją razem z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa ozdoby.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność ozdabiania w odniesieniu do innych warstw ozdabiania. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definiuje cztery domyślne warstwy: Zaznaczenie,Kreślenie, Cyt i Tekst.

  W poniższym przykładzie przedstawiono atrybuty eksportu w definicji warstwy ozdabiania.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Należy utworzyć drugą klasę, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> która implementuje i obsługuje jego <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> zdarzenie przez utworzenie wystąpienia ozdabiania. Tę klasę należy wyeksportować wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "tekst" lub "kod"), dla którego ozdoba jest prawidłowa.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: rodzaj widoku tekstu, dla którego ta ozdoba jest prawidłowa. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> ma zestaw wstępnie zdefiniowanych ról widoku tekstu. Na przykład <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> jest używany głównie do widoków tekstowych plików. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>służy do widoków tekstu, które użytkownik może edytować lub nawigować za pomocą myszy i klawiatury. Przykładami <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> widoków są widok tekstu edytora i okno **Dane wyjściowe.**

  W poniższym przykładzie przedstawiono atrybuty eksportu w dostawcy ozdabiania.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Ozdoba do negocjacji przestrzeni to taka, która zajmuje miejsce na tym samym poziomie co tekst. Aby utworzyć ten rodzaj ozdabiania, należy zdefiniować <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>klasę znacznika, która dziedziczy z , który definiuje ilość miejsca zajmowanego przez ozdobę.

 Podobnie jak w przypadku wszystkich ozdób, należy wyeksportować definicję warstwy ozdób.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Aby utworzyć wystąpienie ozdoby negocjacji przestrzeni, należy utworzyć klasę, <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>która implementuje , oprócz <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> klasy, która implementuje (podobnie jak w przypadku innych rodzajów ozdób).

 Aby zarejestrować dostawcę znaczników, należy wyeksportować go wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj treści (na przykład "tekst" lub "kod"), dla których twoje ozdoby są ważne.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: rodzaj widoku tekstu, dla którego ten znacznik lub ozdoba jest prawidłowy. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> ma zestaw wstępnie zdefiniowanych ról widoku tekstu. Na przykład <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> jest używany głównie do widoków tekstowych plików. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>służy do widoków tekstu, które użytkownik może edytować lub nawigować za pomocą myszy i klawiatury. Przykładami <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> widoków są widok tekstu edytora i okno **Dane wyjściowe.**

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: rodzaj zdefiniowanego znacznika lub ozdabiania. Należy dodać sekundę <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>dla .

  W poniższym przykładzie przedstawiono atrybuty eksportu w dostawcy tageru dla tagu ozdabiania negocjacji przestrzeni.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Rozszerzanie procesorów myszy
 Można dodać specjalną obsługę dla wprowadzania myszy. Utwórz klasę, która <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> dziedziczy i zastąpić zdarzenia myszy dla danych wejściowych, które chcesz obsłużyć. Należy również <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> zaimplementować w drugiej <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> klasie i wyeksportować go wraz z tym określa rodzaj zawartości (na przykład "tekst" lub "kod"), dla którego program obsługi myszy jest prawidłowy.

 W poniższym przykładzie przedstawiono atrybuty eksportu u dostawcy procesora myszy.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Rozszerzanie obsługi upuszczania
 Można dostosować zachowanie programów obsługi upuszczania dla określonych rodzajów tekstu, <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> tworząc klasę, która <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> implementuje i drugą klasę, która implementuje do tworzenia programu obsługi upuszczania. Program obsługi upuszczania należy wyeksportować wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: format tekstu, dla którego ten program obsługi upuszczania jest prawidłowy. Następujące formaty są obsługiwane w kolejności priorytetu od najwyższego do najniższego:

  1. Dowolny format niestandardowy

  2. Kropla pliku

  3. UlepszonaMetafile

  4. Waveaudio

  5. Riff

  6. Dif

  7. Ustawienia regionalne

  8. Palety

  9. PenData (dane pióro)

  10. Serializacji

  11. Link symboliczny

  12. Xaml

  13. Pakiet Xaml

  14. Tiff

  15. Bitmapy

  16. Dib

  17. MetafileZdjęcie

  18. CSV

  19. System.string

  20. HTML Format

  21. Unicodetext

  22. Tekst OEM

  23. Tekst

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa programu obsługi upuszczania.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność obsługi upuszczania przed lub po domyślnym programie obsługi upuszczania. Domyślny program obsługi upuszczania dla programu Visual Studio nosi nazwę "DefaultFileDropHandler".

  W poniższym przykładzie przedstawiono atrybuty eksportu u dostawcy obsługi upuszczania.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Rozszerzanie opcji edytora
 Można zdefiniować opcje, które mają być prawidłowe tylko w określonym zakresie, na przykład w widoku tekstowym. Edytor udostępnia ten zestaw wstępnie zdefiniowanych opcji: opcje edytora, opcje wyświetlania i opcje widoku Windows Presentation Foundation (WPF). Te opcje można <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>znaleźć <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>w <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>, i .

 Aby dodać nową opcję, należy wyprowadzić klasę z jednej z tych klas definicji opcji:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  W poniższym przykładzie pokazano, jak wyeksportować definicję opcji o wartości logicznej.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Rozszerzanie funkcji IntelliSense
 IntelliSense jest ogólnym terminem dla grupy funkcji, które zawierają informacje o tekście strukturalnym i uzupełnieniu instrukcji dla niego. Funkcje te obejmują uzupełnianie instrukcji, pomoc dotyczącą podpisu, szybkie informacje i żarówki. Ukończenie instrukcji pomaga użytkownikom poprawnie wpisać słowo kluczowe lub nazwę członka języka. Pomoc dotycząca podpisu wyświetla podpis lub podpisy dla metody, którą użytkownik właśnie wpisał. Szybkie informacje wyświetla pełny podpis dla typu lub nazwy elementu członkowskiego, gdy mysz spoczywa na nim. Żarówka zapewniają dodatkowe akcje dla niektórych identyfikatorów w niektórych kontekstach, na przykład zmiana nazwy wszystkich wystąpień zmiennej po zmianie nazwy jednego wystąpienia.

 Konstrukcja funkcji IntelliSense jest taka sama we wszystkich przypadkach:

- *Broker* IntelliSense jest odpowiedzialny za cały proces.

- *Sesja* IntelliSense reprezentuje sekwencję zdarzeń między wyzwoleniem prezentera a zatwierdzeniem lub anulowaniem zaznaczenia. Sesja jest zazwyczaj wyzwalane przez gest użytkownika.

- *Kontroler* IntelliSense jest odpowiedzialny za podjęcie decyzji, kiedy sesja powinna się rozpocząć i zakończyć. Decyduje również, kiedy informacje powinny zostać zatwierdzone i kiedy sesja powinna zostać anulowana.

- *Źródło* IntelliSense udostępnia zawartość i decyduje o najlepszym dopasować.

- *Prezenter* IntelliSense jest odpowiedzialny za wyświetlanie zawartości.

  W większości przypadków zaleca się podanie co najmniej źródła i kontrolera. Można również podać prezentera, jeśli chcesz dostosować wyświetlacz.

### <a name="implement-an-intellisense-source"></a>Implementowanie źródła IntelliSense
 Aby dostosować źródło, należy zaimplementować jeden (lub więcej) następujących interfejsów źródłowych:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>został przestarzały na <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>rzecz .

 Ponadto należy zaimplementować dostawcę tego samego rodzaju:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>został przestarzały na <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>rzecz .

 Dostawca należy wyeksportować wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa źródła.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj treści (na przykład "tekst" lub "kod"), do którego ma zastosowanie źródło.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność, w jakiej powinno się pojawić źródło (w odniesieniu do innych źródeł).

- W poniższym przykładzie przedstawiono atrybuty eksportu u dostawcy źródła ukończenia.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Aby uzyskać więcej informacji na temat implementowania źródeł intellisense, zobacz następujące wskazówki:

- [Instruktaż: Wyświetlanie etykietek narzędzi QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Instruktaż: Wyświetlanie pomocy podpisu](../extensibility/walkthrough-displaying-signature-help.md)

- [Instruktaż: Zakończenie instrukcji wyświetlania](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementowanie kontrolera IntelliSense
 Aby dostosować kontroler, należy zaimplementować <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interfejs. Ponadto należy zaimplementować dostawcę kontrolera wraz z następującymi atrybutami:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa sterownika.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj treści (na przykład "tekst" lub "kod"), do którego stosuje się kontroler.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność, w jakiej powinien pojawić się kontroler (w odniesieniu do innych kontrolerów).

  W poniższym przykładzie przedstawiono atrybuty eksportu u dostawcy kontrolera ukończenia.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Aby uzyskać więcej informacji na temat korzystania z kontrolerów IntelliSense, zobacz następujące wskazówki:

- [Instruktaż: Wyświetlanie etykietek narzędzi QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
