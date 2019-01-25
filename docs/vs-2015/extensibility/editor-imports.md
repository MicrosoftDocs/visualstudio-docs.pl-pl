---
title: Importy edytora | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 461687e5d1e9570ea2e03610f838f6114fbc7643
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779875"
---
# <a name="editor-imports"></a>Importy edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zaimportować szereg usług edytora, fabryk i brokerzy, umożliwiające rozszerzenie z różnymi rodzajami dostępu do podstawowy edytor. Na przykład można importować <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> zapewnienie użytkownikowi <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> dla danego typu zawartości. (To navigator pozwala wykonywać różne rodzaje wyszukiwania dla bufora tekstowego.)  
  
 Aby użyć importu edytora, zaimportować jako pole lub właściwość klasy, które eksportuje część Managed Extensibility Framework.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat Managed Extensibility Framework, zobacz [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
## <a name="import-syntax"></a>Składnia importu  
 Poniższy przykład pokazuje, jak zaimportować edytora opcje fabryki usługi.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Jeśli chcesz zaimportować usługi jako pola i właściwości nie powinien być skonfigurowany `null` w deklaracji w celu uniknięcia ostrzeżeń kompilatora o nie przypisanie do zmiennej:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Aby uzyskać więcej przykładów użycia importów zobacz następujące instruktaże:  
  
 [Przewodnik: Tworzenie marginesie](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Przewodnik: Dostosowywanie widoku tekstu](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Przewodnik: Wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md)  
  
 [Przewodnik: Wyświetlanie etykietek narzędzi Szybkieinfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Przewodnik: Wyświetlanie pomocy dotyczącej sygnatur](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Przewodnik: Wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Przewodnik: Wyświetlanie tagi inteligentne](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>Importowanie dostawcy usług  
 Możesz również zaimportować <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (które można znaleźć w zestawie Microsoft.VisualStudio.Shell.Immutable.10.0) w taki sam sposób, aby uzyskać dostęp do usług Visual Studio:  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Zobacz [instruktażu: Uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) Aby uzyskać więcej informacji.  
  
## <a name="services"></a>Usługi  
 Edytor usługi są ogólnie pojedynczych jednostek, świadczenia usług, które są współużytkowane przez wiele składników.  
  
|Import|Zawiera|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Relacja między rozszerzeniami plików i <xref:Microsoft.VisualStudio.Utilities.IContentType> obiektów.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Kolekcja <xref:Microsoft.VisualStudio.Utilities.IContentType> obiektów.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> Obiekty|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Wiele obiektów karta edytora:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> Obiektu w celu wyświetlenia danego tekstu.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> Różnic.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> Różnic.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> Lub <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Zbiór <xref:Microsoft.VisualStudio.Text.ITextBuffer> obiektów.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Dla <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Przechowuje kolekcję <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> obiektów.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> Dla bufora tekstowego.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> Widoku tekstu.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> Dla określonego zakresu.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> Widoku tekstu.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Pobiera Automatyczne wcięcie <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> obiektów.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Zarządza <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> dla <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generuje tekstu w formacie RTF z zestawu migawki zakresów.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> formatowania wierszy tekstu w widoku.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|A <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> dla obiektu <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Wyszukuje tekst migawki.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> Dla <xref:Microsoft.VisualStudio.Text.ITextBuffer> przez <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> Widoku tekstu.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standardowy zestaw symbole.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> Dla <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Śledzi klawiatury obsługi.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standardowa <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> obiektów.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Obsługuje relację między buforów tekstu i <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> obiektów.|  
  
## <a name="other-imports"></a>Pozostałe Importy  
 Fabryki dostawców i brokerów są zwykle jednostek, które mogą mieć wiele wystąpień w wielu składników.  
  
|Import|Zawiera|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> Typu <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) dla podanego buforu.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Moduł tagujący znacznika tekstu ( <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> Dla danego <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
