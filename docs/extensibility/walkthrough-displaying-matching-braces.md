---
title: 'Instruktaż: Wyświetlanie pasujących nawiasów klamrowych | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 107610733ab9b5c8085b3f987fa999250b453d63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697451"
---
# <a name="walkthrough-display-matching-braces"></a>Instruktaż: Wyświetlanie pasujących nawiasów klamrowych
Zaimplementuj funkcje oparte na języku, takie jak dopasowywanie nawiasów klamrowych, definiując nawiasy klamrowe, które chcesz dopasować, i dodając znacznik tekstowy do pasujących nawiasów klamrowych, gdy daszkownik znajduje się na jednej z nawiasów klamrowych. Można zdefiniować nawiasy klamrowe w kontekście języka, zdefiniować własne rozszerzenie nazwy pliku i typ zawartości oraz zastosować znaczniki tylko do tego typu lub zastosować znaczniki do istniejącego typu zawartości (takiego jak "tekst"). Poniższy przewodnik pokazuje, jak zastosować tagi pasujące nawiasy klamrowe do typu zawartości "tekst".

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu managed extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Tworzenie projektu klasyfikatora edytora. Nazwij `BraceMatchingTest`rozwiązanie .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

## <a name="implement-a-brace-matching-tagger"></a>Implementowanie tagera pasującego nawiasu klamrowego
 Aby uzyskać efekt podświetlania nawiasu, który przypomina ten, który jest używany w <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>programie Visual Studio, można zaimplementować tager typu . Poniższy kod pokazuje, jak zdefiniować tager dla par nawiasów klamrowych na dowolnym poziomie zagnieżdżania. W tym przykładzie par nawiasów klamrowych [] i {} są zdefiniowane w konstruktorze tager, ale w pełnej implementacji języka odpowiednie pary nawiasów klamrowych zostaną zdefiniowane w specyfikacji języka.

### <a name="to-implement-a-brace-matching-tagger"></a>Aby zaimplementować tager dopasowania nawiasu klamrowego

1. Dodaj plik klasy i nadaj jej nazwę Nawiasy klamrowe.

2. Zaimportuj następujące obszary nazw.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Zdefiniuj `BraceMatchingTagger` klasę <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> dziedziczącą z typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Dodaj właściwości widoku tekstu, buforu źródłowego, bieżącego punktu migawki, a także zestawu par nawiasów klamrowych.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. W konstruktorze znaczników ustaw właściwości i subskrybuj <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>zdarzenia zmiany widoku i . W tym przykładzie dla celów ilustracyjnych pasujące pary są również zdefiniowane w konstruktorze.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. W ramach <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementacji oświadcza zdarzenie TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Programy obsługi zdarzeń zaktualizować bieżącą pozycję `CurrentChar` opiekuna właściwości i podnieść TagsChanged zdarzenia.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę dopasowania nawiasów klamrowych, gdy bieżący znak jest otwartym nawiasem klamrowym lub gdy poprzedni znak jest nawiasem klamrowym, jak w programie Visual Studio. Po znalezieniu dopasowania ta metoda powoduje wystąpienie dwóch tagów, jednego dla otwartego nawiasu klamrowego i jednego dla nawiasu klamrowego.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Następujące metody prywatne znaleźć pasujące nawiasy klamrowe na dowolnym poziomie zagnieżdżania. Pierwsza metoda znajduje znak zamknięcia, który pasuje do otwartego znaku:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Następująca metoda pomocnika znajduje otwarty znak, który pasuje do bliskiego znaku:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementowanie dostawcy tagera pasującego nawiasu klamrowego
 Oprócz implementowania tager, należy również zaimplementować i wyeksportować dostawcę tager. W takim przypadku typem zawartości dostawcy jest "tekst". Tak, dopasowywanie nawiasów klamrowych pojawi się we wszystkich typach plików tekstowych, ale pełniejsza implementacja stosuje nawias klamrowy pasujący tylko do określonego typu zawartości.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Aby zaimplementować dostawcę tagera pasującego nawiasu

1. Zadeklaruj dostawcę <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>znacznika, który dziedziczy po , nazwać Go BraceMatchingTaggerProvider i wyeksportować go z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "tekst" i . <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodę tworzenia wystąpienia funkcji BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu
 Aby przetestować ten kod, skompiluj rozwiązanie BraceMatchingTest i uruchom go w wystąpieniu eksperymentalnym.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Aby utworzyć i przetestować rozwiązanie BraceMatchingTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze zostanie uruchomione drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy i wpisz tekst zawierający pasujące nawiasy klamrowe.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Po umieszczeniu karetki przed otwartym nawiasem klamrowym należy wyróżnić zarówno ten nawias klamrowy, jak i pasujący nawias klamrowy. Po umieszczeniu kursora tuż po zamknięciu nawiasu klamrowego należy wyróżnić zarówno ten nawias klamrowy, jak i pasujący otwarty nawias klamrowy.

## <a name="see-also"></a>Zobacz też
- [Instruktaż: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
