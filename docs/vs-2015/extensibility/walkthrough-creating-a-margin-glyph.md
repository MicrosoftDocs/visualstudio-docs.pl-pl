---
title: 'Przewodnik: Tworzenie symbolu marginesu | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148856"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Przewodnik: tworzenie symbolu na marginesie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz dostosować wygląd marginesów edytora przy użyciu rozszerzeń edytora niestandardowego. Ten Instruktaż umieszcza niestandardowy symbol na marginesie wskaźnika za każdym razem, gdy słowo "do zrobienia" pojawia się w komentarzu do kodu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `TodoGlyphTest` .  
  
2. Dodaj element projektu klasyfikatora edytora. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Usuń istniejące pliki klas.  
  
## <a name="defining-the-glyph"></a>Definiowanie symbolu  
 Definiowanie glifu przez implementację <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfejsu.  
  
#### <a name="to-define-the-glyph"></a>Aby zdefiniować symbol  
  
1. Dodaj plik klasy i nadaj mu nazwę `TodoGlyphFactory` .  
  
2. Dodaj następujące deklaracje using.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3. Dodaj klasę o nazwie `TodoGlyphFactory` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4. Dodaj pole prywatne, które definiuje wymiary glifu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5. Implementowanie `GenerateGlyph` przez zdefiniowanie elementu interfejsu użytkownika (UI) glifów. `TodoTag` został zdefiniowany w dalszej części tego przewodnika.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6. Dodaj klasę o nazwie `TodoGlyphFactoryProvider` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Wyeksportuj tę klasę z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> po VsTextMarker, z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" i z <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metodę, tworząc wystąpienie elementu `TodoGlyphFactory` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definiowanie znacznika do wykonania i moduł tagujący  
 Zdefiniuj relację między elementem interfejsu użytkownika zdefiniowanym w poprzednich krokach i marginesie wskaźnika, tworząc typ znacznika i moduł tagujący, a następnie eksportując go przy użyciu dostawcy moduł tagujący.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Aby zdefiniować tag do wykonania i moduł tagujący  
  
1. Dodaj nowy plik klasy do projektu i nadaj mu nazwę `TodoTagger` .  
  
2. Dodaj następujące Importy.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3. Dodaj klasę o nazwie `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4. Zmodyfikuj klasę o nazwie `TodoTagger` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Typ `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5. Do `TodoTagger` klasy Dodaj pola prywatne dla <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> i dla tekstu do znalezienia w obszarze klasyfikacji.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6. Dodaj konstruktora, który ustawia klasyfikatora.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, wyszukując wszystkie zakresy klasyfikacji, których nazwy zawierają wyraz "komentarz", którego tekst zawiera tekst wyszukiwania. Za każdym razem, gdy zostanie znaleziony tekst wyszukiwania, Przywróć Nowy <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> Typ `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8. Zadeklaruj `TagsChanged` zdarzenie.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Dodaj klasę o nazwie `TodoTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> i wyeksportuj ją z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Zaimportuj <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodę, tworząc wystąpienie elementu `TodoTagger` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Kompilowanie i testowanie kodu  
 Aby przetestować ten kod, skompiluj rozwiązanie TodoGlyphTest i uruchom je w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Aby skompilować i przetestować rozwiązanie TodoGlyphTest  
  
1. Skompiluj rozwiązanie.  
  
2. Uruchom projekt, naciskając klawisz F5. Zostanie utworzone drugie wystąpienie programu Visual Studio.  
  
3. Upewnij się, że margines wskaźnika jest pokazywany. (W menu **Narzędzia** kliknij pozycję **Opcje**. Na stronie **Edytor tekstu** upewnij się, że jest zaznaczony **margines wskaźnika** .)  
  
4. Otwórz plik kodu z komentarzami. Dodaj słowo "do zrobienia" do jednej z sekcji komentarzy.  
  
5. Jasnoniebieski okrąg, który ma ciemny niebieski kontur, powinien pojawić się na marginesie wskaźnika po lewej stronie okna kod.
