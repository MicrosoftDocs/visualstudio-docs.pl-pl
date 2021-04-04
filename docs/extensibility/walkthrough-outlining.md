---
title: 'Przewodnik: Tworzenie konspektu | Microsoft Docs'
description: Dowiedz się, jak definiować i wyświetlać regiony tworzenia konspektu w kontekście usługi językowej lub własnego rozszerzenia nazwy pliku i typu zawartości.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7bf4c0cc8757ea4f034da2ac17d6c76971f86305
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217232"
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

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet1":::

3. Utwórz klasę o nazwie `OutliningTagger` i zaimplementuj ją <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet2":::

4. Dodaj niektóre pola, aby śledzić bufor tekstu i migawkę oraz zbierać zestawy wierszy, które powinny być otagowane jako regiony konspektu. Ten kod zawiera listę obiektów regionów (do zdefiniowania później) reprezentujących regiony konspektu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet3":::

5. Dodaj Konstruktor moduł tagujący, który inicjuje pola, analizuje bufor i dodaje procedurę obsługi zdarzeń do <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet4":::

6. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, która tworzy wystąpienia znaczników. W tym przykładzie przyjęto założenie, że zakresy w <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> przekazaniu do metody są ciągłe, chociaż może to nie zawsze być przypadek. Ta metoda tworzy wystąpienie nowego zakresu tagu dla każdego regionu konspektu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet5":::

7. Zadeklaruj `TagsChanged` procedurę obsługi zdarzeń.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet6":::

8. Dodaj `BufferChanged` program obsługi zdarzeń, który reaguje na <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia przez analizowanie buforu tekstu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet7":::

9. Dodaj metodę, która analizuje bufor. Przykład podanym tutaj dotyczy tylko ilustracji. Synchronicznie analizuje bufor w zagnieżdżonych regionach konspektu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet8":::

10. Poniższa metoda pomocnicza Pobiera liczbę całkowitą, która reprezentuje poziom konspektu, tak że 1 to para nawiasów klamrowych z lewej strony.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet9":::

11. Następująca metoda pomocnika tłumaczy region (zdefiniowany w dalszej części tego artykułu) do element snapshotspan.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet10":::

12. Poniższy kod dotyczy tylko ilustracji. Definiuje klasę PartialRegion, która zawiera numer wiersza i przesunięcie początku regionu konspektu oraz odwołanie do regionu nadrzędnego (jeśli istnieje). Ten kod umożliwia analizatorowi skonfigurowanie zagnieżdżonych regionów konspektu. Klasa regionu pochodnego zawiera odwołanie do numeru wiersza końca regionu konspektu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet11":::

## <a name="implement-a-tagger-provider"></a>Implementowanie dostawcy moduł tagujący
 Wyeksportuj dostawcę moduł tagujący do moduł tagujący. Dostawca moduł tagujący tworzy `OutliningTagger` dla bufora typu zawartości "text" lub w przeciwnym razie zwraca wartość, `OutliningTagger` Jeśli bufor już istnieje.

### <a name="to-implement-a-tagger-provider"></a>Aby zaimplementować dostawcę moduł tagujący

1. Utwórz klasę o nazwie `OutliningTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> i wyeksportuj ją z atrybutami ContentType i TagType.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet12":::

2. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodę, dodając `OutliningTagger` do właściwości buforu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet13":::

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
