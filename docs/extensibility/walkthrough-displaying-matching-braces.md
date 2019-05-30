---
title: 'Przewodnik: Wyświetlanie, dopasowywanie nawiasów klamrowych | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bbea179eb2140706ee868a8a48215e7f490f57d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312521"
---
# <a name="walkthrough-display-matching-braces"></a>Przewodnik: Wyświetlanie parowanych nawiasów klamrowych
Implementuje funkcje opartych na języku, np. parowanie nawiasów klamrowych, definiując nawiasy klamrowe, które chcesz dopasować i dodaniu tekstu znacznika do parowanych nawiasów klamrowych po karetce na jednym z nawiasami klamrowymi. Można zdefiniować nawiasy klamrowe w kontekście języka, zdefiniować własne rozszerzenia nazwy pliku i typu zawartości i zastosować znaczniki do dokładnie, wpisz lub zastosować znaczniki do istniejącego typu zawartości (na przykład "text"). Następujące instruktaż przedstawia sposób zastosowania parowanie nawiasów klamrowych tagów, aby typ zawartości "text".

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie instaluj programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Utwórz projekt Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Utwórz projekt Klasifikace edytora. Nazwij rozwiązanie `BraceMatchingTest`.

2. Dodaj szablon elementu edytora klasyfikatora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klasy.

## <a name="implement-a-brace-matching-tagger"></a>Implementowanie dopasowania moduł tagujący nawiasu klamrowego
 Aby uzyskać nawiasu klamrowego wyróżnianie efekt, który przypomina ten, który jest używany w programie Visual Studio, można zaimplementować moduł tagujący typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Poniższy kod przedstawia sposób definiowania moduł tagujący dla par nawiasu klamrowego na każdym poziomie zagnieżdżania. W tym przykładzie pary nawiasów [] i {} są zdefiniowane w Konstruktorze moduł tagujący, ale w implementacji pełną obsługą języka lub odpowiednie nawias klamrowy pary zostaną zdefiniowane w specyfikacji języka.

### <a name="to-implement-a-brace-matching-tagger"></a>Aby zaimplementować dopasowania moduł tagujący nawiasu klamrowego

1. Dodaj plik klasy i nadaj mu nazwę BraceMatching.

2. Zaimportuj następujące przestrzenie nazw.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Zdefiniuj klasę `BraceMatchingTagger` tej, która dziedziczy <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Dodaj właściwości widoku tekstu, bufor źródłowy, bieżący punkt migawki, a także zestaw par nawiasu klamrowego.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. W Konstruktorze moduł tagujący Ustaw właściwości i subskrybowanie zdarzeń zmiany widoku <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. W tym przykładzie w celach ilustracyjnych, pasujących par są także definiowane w konstruktorze.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Jako część <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementacji zadeklarować zdarzenia TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Programy obsługi zdarzeń aktualizacji w bieżącym położeniu karetki `CurrentChar` właściwość i zgłoś zdarzenie TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, aby dopasować nawiasy klamrowe albo gdy bieżący znak jest otwierający nawias klamrowy, lub gdy poprzedni znak jest bliskie nawiasu klamrowego, tak jak w programie Visual Studio. Gdy zostanie znalezione dopasowanie, ta metoda tworzy dwa tagi: jeden dla otwierający nawias klamrowy, a drugi dla Zamknij nawiasu klamrowego.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Następujące metody prywatne znaleźć pasujący nawias klamrowy na każdym poziomie zagnieżdżania. Pierwsza metoda umożliwia znalezienie Zamknij znak, który pasuje do znaku Otwórz:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Następującą metodę pomocnika umożliwia znalezienie Otwórz znak, który pasuje do znaku Zamknij:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementowanie dostawcy moduł tagujący pasującego nawiasu klamrowego
 Oprócz wykonywania moduł tagujący, można także wdrożyć i eksportować dostawcy moduł tagujący. W takim przypadku zawartości typ dostawcy jest "text". Tak parowanie nawiasów klamrowych pojawi się na wszystkich typów plików tekstowych, ale pełniejszego implementacji stosuje parowanie nawiasów klamrowych tylko do określonego typu zawartości.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Do implementowania dostawcy moduł tagujący pasującego nawiasu klamrowego

1. Zadeklaruj dostawcy moduł tagujący, która dziedziczy <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, a następnie nadaj mu nazwę BraceMatchingTaggerProvider i wyeksportować je za pomocą <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodę, aby utworzyć wystąpienie BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu
 Aby przetestować ten kod, Kompiluj rozwiązanie BraceMatchingTest, a następnie uruchomić go w doświadczalnym wystąpieniu.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Aby skompilować i przetestować rozwiązanie BraceMatchingTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio został uruchomiony.

3. Utwórz plik tekstowy, a następnie wpisz dowolny tekst, który zawiera pasujące nawiasy klamrowe.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Po umieszczeniu karetki przed otwierający nawias klamrowy, powinien być wyróżniony tego nawiasów i zamknij nawiasów. Gdy umieścisz kursor zaraz po Zamknij nawias klamrowy, powinien być wyróżniony tego nawiasów i otwierający nawias klamrowy dopasowania.

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Połączyć typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)