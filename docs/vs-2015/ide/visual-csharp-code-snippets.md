---
title: Fragmenty kodu Visual C# | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4655ea7160d353fc8735a9025f36de368f247ba8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698182"
---
# <a name="visual-c-code-snippets"></a>Wstawki kodu Visual C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kodu są gotowe fragmenty kodu, które szybko można wstawić w kodzie. Na przykład `for` fragment kodu tworzy pustą `for` pętli. Niektóre fragmenty kodu pochodzą z funkcji Otocz przez fragmenty kodu, które umożliwia wybór wierszy kodu, a następnie wybierz fragment kodu, która obejmuje też dokument wybranych wierszy kodu. Na przykład kiedy wybierz linii kodu i przy następnie uaktywnić `for` fragment kodu tworzy `for` pętli za pomocą tych wierszy kodu wewnątrz bloku pętli. Fragmenty kodu ułatwia pisanie program code szybsze, prostsze i bardziej niezawodne.  
  
 Wstaw fragment kodu w lokalizacji kursora lub Wstaw Otocz przez fragment kodu wokół zaznaczonego kodu. Wstawek kodu jest wywoływana za pomocą **Wstaw fragment kodu** lub **Otocz** polecenia na **IntelliSense** menu lub za pomocą skrótów klawiaturowych CTRL + K następnie X lub CTRL + K i następnie S odpowiednio.  
  
 Wstawek kodu wyświetla wszystkie dostępne wstawki programu nazwę fragmentu kodu. Wstawianie wstawek kodu obejmuje również okno dialogowe danych wejściowych, w którym możesz wpisać nazwę fragmentu kodu lub część nazwy fragmentu kodu. Wstawianie wstawek kodu wyróżnia najlepiej dopasowany do nazwy fragmentu kodu. Klawisza TAB w dowolnym momencie zamknąć wstawek kodu i Wstaw fragment kodu aktualnie wybrany. Wpisując ESC albo klikając przycisk myszy w edytorze kodu będą odrzucać wstawek kodu bez wstawiania fragmentu kodu.  
  
## <a name="default-code-snippets"></a>Fragmenty kodu domyślnego  
 Domyślnie następujące fragmenty kodu są uwzględnione w programie Visual Studio.  
  
|Nazwa (lub skrót)|Opis|Prawidłowe lokalizacje, aby wstawić fragment kodu|  
|--------------------------|-----------------|---------------------------------------|  
|#if|Tworzy [#if](https://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2) dyrektywy i [#endif](https://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05) dyrektywy.|W dowolnym miejscu.|  
|#region|Tworzy [#region](https://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4) dyrektywy i [#endregion](https://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526) dyrektywy.|W dowolnym miejscu.|  
|~|Tworzy destruktor klasy zawierającej.|Wewnątrz klasy.|  
|— atrybut|Tworzy oświadczenie dla klasy, która pochodzi od klasy <xref:System.Attribute>.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|  
|checked|Tworzy [zaznaczone](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|class|Tworzy deklaracji klasy.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|  
|ctor|Tworzy konstruktora dla klasy zawierającej.|Wewnątrz klasy.|  
|cw|Tworzy wywołanie <xref:System.Console.WriteLine%2A>.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|do|Tworzy [czy](https://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb) `while` pętli.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|else|Tworzy [else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|enum|Tworzy [wyliczenia](https://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c) deklaracji.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|  
|equals|Tworzy deklaracji metody, która zastępuje <xref:System.Object.Equals%2A> metody zdefiniowanej w <xref:System.Object> klasy.|Wewnątrz klasy lub struktury.|  
|wyjątek|Tworzy oświadczenie dla klasy, która wynika z wyjątku (<xref:System.Exception> domyślnie).|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|  
|dla|Tworzy [dla](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) pętli.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|foreach|Tworzy [foreach](https://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec) pętli.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|lepiej wykorzystać możliwości|Tworzy [dla](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) pętli tego zmniejsza zmienna pętli po każdej iteracji.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|if|Tworzy [Jeśli](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|Indeksator|Tworzy deklaracji indeksatora.|Wewnątrz klasy lub struktury.|  
|interface|Tworzy [interfejsu](https://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) deklaracji.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|  
|wywołania|Tworzy blok, który bezpiecznie wywołuje zdarzenie.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|iterator|Tworzy iterator.|Wewnątrz klasy lub struktury.|  
|iterindex|Tworzy "o nazwie" pary iteratora i indeksatora przy użyciu klasy zagnieżdżonej.|Wewnątrz klasy lub struktury.|  
|lock|Tworzy [blokady](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|mbox|Tworzy wywołanie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Może trzeba dodać odwołanie do pliku System.Windows.Forms.dll.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|— przestrzeń nazw|Tworzy [przestrzeni nazw](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) deklaracji.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw).|  
|Prop|Tworzy [automatycznie implementowana właściwość](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) deklaracji.|Wewnątrz klasy lub struktury.|  
|propfull|Tworzy deklaracja właściwości get i ustaw metody dostępu.|Wewnątrz klasy lub struktury.|  
|propg|Tworzy tylko do odczytu [automatycznie implementowana właściwość](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) za pomocą prywatnej metody dostępu "set".|Wewnątrz klasy lub struktury.|  
|SIM|Tworzy [statyczne](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[int](https://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52) deklaracji metody Main.|Wewnątrz klasy lub struktury.|  
|struktura |Tworzy [struktury](https://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c) deklaracji.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|  
|svm|Tworzy [statyczne](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[void](https://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4) deklaracji metody Main.|Wewnątrz klasy lub struktury.|  
|— przełącznik|Tworzy [Przełącz](https://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|Wypróbuj|Tworzy [try-catch —](https://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|tryf|Tworzy [try-finally](https://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|unchecked|Tworzy [unchecked](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|unsafe|Tworzy [niebezpieczne](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) bloku.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
|korzystanie|Tworzy [przy użyciu](https://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8) dyrektywy.|Wewnątrz przestrzeni nazw (w tym globalnej przestrzeni nazw).|  
|while|Tworzy [podczas](https://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59) pętli.|Wewnątrz metody, indeksatora, metody dostępu właściwości lub metody dostępu zdarzeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wstawek kodu](../ide/code-snippet-functions.md)   
 [Fragmenty kodu](../ide/code-snippets.md)   
 [Instrukcje: Tworzenie nowego fragmentu kodu przy użyciu zamiany](https://msdn.microsoft.com/8d56d43c-097a-475b-aa85-cae1554b6338)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Instrukcje: Użycie fragmentów kodu polecenia Otocz przez](../ide/how-to-use-surround-with-code-snippets.md)   
 [Instrukcje: Przywracanie refaktoryzowanych fragmentów kodu C#](../ide/how-to-restore-csharp-refactoring-snippets.md)
