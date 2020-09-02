---
title: 'Przewodnik: wyświetlanie pasujących nawiasów klamrowych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caaafd0143d3b09a51518ee5f54a02b06dbf10aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165781"
---
# <a name="walkthrough-displaying-matching-braces"></a>Przewodnik: wyświetlanie parowanych nawiasów klamrowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zaimplementować funkcje oparte na języku, takie jak dopasowanie nawiasów klamrowych, definiując nawiasy klamrowe, które mają być dopasowane, a następnie dodając tag znacznika tekstu do pasujących nawiasów klamrowych, gdy karetka jest w jednym z nawiasów klamrowych. Można zdefiniować nawiasy klamrowe w kontekście języka lub zdefiniować własne rozszerzenie nazwy pliku i typ zawartości oraz zastosować Tagi tylko do tego typu lub można zastosować znaczniki do istniejącego typu zawartości (na przykład "tekst"). W poniższym przewodniku pokazano, jak zastosować nawiasy klamrowe do typu zawartości "text".  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1. Utwórz projekt klasyfikatora edytora. Nadaj nazwę rozwiązanie `BraceMatchingTest` .  
  
2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Usuń istniejące pliki klas.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementowanie dopasowywania moduł tagujący w nawiasach klamrowych  
 Aby uzyskać efekt wyróżniania nawiasów klamrowych, który jest podobny do tego, który jest używany w programie Visual Studio, można zaimplementować moduł tagujący typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Poniższy kod ilustruje sposób definiowania moduł tagujący dla par nawiasów klamrowych na dowolnym poziomie zagnieżdżenia. W tym przykładzie pary nawiasów klamrowych []. [], i {} są zdefiniowane w konstruktorze moduł tagujący, ale w pełnej implementacji języka w specyfikacji języka należy zdefiniować odpowiednie pary nawiasów klamrowych.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Aby zaimplementować moduł tagujący pasujący do nawiasu klamrowego  
  
1. Dodaj plik klasy i nadaj mu nazwę BraceMatching.  
  
2. Zaimportuj następujące przestrzenie nazw.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3. Zdefiniuj klasę `BraceMatchingTagger` , która dziedziczy po <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typie <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4. Dodaj właściwości widoku tekstu, buforu źródłowego i bieżącego punktu migawki, a także zestawu par nawiasów klamrowych.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5. W konstruktorze moduł tagujący ustaw właściwości i Zasubskrybuj widok zmiany zdarzeń <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . W tym przykładzie, w celu zilustrowania, zgodne pary są również zdefiniowane w konstruktorze.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6. W ramach <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementacji Zadeklaruj zdarzenie TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7. Programy obsługi zdarzeń aktualizują bieżącą pozycję karetki do `CurrentChar` właściwości i generują zdarzenie TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, aby dopasować nawiasy klamrowe, gdy bieżący znak jest otwartym nawiasem klamrowym lub kiedy poprzedni znak jest zamykanym nawiasem klamrowym, jak w programie Visual Studio. Po znalezieniu dopasowania ta metoda tworzy wystąpienie dwóch tagów, po jednym dla otwierającego nawiasu klamrowego i jeden dla zamykającego nawiasu klamrowego.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Poniższe metody prywatne Znajdź pasujący nawias klamrowy na dowolnym poziomie zagnieżdżenia. Pierwsza metoda umożliwia znalezienie znaku zamykającego, który pasuje do otwartego znaku:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Poniższa metoda pomocnika umożliwia znalezienie otwartego znaku, który pasuje do znaku zamykającego:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementacja dostawcy moduł tagujący pasującego do nawiasu klamrowego  
 Oprócz wdrożenia moduł tagujący, należy również zaimplementować i wyeksportować dostawcę moduł tagujący. W takim przypadku typem zawartości dostawcy jest "text". Oznacza to, że dopasowywanie nawiasów klamrowych będzie wyświetlane we wszystkich typach plików tekstowych, ale w celu zastosowania większej implementacji tylko do określonego typu zawartości zostanie zastosowane przenawiasy klamrowe.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Aby zaimplementować dostawcę moduł tagujący zgodny z nawiasem klamrowym  
  
1. Zadeklaruj dostawcę moduł tagujący, który dziedziczy po <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , nadaj mu nazwę BraceMatchingTaggerProvider i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodę, aby utworzyć wystąpienie BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Kompilowanie i testowanie kodu  
 Aby przetestować ten kod, skompiluj rozwiązanie BraceMatchingTest i uruchom je w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Aby skompilować i przetestować rozwiązanie BraceMatchingTest  
  
1. Skompiluj rozwiązanie.  
  
2. Po uruchomieniu tego projektu w debugerze tworzone jest drugie wystąpienie programu Visual Studio.  
  
3. Utwórz plik tekstowy i wpisz tekst, który zawiera pasujące nawiasy klamrowe.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4. Gdy umieszczasz karetkę przed otwierającym nawiasem klamrowym, należy podróżnić zarówno ten nawias klamrowy, jak i pasujący nawias zamykający. Po umieszczeniu kursora tuż po zamykającym nawiasie klamrowym, należy podróżnić zarówno ten nawias klamrowy, jak i pasujący otwierający nawias klamrowy.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
