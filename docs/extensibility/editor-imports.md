---
title: Importy edytora | Microsoft Docs
description: Dowiedz się, jak importować usługi edytora, fabryki i brokerów, które udostępniają swoje rozszerzenia różnym rodzajom dostępu do podstawowego edytora.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0587ed6487ec3a1bb833a804bb5ffa76cbc101f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070157"
---
# <a name="editor-imports"></a>Importy edytora
Istnieje możliwość zaimportowania wielu usług edytora, fabryk i brokerów, które zapewniają rozszerzenie z różnymi rodzajami dostępu do podstawowego edytora. Na przykład można zaimportować program w <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> celu zapewnienia <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> dla danego typu zawartości. (Ten Nawigator umożliwia wykonywanie różnych rodzajów wyszukiwania w buforze tekstu).

 Aby użyć importu edytora, należy zaimportować go jako pole lub właściwość klasy, która eksportuje część składnika Managed Extensibility Framework.

> [!NOTE]
> Aby uzyskać więcej informacji na temat Managed Extensibility Framework, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Składnia importu
 Poniższy przykład przedstawia sposób importowania usługi Fabryka opcji edytora.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Jeśli chcesz zaimportować usługę jako pole, a nie właściwość, należy ustawić ją na wartość `null` w deklaracji, aby uniknąć ostrzeżeń kompilatora o przypisaniu do zmiennej:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Aby uzyskać więcej przykładów dotyczących używania importów, zobacz następujące przewodniki:

- [Przewodnik: Tworzenie symbolu marginesu](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Przewodnik: Dostosowywanie widoku tekstu](../extensibility/walkthrough-customizing-the-text-view.md)

- [Wskazówki: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md)

- [Przewodnik: wyświetlanie etykietek narzędzi sekcji szybkich informacji](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Przewodnik: Wyświetlanie pomocy dotyczącej podpisu](../extensibility/walkthrough-displaying-signature-help.md)

- [Przewodnik: Wyświetlanie instrukcji wyświetlania](../extensibility/walkthrough-displaying-statement-completion.md)

- [Przewodnik: wyświetlanie sugestii żarówki](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importowanie dostawcy usług
 Możesz również zaimportować <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (znaleziono w zestawie Microsoft. VisualStudio. Shell.. 10.0) w taki sam sposób, aby uzyskać dostęp do usług Visual Studio:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Aby uzyskać więcej informacji [, zobacz Przewodnik: dostęp do obiektu DTE z rozszerzenia edytora](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) .

## <a name="services"></a>Usługi
 Usługi edytora są ogólnie pojedynczymi jednostkami, które udostępniają usługę i są współużytkowane przez wiele składników.

|Importuj|Umożliwiające|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Relacja między rozszerzeniami plików a <xref:Microsoft.VisualStudio.Utilities.IContentType> obiektami.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Kolekcja obiektów <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> elementy.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Wiele obiektów kart edytora:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>Obiekt dla danego widoku tekstu.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|A <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|A <xref:Microsoft.VisualStudio.Text.ITextDocument> .|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>Różnice.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>Różnice.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>Lub <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>Dla zestawu <xref:Microsoft.VisualStudio.Text.ITextBuffer> obiektów.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>A <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>A <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>A <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>A <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Zachowuje kolekcję <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> obiektów.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>Dla buforu tekstu.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>Dla widoku tekstu.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>Dla określonego zakresu.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>Dla widoku tekstu.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>A <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Pobiera Automatyczne wcięcie za pomocą <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> obiektów.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Zarządza przez <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|A <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generuje tekst sformatowany w formacie RTF z zestawu zakresów migawek.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|A <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> dla elementu <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Element <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> do formatowania wierszy tekstu w widoku.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>Obiekt dla elementu <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Przeszukuje migawkę tekstu.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|A <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> <xref:Microsoft.VisualStudio.Text.ITextBuffer> przez <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>Dla widoku tekstu.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standardowy zestaw symboli.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>A <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Śledzi obsługę klawiatury.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>Obiekty standardowe.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Utrzymuje relację między buforami i  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> obiektami tekstu.|

## <a name="other-imports"></a>Inne Importy
 Fabryki dostawcy i brokerzy są zazwyczaj jednostkami, które mogą mieć wiele wystąpień w wielu składnikach.

|Importuj|Umożliwiające|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|A <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> ) dla danego buforu.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Moduł tagujący znacznika tekstu (a <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>Dla danego elementu <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|A <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|A <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|A <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession> .|

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
