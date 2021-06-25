---
title: Edytor importuje | Microsoft Docs
description: Dowiedz się, jak importować usługi edytora, fabryki i brokery, które zapewniają rozszerzeniu różne rodzaje dostępu do edytora podstawowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f2fa91b41017512b3f38ad61b800b293e0abaa1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898347"
---
# <a name="editor-imports"></a>Importy edytora
Możesz zaimportować wiele usług edytora, fabryk i brokerów, które zapewniają rozszerzeniu różne rodzaje dostępu do edytora podstawowego. Na przykład można zaimportować , aby zapewnić typ zawartości dla <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> danego typu zawartości. (To nawigator umożliwia wykonywanie różnych rodzajów wyszukiwań w buforze tekstowym).

 Aby użyć importu edytora, należy zaimportować go jako pole lub właściwość klasy, która eksportuje część Managed Extensibility Framework składnika.

> [!NOTE]
> Aby uzyskać więcej informacji na temat Managed Extensibility Framework, zobacz [Managed Extensibility Framework (MEF).](/dotnet/framework/mef/index)

## <a name="import-syntax"></a>Składnia importu
 W poniższym przykładzie pokazano, jak zaimportować usługę fabryki opcji edytora.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Jeśli chcesz zaimportować usługę jako pole, a nie właściwość, należy ustawić ją na wartość w deklaracji , aby uniknąć ostrzeżeń kompilatora dotyczących niew przypisywania `null` do zmiennej:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Aby uzyskać więcej przykładów użycia importów, zobacz następujące wskazówki:

- [Przewodnik: tworzenie glifu marginesu](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Przewodnik: dostosowywanie widoku tekstu](../extensibility/walkthrough-customizing-the-text-view.md)

- [Przewodnik: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md)

- [Przewodnik: wyświetlanie etykietek narzędzi QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Przewodnik: wyświetlanie pomocy dotyczącej sygnatur](../extensibility/walkthrough-displaying-signature-help.md)

- [Przewodnik: uzupełnianie instrukcji wyświetlania](../extensibility/walkthrough-displaying-statement-completion.md)

- [Przewodnik: wyświetlanie sugestii żarówki](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importowanie dostawcy usług
 Możesz również zaimportować pakiet (znaleziony w zestawie <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> Microsoft.VisualStudio.Shell.Immutable.10.0) w taki sam sposób, aby uzyskać dostęp do Visual Studio usług:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Aby [uzyskać więcej informacji,](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) zobacz Przewodnik: uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora.

## <a name="services"></a>Usługi
 Usługi edytora są zazwyczaj pojedynczymi jednostkami, które zapewniają usługę i są współużytkami wielu składników.

|Importuj|Zapewnia|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Relacja między rozszerzeniami plików i <xref:Microsoft.VisualStudio.Utilities.IContentType> obiektami.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Kolekcja obiektów <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> Obiektów.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Wiele obiektów adaptera edytora:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Obiekt <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> dla danego widoku tekstu.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Element <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Element <xref:Microsoft.VisualStudio.Text.ITextDocument> .|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>Różnice.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>Różnice.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Lub <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Element <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> dla zestawu <xref:Microsoft.VisualStudio.Text.ITextBuffer> obiektów.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Element <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> dla . <xref:Microsoft.VisualStudio.Text.ITextBuffer>|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Element <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> dla . <xref:Microsoft.VisualStudio.Text.Editor.ITextView>|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Element <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> dla . <xref:Microsoft.VisualStudio.Text.Editor.ITextView>|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Element <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> dla . <xref:Microsoft.VisualStudio.Text.Editor.ITextView>|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Utrzymuje kolekcję <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> obiektów .|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Element <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> dla buforu tekstowego.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Element <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> dla widoku tekstowego.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Dla <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> określonego zakresu.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Element <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> dla widoku tekstowego.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Element <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> dla . <xref:Microsoft.VisualStudio.Text.Editor.ITextView>|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Pobiera automatyczne wcięcie <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> obiektów.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Zarządza dla <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Element <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generuje tekst w formacie RTF na podstawie zestawu zakresów migawek.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Element <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> dla . <xref:Microsoft.VisualStudio.Text.Editor.ITextView>|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Do <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> formatowania wierszy tekstu w widoku.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Obiekt <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView> obiektu .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Wyszukuje migawkę tekstową.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Element <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> dla przez <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Element <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> dla widoku tekstowego.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standardowy zestaw glifów.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Element <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> dla . <xref:Microsoft.VisualStudio.Text.Editor.ITextView>|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Śledzi obsługę klawiatury.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Obiekty <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> standardowe.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Utrzymuje relację między buforami tekstowym i  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> obiektami.|

## <a name="other-imports"></a>Inne importy
 Fabryki dostawców i brokerzy to zazwyczaj jednostki, które mogą mieć wiele wystąpień w wielu składnikach.

|Importuj|Zapewnia|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Typ <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> ) dla danego <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> buforu.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Tag znacznika tekstu <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> (typ <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Dla <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> danego . <xref:Microsoft.VisualStudio.Text.Editor.ITextView>|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Element <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Element <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Element <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession> .|

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
