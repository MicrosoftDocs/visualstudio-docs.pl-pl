---
title: 'Przewodnik: Tworzenie konspektu | Microsoft Docs'
description: Dowiedz się, jak definiować i wyświetlać regiony tworzenia konspektu w kontekście usługi językowej lub własnego rozszerzenia nazwy pliku i typu zawartości.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: ea0f16deee17e2cd249c0ee1de0861a936abc75c
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877900"
---
# <a name="walkthrough-outlining"></a>Przewodnik: tworzenie konspektu
Skonfiguruj funkcje oparte na języku, takie jak konspekt, definiując rodzaje regionów tekstu, które chcesz rozwinąć lub zwinąć. Można zdefiniować regiony w kontekście usługi językowej lub zdefiniować własne rozszerzenie nazwy pliku i typ zawartości oraz zastosować definicję regionu tylko do tego typu lub zastosować definicje regionów do istniejącego typu zawartości (na przykład "tekst"). W tym instruktażu pokazano, jak definiować i wyświetlać regiony konspektu.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Managed Extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Utwórz projekt VSIX. Nadaj nazwę rozwiązanie `OutlineRegionTest` .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

## <a name="implement-an-outlining-tagger"></a>Zaimplementuj moduł tagujący konspektu
 Regiony tworzenia konspektu są oznaczone przez rodzaj tagu ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Ten tag zawiera standardowe zachowanie konspektu. Region konspektu może być rozwinięty lub zwinięty. Region konspektu jest oznaczony znakiem plus ( **+** ), jeśli jest zwinięty lub znak minus ( **-** ), jeśli jest rozwinięty, a rozwinięty region zostaje oddzielony linią pionową.

 Poniższe kroki przedstawiają sposób definiowania moduł tagujący, który tworzy regiony tworzenia konspektu dla wszystkich regionów ograniczonych nawiasami (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Aby zaimplementować konspekt moduł tagujący

1. Dodaj plik klasy i nadaj mu nazwę `OutliningTagger` .

2. Zaimportuj następujące przestrzenie nazw.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Utwórz klasę o nazwie `OutliningTagger` i zaimplementuj ją <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Dodaj niektóre pola, aby śledzić bufor tekstu i migawkę oraz zbierać zestawy wierszy, które powinny być otagowane jako regiony konspektu. Ten kod zawiera listę obiektów regionów (do zdefiniowania później) reprezentujących regiony konspektu.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Dodaj Konstruktor moduł tagujący, który inicjuje pola, analizuje bufor i dodaje procedurę obsługi zdarzeń do <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, która tworzy wystąpienia znaczników. W tym przykładzie przyjęto założenie, że zakresy w <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> przekazaniu do metody są ciągłe, chociaż może to nie zawsze być przypadek. Ta metoda tworzy wystąpienie nowego zakresu tagu dla każdego regionu konspektu.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Zadeklaruj `TagsChanged` procedurę obsługi zdarzeń.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Dodaj `BufferChanged` program obsługi zdarzeń, który reaguje na <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia przez analizowanie buforu tekstu.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Dodaj metodę, która analizuje bufor. Przykład podanym tutaj dotyczy tylko ilustracji. Synchronicznie analizuje bufor w zagnieżdżonych regionach konspektu.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Poniższa metoda pomocnicza Pobiera liczbę całkowitą, która reprezentuje poziom konspektu, tak że 1 to para nawiasów klamrowych z lewej strony.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Następująca metoda pomocnika tłumaczy region (zdefiniowany w dalszej części tego artykułu) do element snapshotspan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Poniższy kod dotyczy tylko ilustracji. Definiuje klasę PartialRegion, która zawiera numer wiersza i przesunięcie początku regionu konspektu oraz odwołanie do regionu nadrzędnego (jeśli istnieje). Ten kod umożliwia analizatorowi skonfigurowanie zagnieżdżonych regionów konspektu. Klasa regionu pochodnego zawiera odwołanie do numeru wiersza końca regionu konspektu.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementowanie dostawcy moduł tagujący
 Wyeksportuj dostawcę moduł tagujący do moduł tagujący. Dostawca moduł tagujący tworzy `OutliningTagger` dla bufora typu zawartości "text" lub w przeciwnym razie zwraca wartość, `OutliningTagger` Jeśli bufor już istnieje.

### <a name="to-implement-a-tagger-provider"></a>Aby zaimplementować dostawcę moduł tagujący

1. Utwórz klasę o nazwie `OutliningTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> i wyeksportuj ją z atrybutami ContentType i TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodę, dodając `OutliningTagger` do właściwości buforu.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Kompiluj i Testuj kod
 Aby przetestować ten kod, skompiluj rozwiązanie OutlineRegionTest i uruchom je w eksperymentalnym wystąpieniu.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Aby skompilować i przetestować rozwiązanie OutlineRegionTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze uruchomione jest drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy. Wpisz dowolny tekst, który zawiera nawiasy otwierające i zamykające nawiasy klamrowe.

    ```
    [
       Hello
    ]
    ```

4. Powinien istnieć region konspektu, który zawiera oba nawiasy. Aby zwinąć region tworzenia konspektu, powinno być możliwe kliknięcie znaku minus z lewej strony otwierającego nawiasu klamrowego. Gdy region jest zwinięty, symbol wielokropka (*...*) powinien pojawić się po lewej stronie zwiniętego regionu, a po umieszczeniu wskaźnika na wielokropku powinien pojawić się okno podręczne zawierające **tekst** umieszczania tekstu.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
