---
title: Importy edytora | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6af95b452166aa71950ac1e869d333d12d857b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712013"
---
# <a name="editor-imports"></a>Importowanie edytora
Można zaimportować wiele usług edytora, fabryk i brokerów, które zapewniają rozszerzenie z różnych rodzajów dostępu do edytora podstawowego. Na przykład można zaimportować, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> aby zapewnić państwu dla danego typu zawartości. (Ten nawigator umożliwia wykonywanie różnych rodzajów wyszukiwań w buforze tekstowym).

 Aby użyć importu edytora, należy zaimportować go jako pole lub właściwość klasy, która eksportuje część składnika Managed Extensibility Framework.

> [!NOTE]
> Aby uzyskać więcej informacji na temat struktury zarządzanej rozszerzalności, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Składnia importu
 W poniższym przykładzie pokazano, jak zaimportować usługę fabryczną opcji edytora.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Jeśli chcesz zaimportować usługę jako pole, a nie `null` właściwość, należy ustawić ją w deklaracji, aby uniknąć ostrzeżeń kompilatora o nie przypisywaniu do zmiennej:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Aby uzyskać więcej przykładów używania importu, zobacz następujące wskazówki:

- [Instruktaż: tworzenie glifów marginesu](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Instruktaż: dostosowywanie widoku tekstu](../extensibility/walkthrough-customizing-the-text-view.md)

- [Instruktaż: Wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md)

- [Instruktaż: Wyświetlanie etykietek narzędzi QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Instruktaż: Wyświetlanie pomocy podpisu](../extensibility/walkthrough-displaying-signature-help.md)

- [Instruktaż: Zakończenie instrukcji wyświetlania](../extensibility/walkthrough-displaying-statement-completion.md)

- [Instruktaż: Wyświetlanie sugestii żarówki](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importowanie usługodawcy
 Można również zaimportować <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (znaleziono w zestawie Microsoft.VisualStudio.Shell.Immutable.10.0) w taki sam sposób, aby uzyskać dostęp do usług programu Visual Studio:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Zobacz [Instruktaż: Dostęp do obiektu DTE z rozszerzenia edytora,](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) aby uzyskać więcej informacji.

## <a name="services"></a>Usługi
 Usługi edytora są zazwyczaj pojedyncze jednostki, które zapewniają usługę i są współużytkowane przez wiele składników.

|Import|Zapewnia|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Relacja między rozszerzeniami <xref:Microsoft.VisualStudio.Utilities.IContentType> plików a obiektami.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Kolekcja obiektów <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>Obiektów.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Wiele obiektów karty edytora:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Obiekt <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> dla danego widoku tekstu.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Różnica. <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Różnica. <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|An <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> lub <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>an .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Dla <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> zestawu <xref:Microsoft.VisualStudio.Text.ITextBuffer> obiektów.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|For <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> a <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|For <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|For <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|For <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Zachowuje kolekcję <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> obiektów.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Dla <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> buforu tekstu.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Dla <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> widoku tekstu.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Dla <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> określonego zakresu.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Dla <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> widoku tekstu.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|For <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Pobiera automatyczne wcięcie <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> za pośrednictwem obiektów.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Zarządza <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> for . <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|An <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generuje tekst w formacie RTF z zestawu zakresów migawek.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Dla <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> . <xref:Microsoft.VisualStudio.Text.Editor.ITextView>|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> do formatowania wierszy tekstu w widoku.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Obiekt <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>pliku .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Przeszukuje migawkę tekstu.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Dla <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> przez <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Dla <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> widoku tekstu.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standardowy zestaw glifów.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|For <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Śledzi obsługę klawiatury.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Obiekty <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> standardowe.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Utrzymuje relację między buforami <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> tekstu i obiektami.|

## <a name="other-imports"></a>Inne przywóz
 Fabryki dostawców i brokerzy są zazwyczaj jednostkami, które mogą mieć wiele wystąpień w wielu składnikach.

|Import|Zapewnia|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|A <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) dla danego buforu.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Znacznik tekstowy (typu) <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Dla <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> danego <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
