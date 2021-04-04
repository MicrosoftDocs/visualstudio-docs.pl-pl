---
title: 'Przewodnik: Tworzenie symbolu marginesu | Microsoft Docs'
description: Dowiedz się, jak dostosować wygląd marginesów edytora przy użyciu rozszerzeń edytora niestandardowego, korzystając z tego przewodnika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec5eecef40220c2cf2d4e3f1ece8eb5eb763bdeb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217414"
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

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet1":::

3. Dodaj klasę o nazwie `TodoGlyphFactory` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet2":::

4. Dodaj pole prywatne, które definiuje wymiary glifu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet3":::

5. Implementowanie `GenerateGlyph` przez zdefiniowanie elementu interfejsu użytkownika (UI) glifów. `TodoTag` został zdefiniowany w dalszej części tego przewodnika.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet4":::

6. Dodaj klasę o nazwie `TodoGlyphFactoryProvider` implementującej <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Wyeksportuj tę klasę z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> po VsTextMarker, z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" i z <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet5":::

7. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metodę, tworząc wystąpienie elementu `TodoGlyphFactory` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet6":::

## <a name="define-a-todo-tag-and-tagger"></a>Zdefiniuj tag do wykonania i moduł tagujący
 Zdefiniuj relację między elementem interfejsu użytkownika zdefiniowanym w poprzednich krokach i marginesie wskaźnika. Utwórz typ znacznika i moduł tagujący i wyeksportuj go za pomocą dostawcy moduł tagujący.

### <a name="to-define-a-todo-tag-and-tagger"></a>Aby zdefiniować tag do wykonania i moduł tagujący

1. Dodaj nowy plik klasy do projektu i nadaj mu nazwę `TodoTagger` .

2. Dodaj następujące Importy.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet7":::

3. Dodaj klasę o nazwie `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet8":::

4. Zmodyfikuj klasę o nazwie `TodoTagger` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Typ `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet9":::

5. Do `TodoTagger` klasy Dodaj pola prywatne dla <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> i dla tekstu do znalezienia w obszarze klasyfikacji.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet10":::

6. Dodaj konstruktora, który ustawia klasyfikatora.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet11":::

7. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, wyszukując wszystkie zakresy klasyfikacji, których nazwy zawierają wyraz "komentarz", którego tekst zawiera tekst wyszukiwania. Za każdym razem, gdy zostanie znaleziony tekst wyszukiwania, Przywróć Nowy <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> Typ `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet12":::

8. Zadeklaruj `TagsChanged` zdarzenie.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet13":::

9. Dodaj klasę o nazwie `TodoTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> i wyeksportuj ją z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet14":::

10. Zaimportuj <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet15":::

11. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodę, tworząc wystąpienie elementu `TodoTagger` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet16":::

## <a name="build-and-test-the-code"></a>Kompiluj i Testuj kod
 Aby przetestować ten kod, skompiluj rozwiązanie TodoGlyphTest i uruchom je w eksperymentalnym wystąpieniu.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Aby skompilować i przetestować rozwiązanie TodoGlyphTest

1. Skompiluj rozwiązanie.

2. Uruchom projekt, naciskając klawisz **F5**. Zostanie uruchomione drugie wystąpienie programu Visual Studio.

3. Upewnij się, że margines wskaźnika jest pokazywany. (W menu **Narzędzia** kliknij pozycję **Opcje**. Na stronie **Edytor tekstu** upewnij się, że jest zaznaczony **margines wskaźnika** .)

4. Otwórz plik kodu z komentarzami. Dodaj słowo "do zrobienia" do jednej z sekcji komentarzy.

5. Jasnoniebieski okrąg z ciemnego niebieskiego konspektu pojawia się na marginesie wskaźnika po lewej stronie okna kod.
