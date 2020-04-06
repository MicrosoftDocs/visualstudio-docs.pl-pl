---
title: 'Przewodnik: Tworzenie glifów marginesu | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9588b150dd795fc2bc5e6c55d8f6e2359f609939
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697701"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Instruktaż: tworzenie glifów marginesu
Wygląd marginesów edytora można dostosować za pomocą niestandardowych rozszerzeń edytora. W tym instruktażu umieszcza niestandardowy glif na marginesie wskaźnika, gdy słowo "todo" pojawia się w komentarzu do kodu.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Tworzenie projektu MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C# / Extensibility**, a następnie **VSIX Project**.) Nazwij `TodoGlyphTest`rozwiązanie .

2. Dodaj element projektu klasyfikatora edytora. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

## <a name="define-the-glyph"></a>Zdefiniuj glif
 Zdefiniuj glif, <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> uruchamiając interfejs.

### <a name="to-define-the-glyph"></a>Aby zdefiniować glif

1. Dodaj plik klasy i `TodoGlyphFactory`nadaj jego nazwę .

2. Dodaj następujący kod przy użyciu deklaracji.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Dodaj klasę `TodoGlyphFactory` o nazwie, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Dodaj pole prywatne definiujące wymiary glifu.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implementuj przez zdefiniowanie elementu interfejsu użytkownika glifów.Implementing `GenerateGlyph` by defining the glyph user interface (UI) element. `TodoTag`jest zdefiniowany w dalszej części tego przewodnika.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Dodaj klasę `TodoGlyphFactoryProvider` o nazwie, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Eksportuj tę <xref:Microsoft.VisualStudio.Utilities.NameAttribute> klasę z "TodoGlyph", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Po VsTextMarker, a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> "code" i TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metodę, tworząc wystąpienie pliku `TodoGlyphFactory`.

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Definiowanie znacznika Todo i znacznika
 Zdefiniuj relację między elementem interfejsu użytkownika zdefiniowanym w poprzednich krokach a marginesem wskaźnika. Utwórz typ tagu i znacznik i wyeksportuj go za pomocą dostawcy znaczników.

### <a name="to-define-a-todo-tag-and-tagger"></a>Aby zdefiniować znacznik todo i znacznik

1. Dodaj nowy plik klasy do projektu `TodoTagger`i nadaj jego nazwę .

2. Dodaj następujące importy.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Dodaj klasę `TodoTag`o nazwie .

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Zmodyfikuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> klasę `TodoTag`o nazwie, `TodoTagger` która implementuje typ .

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. Do `TodoTagger` klasy dodaj pola prywatne <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> dla i dla tekstu, aby znaleźć w zakresach klasyfikacji.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Dodaj konstruktora, który ustawia klasyfikatora.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, znajdując wszystkie zakresy klasyfikacji, których nazwy zawierają słowo "komentarz" i których tekst zawiera tekst wyszukiwania. Za każdym razem, gdy zostanie znaleziony <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> wyszukiwany tekst, odwróć nowy typ `TodoTag`.

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Zadeklaruj `TagsChanged` zdarzenie.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Dodaj klasę `TodoTaggerProvider` o nazwie, która implementuje , i wyeksportuj <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ją z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "kod" <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> i TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Zaimportuj plik <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodę, tworząc wystąpienie pliku `TodoTagger`.

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu
 Aby przetestować ten kod, skompiluj rozwiązanie TodoGlyphTest i uruchom go w wystąpieniu eksperymentalnym.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Aby zbudować i przetestować rozwiązanie TodoGlyphTest

1. Skompiluj rozwiązanie.

2. Uruchom projekt, naciskając klawisz **F5**. Rozpoczyna się drugie wystąpienie programu Visual Studio.

3. Upewnij się, że margines wskaźnika jest wyświetlany. (W menu **Narzędzia** kliknij polecenie **Opcje**. Na stronie **Edytor tekstu** upewnij się, że zaznaczony jest **margines wskaźnika).**

4. Otwórz plik kodu zawierający komentarze. Dodaj słowo "todo" do jednej z sekcji komentarzy.

5. Jasnoniebieski okrąg z ciemnoniebieskim konturem pojawia się na marginesie wskaźnika po lewej stronie okna kodu.
