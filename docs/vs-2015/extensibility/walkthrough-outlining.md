---
title: 'Przewodnik: Tworzenie konspektu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c1dd3d28b9978b52c95b5ff905d57720ed10f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201958"
---
# <a name="walkthrough-outlining"></a>Przewodnik: tworzenie konspektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcje bazujące na języku, takie jak konspekt, można zaimplementować, definiując rodzaje regionów tekstu, które mają zostać rozwinięte lub zwinięte. Można zdefiniować regiony w kontekście usługi językowej lub zdefiniować własne rozszerzenie nazwy pliku i typ zawartości oraz zastosować definicję regionu tylko do tego typu lub można zastosować definicje regionów do istniejącego typu zawartości (na przykład "tekst"). W tym instruktażu pokazano, jak definiować i wyświetlać regiony konspektu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1. Utwórz projekt VSIX. Nadaj nazwę rozwiązanie `OutlineRegionTest` .  
  
2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Usuń istniejące pliki klas.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementowanie konspektu moduł tagujący  
 Regiony tworzenia konspektu są oznaczone przez rodzaj tagu ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Ten tag zawiera standardowe zachowanie konspektu. Region konspektu może być rozwinięty lub zwinięty. Region konspektu jest oznaczony znakiem PLUS, jeśli jest zwinięty lub znak MINUS, jeśli jest rozwinięty, a rozwinięty region zostaje oddzielony linią pionową.  
  
 Poniższe kroki przedstawiają sposób definiowania moduł tagujący, który tworzy regiony tworzenia konspektu dla wszystkich regionów, które są rozdzielane przez "[" i "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Aby zaimplementować konspekt moduł tagujący  
  
1. Dodaj plik klasy i nadaj mu nazwę `OutliningTagger` .  
  
2. Zaimportuj następujące przestrzenie nazw.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3. Utwórz klasę o nazwie `OutliningTagger` i zaimplementuj ją <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4. Dodaj niektóre pola, aby śledzić bufor tekstu i migawkę oraz zbierać zestawy wierszy, które powinny być otagowane jako regiony konspektu. Ten kod zawiera listę obiektów regionów (do zdefiniowania później) reprezentujących regiony konspektu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5. Dodaj Konstruktor moduł tagujący, który inicjuje pola, analizuje bufor i dodaje procedurę obsługi zdarzeń do <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, która tworzy wystąpienia znaczników. W tym przykładzie przyjęto założenie, że zakresy w <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> przekazaniu do metody są ciągłe, chociaż może to nie zawsze być przypadek. Ta metoda tworzy wystąpienie nowego zakresu tagu dla każdego regionu konspektu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7. Zadeklaruj `TagsChanged` procedurę obsługi zdarzeń.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8. Dodaj `BufferChanged` program obsługi zdarzeń, który reaguje na <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia przez analizowanie buforu tekstu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Dodaj metodę, która analizuje bufor. Przykład podanym tutaj dotyczy tylko ilustracji. Synchronicznie analizuje bufor w zagnieżdżonych regionach konspektu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. Poniższa metoda pomocnicza Pobiera liczbę całkowitą, która reprezentuje poziom konspektu, tak że 1 to para nawiasów klamrowych z lewej strony.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. Następująca metoda pomocnika tłumaczy region (zdefiniowany w dalszej części tego tematu) do element snapshotspan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Poniższy kod dotyczy tylko ilustracji. Definiuje klasę PartialRegion, która zawiera numer wiersza i przesunięcie początku regionu konspektu, a także odwołanie do regionu nadrzędnego (jeśli istnieje). Umożliwia to analizatorowi skonfigurowanie zagnieżdżonych regionów konspektu. Klasa regionu pochodnego zawiera odwołanie do numeru wiersza końca regionu konspektu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementowanie dostawcy moduł tagujący  
 Należy wyeksportować dostawcę moduł tagujący do moduł tagujący. Dostawca moduł tagujący tworzy `OutliningTagger` dla bufora typu zawartości "text" lub w przeciwnym razie zwraca wartość, `OutliningTagger` Jeśli bufor już istnieje.  
  
#### <a name="to-implement-a-tagger-provider"></a>Aby zaimplementować dostawcę moduł tagujący  
  
1. Utwórz klasę o nazwie `OutliningTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> i wyeksportuj ją z atrybutami ContentType i TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodę, dodając `OutliningTagger` do właściwości buforu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Kompilowanie i testowanie kodu  
 Aby przetestować ten kod, skompiluj rozwiązanie OutlineRegionTest i uruchom je w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Aby skompilować i przetestować rozwiązanie OutlineRegionTest  
  
1. Skompiluj rozwiązanie.  
  
2. Po uruchomieniu tego projektu w debugerze tworzone jest drugie wystąpienie programu Visual Studio.  
  
3. Utwórz plik tekstowy. Wpisz dowolny tekst, który zawiera klamrowy nawias otwierający i zamykający nawias klamrowy.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4. Powinien istnieć region konspektu, który zawiera oba nawiasy klamrowe. Powinien być w stanie kliknąć znak MINUS z lewej strony otwierającego nawiasu klamrowego, aby zwinąć region tworzenia konspektu. Gdy region jest zwinięty, symbol wielokropka (...) powinien pojawić się po lewej stronie zwiniętego regionu, a po umieszczeniu wskaźnika na wielokropku powinien pojawić się okno podręczne zawierające **tekst** umieszczania tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
