---
title: 'Przewodnik: Tworzenie marginesie | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa18b900ca44fbb52c646bfdf021beed6e77f504
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112471"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Przewodnik: Tworzenie symbolu na marginesie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą rozszerzenia niestandardowego edytora, można dostosować wygląd marginesu edytora. W tym przewodniku umieszcza glifów margines wskaźnika zawsze wtedy, gdy wyraz "todo" pojawia się w komentarzu do kodu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
1. Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `TodoGlyphTest`.  
  
2. Dodaj element projektu klasyfikatora edytora. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Usuń istniejące pliki klasy.  
  
## <a name="defining-the-glyph"></a>Definiowanie glifów  
 Zdefiniuj symbol poprzez implementację <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfejsu.  
  
#### <a name="to-define-the-glyph"></a>Aby zdefiniować symbol  
  
1. Dodaj plik klasy i nadaj mu nazwę `TodoGlyphFactory`.  
  
2. Dodaj następujące deklaracje.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3. Dodaj klasę o nazwie `TodoGlyphFactory` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4. Dodaj pola prywatnego, który definiuje wymiary glif.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5. Implementowanie `GenerateGlyph` , definiując elementu interfejsu użytkownika symbol. `TodoTag` jest zdefiniowany w dalszej części tego przewodnika.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6. Dodaj klasę o nazwie `TodoGlyphFactoryProvider` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Eksportowanie tej klasy przy użyciu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> z "TodoGlyph" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z VsTextMarker po <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "code" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7. Implementowanie <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metoda przez utworzenie wystąpienia `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definiowanie tagów zadań do wykonania i moduł Tagujący  
 Definiowanie relacji między elementem interfejsu użytkownika, który został zdefiniowany w poprzednich krokach i margines wskaźnika, tworząc typ tagu i moduł tagujący i wyeksportować go przy użyciu dostawcy moduł tagujący.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Aby zdefiniować tagu zadań do wykonania i moduł tagujący  
  
1. Dodaj nowy plik klasy do projektu i nadaj mu nazwę `TodoTagger`.  
  
2. Dodaj następujące instrukcje importu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3. Dodaj klasę o nazwie `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4. Zmodyfikuj klasę o nazwie `TodoTagger` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5. Aby `TodoTagger` klasy, Dodaj pola prywatne dla <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> i tekst do wyszukania w klasyfikacji można obejmuje.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6. Dodaj Konstruktor, który ustawia klasyfikatora.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7. Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> obejmuje metody, wyszukując wszystkich klasyfikacji, których nazwy zawierają wyraz "comment" i którego tekstu zawiera tekst wyszukiwania. Zawsze, gdy zostanie znaleziony tekst wyszukiwania, ponownie uzyskanie nową <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> typu `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8. Zadeklaruj `TagsChanged` zdarzeń.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Dodaj klasę o nazwie `TodoTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "code" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Importuj <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metoda przez utworzenie wystąpienia `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Aby przetestować ten kod, Kompiluj rozwiązanie TodoGlyphTest, a następnie uruchomić go w doświadczalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Aby skompilować i przetestować rozwiązanie TodoGlyphTest  
  
1. Skompiluj rozwiązanie.  
  
2. Uruchom projekt, naciskając klawisz F5. Drugie wystąpienie programu Visual Studio jest uruchomiony.  
  
3. Upewnij się, że margines wskaźnika jest wyświetlane. (Na **narzędzia** menu, kliknij przycisk **opcje**. Na **edytora tekstów** strony, upewnij się, że **margines wskaźnika** jest zaznaczona.)  
  
4. Otwórz plik kodu, który ma komentarzy. Dodaj ten wyraz "todo" do sekcji komentarzy.  
  
5. Jasny jasnoniebieski okrąg, zawierającej niebieski kontur ciemny powinna pojawić się na marginesie wskaźnik po lewej stronie okna kodu.
