---
title: 'Przewodnik: Tworzenie symbolu marginesu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b94ab61f56d74537758c189adc9c104516f67f92
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905055"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Przewodnik: Tworzenie symbolu marginesu
Możesz dostosować wygląd marginesów edytora przy użyciu rozszerzeń edytora niestandardowego. Ten Instruktaż umieszcza niestandardowy symbol na marginesie wskaźnika za każdym razem, gdy słowo "do zrobienia" pojawia się w komentarzu do kodu.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Tworzenie projektu MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `TodoGlyphTest` .

2. Dodaj element projektu klasyfikatora edytora. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

## <a name="define-the-glyph"></a>Definiowanie glifu
 Zdefiniuj glif, uruchamiając <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfejs.

### <a name="to-define-the-glyph"></a>Aby zdefiniować symbol

1. Dodaj plik klasy i nadaj mu nazwę `TodoGlyphFactory` .

2. Dodaj następujący kod przy użyciu deklaracji.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Dodaj klasę o nazwie `TodoGlyphFactory` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Dodaj pole prywatne, które definiuje wymiary glifu.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implementowanie `GenerateGlyph` przez zdefiniowanie elementu interfejsu użytkownika (UI) glifów. `TodoTag`został zdefiniowany w dalszej części tego przewodnika.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Dodaj klasę o nazwie `TodoGlyphFactoryProvider` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Wyeksportuj tę klasę z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> po VsTextMarker, z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" i z <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metodę, tworząc wystąpienie elementu `TodoGlyphFactory` .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Zdefiniuj tag do wykonania i moduł tagujący
 Zdefiniuj relację między elementem interfejsu użytkownika zdefiniowanym w poprzednich krokach i marginesie wskaźnika. Utwórz typ znacznika i moduł tagujący i wyeksportuj go za pomocą dostawcy moduł tagujący.

### <a name="to-define-a-todo-tag-and-tagger"></a>Aby zdefiniować tag do wykonania i moduł tagujący

1. Dodaj nowy plik klasy do projektu i nadaj mu nazwę `TodoTagger` .

2. Dodaj następujące Importy.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Dodaj klasę o nazwie `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Zmodyfikuj klasę o nazwie `TodoTagger` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Typ `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. Do `TodoTagger` klasy Dodaj pola prywatne dla <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> i dla tekstu do znalezienia w obszarze klasyfikacji.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Dodaj konstruktora, który ustawia klasyfikatora.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, wyszukując wszystkie zakresy klasyfikacji, których nazwy zawierają wyraz "komentarz", którego tekst zawiera tekst wyszukiwania. Za każdym razem, gdy zostanie znaleziony tekst wyszukiwania, Przywróć Nowy <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> Typ `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Zadeklaruj `TagsChanged` zdarzenie.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Dodaj klasę o nazwie `TodoTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> i wyeksportuj ją z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Zaimportuj <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodę, tworząc wystąpienie elementu `TodoTagger` .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Kompiluj i Testuj kod
 Aby przetestować ten kod, skompiluj rozwiązanie TodoGlyphTest i uruchom je w eksperymentalnym wystąpieniu.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Aby skompilować i przetestować rozwiązanie TodoGlyphTest

1. Skompiluj rozwiązanie.

2. Uruchom projekt, naciskając klawisz **F5**. Zostanie uruchomione drugie wystąpienie programu Visual Studio.

3. Upewnij się, że margines wskaźnika jest pokazywany. (W menu **Narzędzia** kliknij pozycję **Opcje**. Na stronie **Edytor tekstu** upewnij się, że jest zaznaczony **margines wskaźnika** .)

4. Otwórz plik kodu z komentarzami. Dodaj słowo "do zrobienia" do jednej z sekcji komentarzy.

5. Jasnoniebieski okrąg z ciemnego niebieskiego konspektu pojawia się na marginesie wskaźnika po lewej stronie okna kod.
