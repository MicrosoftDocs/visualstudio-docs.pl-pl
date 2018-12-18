---
title: 'Wskazówki: Tworzenie konspektu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 897ff6a39716f424c40fa587d905847a0dbb3682
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805271"
---
# <a name="walkthrough-outlining"></a>Przewodnik: tworzenie konspektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz zaimplementować opartych na języku funkcje, takie jak tworzenie konspektu, definiując rodzaje regionów tekst, który chcesz rozwinąć lub zwinąć. Regiony można zdefiniować w kontekście usługi językowej, można zdefiniować własny plik Nazwa rozszerzenia i zawartości typ i zastosować definicji region tylko do tego typu lub definicje regionu można zastosować do istniejącego typu zawartości (na przykład "text"). Ten poradnik pokazuje jak zdefiniować i wyświetlanie konspektu regionów.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Framework (MEF) zarządzanych rozszerzeń  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1.  Utwórz projekt VSIX. Nazwij rozwiązanie `OutlineRegionTest`.  
  
2.  Dodaj szablon elementu edytora klasyfikatora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń istniejące pliki klasy.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementowanie konspektu moduł Tagujący  
 Konspektu regiony są oznaczone według rodzaju tagu (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Ten tag udostępnia standardowy konspekt zachowanie. Schemat regionu można można rozwijać i zwijać. Schemat region jest oznaczony za plus, jeśli jest zwinięte lub znaku MINUS, jeśli jest on rozwinięty i rozwinięty region jest zaznaczonymi przez pionowym wierszem.  
  
 Poniższe kroki pokazują jak zdefiniować moduł tagujący, tworzącą konspektu regiony dla wszystkich regionów, które są rozdzielane znakami "[" i "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Aby zaimplementować konspektu moduł tagujący  
  
1.  Dodaj plik klasy i nadaj mu nazwę `OutliningTagger`.  
  
2.  Zaimportuj następujące przestrzenie nazw.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3.  Utwórz klasę o nazwie `OutliningTagger`, potem z łatwością wdrożyć <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4.  Dodaj pola do śledzenia bufora tekstowego i migawki i są gromadzone zestawów wierszy, które powinny zostać oznaczony jako zwijanie regionów. Ten kod zawiera listę obiektów Region (do ustalenia później), które reprezentują konspektu regionów.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5.  Dodaj Konstruktor moduł tagujący, która inicjuje pól, analizowania buforu, i dodaje procedurę obsługi zdarzeń do <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> obejmuje metodę, która tworzy wystąpienie tagu. W tym przykładzie założono, że zakresy w <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> przekazanego do metody są ciągłe, mimo że to nie zawsze jest wymagane. Ta metoda tworzy nowy zakres tagów dla poszczególnych regionów konspektu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7.  Zadeklaruj `TagsChanged` programu obsługi zdarzeń.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8.  Dodaj `BufferChanged` programu obsługi zdarzeń, które odpowiada <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia według podczas analizowania buforu tekstowego.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Dodaj metodę, która analizuje buforu. Przykład podany w tym miejscu jest wyłącznie do celów informacyjnych. Analizuje synchronicznie buforu w zagnieżdżonych konspektu regionów.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. Następującą metodę pomocnika pobiera liczba całkowita, która reprezentuje stopień konspektu, w taki sposób, że 1 jest parę nawiasów skrajnie po lewej stronie.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. Następującą metodę pomocnika tłumaczy Region (zdefiniowane w dalszej części tego tematu) na element SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Poniższy kod jest wyłącznie do celów informacyjnych. Definiuje klasę PartialRegion, który zawiera numer wiersza i przesunięcia początkowego konspektu regionu, a także odwołanie do regionu nadrzędnego (jeśli istnieje). Dzięki temu analizatora składni skonfigurować zagnieżdżone zwijanie regionów. Klasa pochodna Region zawiera odwołanie do numeru wiersza końcowego konspektu regionu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementowanie dostawcy moduł Tagujący  
 Dostawca moduł tagujący należy wyeksportować dla Twojego moduł tagujący. Tworzy dostawcę moduł tagujący `OutliningTagger` dla buforu "text" typ zawartości lub inne zwraca `OutliningTagger` Jeśli bufor zawiera już jeden.  
  
#### <a name="to-implement-a-tagger-provider"></a>Aby zaimplementować dostawcę moduł tagujący  
  
1.  Utwórz klasę o nazwie `OutliningTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>i wyeksportuj go za pomocą atrybutów ContentType i typu tag.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metody, dodając `OutliningTagger` właściwości buforu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Aby przetestować ten kod, Kompiluj rozwiązanie OutlineRegionTest, a następnie uruchomić go w doświadczalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Aby skompilować i przetestować rozwiązanie OutlineRegionTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze drugiego wystąpienia programu Visual Studio jest uruchomiony.  
  
3.  Utwórz plik tekstowy. Wpisz jakiś tekst, który zawiera nawias klamrowy otwierający i zamykający nawias klamrowy.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Powinna istnieć konspektu region, który zawiera oba nawiasów klamrowych. Można kliknąć przycisk z lewej strony otwierający nawias klamrowy znak MINUS, aby zwinąć konspektu regionu. Gdy region jest zwinięte, symbol wielokropka (...) powinien pojawić się po lewej stronie Zwinięty region, a okno podręczne zawierające tekst **umieść tekst** powinien zostać wyświetlony po umieszczeniu wskaźnika na wielokropek.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

