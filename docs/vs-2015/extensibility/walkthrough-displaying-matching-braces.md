---
title: 'Przewodnik: Wyświetlanie, dopasowywanie nawiasów klamrowych | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084937"
---
# <a name="walkthrough-displaying-matching-braces"></a>Przewodnik: Wyświetlanie parowanych nawiasów klamrowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz zaimplementować opartych na języku funkcje, takie jak parowanie nawiasów klamrowych przez definiowanie nawiasy klamrowe, które chcesz dopasować, a następnie dodanie tagu znacznika tekstu do pasujące nawiasy klamrowe, gdy karetka znajduje się na jednym z nawiasami klamrowymi. Można zdefiniować nawiasy klamrowe w kontekście języka, można zdefiniować własny plik Nazwa rozszerzenia i zawartości typ i zastosować znaczniki do właśnie tego typu lub można zastosować znaczniki do istniejącego typu zawartości (na przykład "text"). Następujące instruktaż przedstawia sposób zastosowania parowanie nawiasów klamrowych tagów, aby typ zawartości "text".  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Framework (MEF) zarządzanych rozszerzeń  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1. Utwórz projekt Klasifikace edytora. Nazwij rozwiązanie `BraceMatchingTest`.  
  
2. Dodaj szablon elementu edytora klasyfikatora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Usuń istniejące pliki klasy.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementowanie dopasowania moduł Tagujący nawiasu klamrowego  
 Aby uzyskać nawiasu klamrowego wyróżnianie efekt, który przypomina ten, który jest używany w programie Visual Studio, można zaimplementować moduł tagujący typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Poniższy kod przedstawia sposób definiowania moduł tagujący dla par nawiasu klamrowego na każdym poziomie zagnieżdżania. W tym przykładzie [] pary nawiasów. [], a {} są zdefiniowane w Konstruktorze moduł tagujący, ale w implementacji pełną obsługą języka pary nawiasów odpowiednie zostaną zdefiniowane w specyfikacji języka.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Aby zaimplementować dopasowania moduł tagujący nawiasu klamrowego  
  
1. Dodaj plik klasy i nadaj mu nazwę BraceMatching.  
  
2. Zaimportuj następujące przestrzenie nazw.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3. Zdefiniuj klasę `BraceMatchingTagger` tej, która dziedziczy <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4. Dodaj właściwości widoku tekstu, bufor źródłowy a bieżącym punkcie migawki, a także zestaw par nawiasu klamrowego.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5. W Konstruktorze moduł tagujący Ustaw właściwości i subskrybowanie zdarzeń zmiany widoku <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. W tym przykładzie w celach ilustracyjnych, pasujących par są także definiowane w konstruktorze.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6. Jako część <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementacji zadeklarować zdarzenia TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7. Programy obsługi zdarzeń aktualizacji w bieżącym położeniu karetki `CurrentChar` właściwość i zgłoś zdarzenie TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8. Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodę, aby dopasować nawiasy klamrowe albo gdy bieżący znak jest otwierający nawias klamrowy, lub gdy poprzedni znak jest bliskie nawiasu klamrowego, tak jak w programie Visual Studio. Gdy zostanie znalezione dopasowanie, ta metoda tworzy dwa tagi: jeden dla otwierający nawias klamrowy, a drugi dla Zamknij nawiasu klamrowego.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Następujące metody prywatne znaleźć pasujący nawias klamrowy na każdym poziomie zagnieżdżania. Pierwsza metoda umożliwia znalezienie Zamknij znak, który pasuje do znaku Otwórz:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Następującą metodę pomocnika umożliwia znalezienie Otwórz znak, który pasuje do znaku Zamknij:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementowanie nawias klamrowy dopasowania moduł Tagujący dostawcy  
 Oprócz wykonywania moduł tagujący, można także wdrożyć i eksportować dostawcy moduł tagujący. W takim przypadku zawartości typ dostawcy jest "text". Oznacza to, że parowanie nawiasów klamrowych pojawi się na wszystkich typów plików tekstowych, ale pełniejszego implementacji naliczona zostałaby parowanie nawiasów klamrowych tylko do określonego typu zawartości.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Do implementowania dostawcy moduł tagujący pasującego nawiasu klamrowego  
  
1. Zadeklaruj dostawcy moduł tagujący, która dziedziczy <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, a następnie nadaj mu nazwę BraceMatchingTaggerProvider i wyeksportować je za pomocą <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2. Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodę, aby utworzyć wystąpienie BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Aby przetestować ten kod, Kompiluj rozwiązanie BraceMatchingTest, a następnie uruchomić go w doświadczalnym wystąpieniu.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Aby skompilować i przetestować rozwiązanie BraceMatchingTest  
  
1. Skompiluj rozwiązanie.  
  
2. Po uruchomieniu tego projektu w debugerze drugiego wystąpienia programu Visual Studio jest uruchomiony.  
  
3. Utwórz plik tekstowy, a następnie wpisz dowolny tekst, który zawiera pasujące nawiasy klamrowe.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4. Po umieszczeniu karetki przed otwierający nawias klamrowy, powinien być wyróżniony tego nawiasów i zamknij nawiasów. Gdy umieścisz kursor zaraz po Zamknij nawias klamrowy, powinien być wyróżniony tego nawiasów i otwierający nawias klamrowy dopasowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
