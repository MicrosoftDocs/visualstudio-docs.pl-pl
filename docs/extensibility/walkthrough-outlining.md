---
title: 'Przewodnik: Konspekt | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7de78a60dd7de129eb2626e414ce6ec44bb20ce3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827526"
---
# <a name="walkthrough-outlining"></a>Przewodnik: Tworzenie konspektu
Konfigurowanie opartych na języku funkcje, takie jak tworzenie konspektu, definiując rodzaje regionów tekst, który chcesz rozwinąć lub zwinąć. Można zdefiniować regionów w kontekście usługi języka lub zdefiniować własny plik Nazwa rozszerzenia i zawartości typ i stosowanie definicji region tylko do tego typu lub zastosować definicje region do istniejącego typu zawartości (na przykład "text"). Ten poradnik pokazuje jak zdefiniować i wyświetlanie konspektu regionów.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie instaluj programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Utwórz projekt Managed Extensibility Framework (MEF)  
  
### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1.  Utwórz projekt VSIX. Nazwij rozwiązanie `OutlineRegionTest`.  
  
2.  Dodaj szablon elementu edytora klasyfikatora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń istniejące pliki klasy.  
  
## <a name="implement-an-outlining-tagger"></a>Implementowanie konspektu moduł tagujący  
 Konspektu regiony są oznaczone według rodzaju tagu (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Ten tag udostępnia standardowy konspekt zachowanie. Schemat regionu można można rozwijać i zwijać. Schemat region jest oznaczona przez znak Plus (**+**), jeśli jest zwinięte lub znak Minus (**-**) Jeśli jest on rozwinięty i rozwinięty region jest zaznaczonymi przez pionowym wierszem.  
  
 Poniższe kroki pokazują jak zdefiniować moduł tagujący, tworzącą konspektu regiony dla wszystkich regionów, które są rozdzielane znakami nawiasy (**[**,**]**).  
  
### <a name="to-implement-an-outlining-tagger"></a>Aby zaimplementować konspektu moduł tagujący  
  
1.  Dodaj plik klasy i nadaj mu nazwę `OutliningTagger`.  
  
2.  Zaimportuj następujące przestrzenie nazw.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Utwórz klasę o nazwie `OutliningTagger`, potem z łatwością wdrożyć <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Dodaj pola do śledzenia bufora tekstowego i migawki i są gromadzone zestawów wierszy, które powinny zostać oznaczony jako zwijanie regionów. Ten kod zawiera listę obiektów Region (do ustalenia później), które reprezentują konspektu regionów.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Dodaj Konstruktor moduł tagujący, która inicjuje pól, analizowania buforu, i dodaje procedurę obsługi zdarzeń do <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> obejmuje metodę, która tworzy wystąpienie tagu. W tym przykładzie założono, że zakresy w <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> przekazanego do metody są ciągłe, chociaż nie zawsze wymagane. Ta metoda tworzy nowy zakres tagów dla poszczególnych regionów konspektu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Zadeklaruj `TagsChanged` programu obsługi zdarzeń.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Dodaj `BufferChanged` programu obsługi zdarzeń, które odpowiada <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia według podczas analizowania buforu tekstowego.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Dodaj metodę, która analizuje buforu. Przykład podany w tym miejscu jest wyłącznie do celów informacyjnych. Analizuje synchronicznie buforu w zagnieżdżonych konspektu regionów.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. Następującą metodę pomocnika pobiera liczba całkowita, która reprezentuje stopień konspektu, w taki sposób, że 1 jest parę nawiasów skrajnie po lewej stronie.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. Następującą metodę pomocnika tłumaczy Region (zdefiniowane w dalszej części tego artykułu) na element SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. Poniższy kod jest wyłącznie do celów informacyjnych. Definiuje klasę PartialRegion, który zawiera numer wiersza i przesunięcia początkowego konspektu region i odwołanie do regionu nadrzędnego (jeśli istnieje). Ten kod umożliwia analizatora składni skonfigurować zagnieżdżone zwijanie regionów. Klasa pochodna Region zawiera odwołanie do numeru wiersza końcowego konspektu regionu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implement-a-tagger-provider"></a>Implementowanie dostawcy moduł tagujący  
 Wyeksportuj moduł tagujący dostawcę dla Twojego moduł tagujący. Tworzy dostawcę moduł tagujący `OutliningTagger` dla buforu "text" typ zawartości lub inne zwraca `OutliningTagger` Jeśli bufor zawiera już jeden.  
  
### <a name="to-implement-a-tagger-provider"></a>Aby zaimplementować dostawcę moduł tagujący  
  
1.  Utwórz klasę o nazwie `OutliningTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>i wyeksportuj go za pomocą atrybutów ContentType i typu tag.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metody, dodając `OutliningTagger` właściwości buforu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu  
 Aby przetestować ten kod, Kompiluj rozwiązanie OutlineRegionTest, a następnie uruchomić go w doświadczalnym wystąpieniu.  
  
### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Aby skompilować i przetestować rozwiązanie OutlineRegionTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio został uruchomiony.  
  
3.  Utwórz plik tekstowy. Wpisz jakiś tekst, który zawiera zarówno otwierające nawiasy i zamykających nawiasów kwadratowych.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Powinna istnieć konspektu region, który zawiera oba nawiasy kwadratowe. Można kliknąć przycisk z lewej strony otwierającego nawiasu znak Minus, aby zwinąć konspektu regionu. Gdy region jest zwinięte, symbol wielokropka (*...* ) powinien pojawić się po lewej stronie Zwinięty region, a okno podręczne zawierające tekst **umieść tekst** powinien zostać wyświetlony po umieszczeniu wskaźnika na wielokropek.  
  
## <a name="see-also"></a>Zobacz także  
 [Przewodnik: Połączyć typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)