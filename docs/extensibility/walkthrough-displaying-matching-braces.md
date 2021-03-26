---
title: 'Przewodnik: wyświetlanie pasujących nawiasów klamrowych | Microsoft Docs'
description: Dowiedz się, jak definiować nawiasy klamrowe w kontekście języka, stosując w tym instruktażu znaczniki pasujące do typu zawartości tekstowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0950f6b8ed647a3922fe63e365a97ea0a888ec6e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078620"
---
# <a name="walkthrough-display-matching-braces"></a>Przewodnik: wyświetlanie pasujących nawiasów klamrowych
Implementowanie funkcji opartych na języku, takich jak, dopasowywanie nawiasów klamrowych przez definiowanie nawiasów klamrowych, które mają być dopasowane, i Dodawanie znacznika znacznika tekstu do pasujących nawiasów klamrowych, gdy karetka jest w jednym z nawiasów klamrowych. Można zdefiniować nawiasy klamrowe w kontekście języka, zdefiniować własne rozszerzenie nazwy pliku i typ zawartości oraz zastosować znaczniki do samego typu, lub zastosować znaczniki do istniejącego typu zawartości (na przykład "tekst"). W poniższym przewodniku pokazano, jak zastosować nawiasy klamrowe do typu zawartości "text".

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Utwórz projekt klasyfikatora edytora. Nadaj nazwę rozwiązanie `BraceMatchingTest` .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

## <a name="implement-a-brace-matching-tagger"></a>Implementowanie dopasowywania moduł tagujący w nawiasach klamrowych
 Aby uzyskać efekt wyróżniania nawiasów klamrowych, który jest podobny do tego, który jest używany w programie Visual Studio, można zaimplementować moduł tagujący typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Poniższy kod ilustruje sposób definiowania moduł tagujący dla par nawiasów klamrowych na dowolnym poziomie zagnieżdżenia. W tym przykładzie pary nawiasów klamrowych [] i {} są zdefiniowane w konstruktorze moduł tagujący, ale w całej implementacji języka odpowiednie pary nawiasów klamrowych byłyby zdefiniowane w specyfikacji języka.

### <a name="to-implement-a-brace-matching-tagger"></a>Aby zaimplementować moduł tagujący pasujący do nawiasu klamrowego

1. Dodaj plik klasy i nadaj mu nazwę BraceMatching.

2. Zaimportuj następujące przestrzenie nazw.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Zdefiniuj klasę `BraceMatchingTagger` , która dziedziczy po <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typie <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Dodaj właściwości widoku tekstu, bufor źródłowy, bieżący punkt migawki, a także zestaw par nawiasów klamrowych.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. W konstruktorze moduł tagujący ustaw właściwości i Zasubskrybuj widok zmiany zdarzeń <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . W tym przykładzie, w celu zilustrowania, zgodne pary są również zdefiniowane w konstruktorze.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. W ramach <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementacji Zadeklaruj zdarzenie TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Programy obsługi zdarzeń aktualizują bieżącą pozycję karetki do `CurrentChar` właściwości i generują zdarzenie TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, aby dopasować nawiasy klamrowe, gdy bieżący znak jest otwartym nawiasem klamrowym lub kiedy poprzedni znak jest zamykanym nawiasem klamrowym, jak w programie Visual Studio. Po znalezieniu dopasowania ta metoda tworzy wystąpienie dwóch tagów, po jednym dla otwierającego nawiasu klamrowego i jeden dla zamykającego nawiasu klamrowego.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Poniższe metody prywatne Znajdź pasujący nawias klamrowy na dowolnym poziomie zagnieżdżenia. Pierwsza metoda umożliwia znalezienie znaku zamykającego, który pasuje do otwartego znaku:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Poniższa metoda pomocnika umożliwia znalezienie otwartego znaku, który pasuje do znaku zamykającego:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementuj pasujący moduł tagujący dostawca w nawiasach klamrowych
 Oprócz wdrożenia moduł tagujący, należy również zaimplementować i wyeksportować dostawcę moduł tagujący. W takim przypadku typem zawartości dostawcy jest "text". Tak więc dopasowanie nawiasów klamrowych będzie wyświetlane we wszystkich typach plików tekstowych, ale pełna implementacja stosuje nawiasy klamrowe tylko do określonego typu zawartości.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Aby zaimplementować dostawcę moduł tagujący zgodny z nawiasem klamrowym

1. Zadeklaruj dostawcę moduł tagujący, który dziedziczy po <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , nadaj mu nazwę BraceMatchingTaggerProvider i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodę, aby utworzyć wystąpienie BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Kompiluj i Testuj kod
 Aby przetestować ten kod, skompiluj rozwiązanie BraceMatchingTest i uruchom je w eksperymentalnym wystąpieniu.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Aby skompilować i przetestować rozwiązanie BraceMatchingTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze uruchomione jest drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy i wpisz tekst, który zawiera pasujące nawiasy klamrowe.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Gdy umieszczasz karetkę przed otwierającym nawiasem klamrowym, należy podróżnić zarówno ten nawias klamrowy, jak i pasujący nawias zamykający. Po umieszczeniu kursora tuż po zamykającym nawiasie klamrowym, należy podróżnić zarówno ten nawias klamrowy, jak i pasujący otwierający nawias klamrowy.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
