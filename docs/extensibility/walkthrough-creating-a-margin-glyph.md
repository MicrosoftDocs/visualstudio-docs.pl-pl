---
title: 'Przewodnik: Tworzenie marginesie | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51dea272a595f56abe254eda74dea67415f157a6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020246"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Przewodnik: Utwórz na marginesie
Za pomocą rozszerzenia niestandardowego edytora, można dostosować wygląd marginesu edytora. W tym przewodniku umieszcza glifów margines wskaźnika zawsze wtedy, gdy wyraz "todo" pojawia się w komentarzu do kodu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie instaluj programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Utwórz projekt MEF  
  
1.  Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `TodoGlyphTest`.  
  
2.  Dodaj element projektu klasyfikatora edytora. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń istniejące pliki klasy.  
  
## <a name="define-the-glyph"></a>Zdefiniuj glifów  
 Zdefiniować symbol, uruchamiając <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfejsu.  
  
### <a name="to-define-the-glyph"></a>Aby zdefiniować symbol  
  
1.  Dodaj plik klasy i nadaj mu nazwę `TodoGlyphFactory`.  
  
2.  Dodaj następujący kod, za pomocą deklaracji.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Dodaj klasę o nazwie `TodoGlyphFactory` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Dodaj pola prywatnego, który definiuje wymiary glif.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implementowanie `GenerateGlyph` , definiując elementu interfejsu użytkownika symbol. `TodoTag` jest zdefiniowany w dalszej części tego przewodnika.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Dodaj klasę o nazwie `TodoGlyphFactoryProvider` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Eksportowanie tej klasy przy użyciu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> z "TodoGlyph" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z VsTextMarker po <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "code" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implementowanie <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metoda przez utworzenie wystąpienia `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="define-a-todo-tag-and-tagger"></a>Zdefiniuj znacznik zadań do wykonania i moduł tagujący  
 Definiowanie relacji między elementem interfejsu użytkownika, który został zdefiniowany w poprzednich krokach i margines wskaźnika. Utwórz tag typu i moduł tagujący i wyeksportuj go przy użyciu dostawcy moduł tagujący.  
  
### <a name="to-define-a-todo-tag-and-tagger"></a>Aby zdefiniować tagu zadań do wykonania i moduł tagujący  
  
1.  Dodaj nowy plik klasy do projektu i nadaj mu nazwę `TodoTagger`.  
  
2.  Dodaj następujące instrukcje importu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Dodaj klasę o nazwie `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Zmodyfikuj klasę o nazwie `TodoTagger` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Aby `TodoTagger` klasy, Dodaj pola prywatne dla <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> i tekst do wyszukania w klasyfikacji można obejmuje.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Dodaj Konstruktor, który ustawia klasyfikatora.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> obejmuje metody, wyszukując wszystkich klasyfikacji, których nazwy zawierają wyraz "comment" i którego tekstu zawiera tekst wyszukiwania. Zawsze, gdy zostanie znaleziony tekst wyszukiwania, ponownie uzyskanie nową <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> typu `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Zadeklaruj `TagsChanged` zdarzeń.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Dodaj klasę o nazwie `TodoTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "code" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importuj <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metoda przez utworzenie wystąpienia `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu  
 Aby przetestować ten kod, Kompiluj rozwiązanie TodoGlyphTest, a następnie uruchomić go w doświadczalnym wystąpieniu.  
  
### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Aby skompilować i przetestować rozwiązanie TodoGlyphTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Uruchom projekt, naciskając klawisz **F5**. Drugie wystąpienie programu Visual Studio uruchamia.  
  
3.  Upewnij się, że margines wskaźnika jest wyświetlane. (Na **narzędzia** menu, kliknij przycisk **opcje**. Na **edytora tekstów** strony, upewnij się, że **margines wskaźnika** jest zaznaczona.)  
  
4.  Otwórz plik kodu, który ma komentarzy. Dodaj ten wyraz "todo" do sekcji komentarzy.  
  
5.  Jasny jasnoniebieski okrąg ciemny konspektu niebieski pojawia się w margines wskaźnika do lewej części okna kodu.