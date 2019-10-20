---
title: 'Przykładowe rozszerzenie programu Excel: Klasa TechnologyManager | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac9a4517fcf13dbb0e1d7a6f994092168723e660
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672149"
---
# <a name="sample-excel-extension-technologymanager-class"></a>Przykładowe rozszerzenie programu Excel: klasa TechnologyManager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta Klasa rozszerza klasę <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> i jest odpowiedzialna za dostarczanie podstawowych usług dla rozszerzenia [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Chociaż Klasa bazowa ma wiele metod, w tym przykładzie używany jest tylko podzestaw z nich.

 Niektóre metody po prostu zwracają wartość właściwości. Wiele metod pozwala deweloperom przesłaniać domyślne algorytmy kompilacji do aparatu kodowanego testu interfejsu użytkownika. Te metody zwracają <xref:System.NotSupportedException> lub zwraca `null`, co informuje platformę, aby używała algorytmu domyślnego.

 W zależności od złożoności podstawowej technologii opracowywanie kodu Menedżera technologii może potrwać od kilku tygodni do kilku miesięcy. Program Excel umożliwia utworzenie potencjalnie bardzo obszernego Menedżera technologii. Ten przykład jest celowo ograniczony do arkuszy programu Excel i komórek i używa ograniczonego formatowania.

 Gdy jest to możliwe, kod Menedżera technologii używa kanału komunikacji zdalnej .NET otwartego przez klasę `Communicator`, aby wyodrębnić informacje z dodatku działającego w procesie programu Excel.

## <a name="com-visibility"></a>Widoczność COM
 Należy zauważyć, że ta klasa i każda Klasa elementu rozszerzająca klasę <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> wszystkie mają <xref:System.Runtime.InteropServices.ComVisibleAttribute> z wartością `true`, aby upewnić się, że klasy są widoczne dla modelu COM.

## <a name="technologyname-property"></a>TechnologyName — Właściwość
 To przesłonięcie właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> musi zapewnić unikatową i zrozumiałą nazwę, która identyfikuje podstawową technologię dla każdego innego składnika rozszerzenia. Dla tego rozszerzenia wartością jest "Excel".

## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel, Metoda
 To przesłonięcie metody <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> zwraca liczbę wskazującą poziom wsparcia, który Menedżer technologii może zaoferować dla formantu reprezentowanego przez podane dojście. Im wyższa wartość zwracana, tym bardziej Menedżer technologii może obsługiwać formant. W takim przypadku metoda sprawdza okno, które zawiera kontrolkę i jeśli jest to arkusz programu Excel, metoda zwraca najwyższą wartość; w przeciwnym razie zwraca zero, co oznacza, że nie jest dostępna żadna pomoc techniczna.

## <a name="methods-to-get-an-element"></a>Metody uzyskiwania elementu
 Istnieje kilka istotnych metod, które są używane przez strukturę testowania kodowanego interfejsu użytkownika w celu uzyskania elementu specyficznego dla technologii przez udostępnienie dojścia, punktu na ekranie lub elementu z innej technologii. Kod dla tych metod nie wymaga wyjaśnień. Metody podstawowe są następujące:

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>

## <a name="parsequeryid-method"></a>ParseQueryId, Metoda
 Po utworzeniu kodowanego testu interfejsu użytkownika użytkownik może określić wartości właściwości dla niektórych lub wszystkich kontrolek w teście. Te wartości właściwości są używane przez platformę testowania do tworzenia par nazwa-wartość o nazwie Wyszukaj właściwości, które są używane do znajdowania określonych kontrolek interfejsu użytkownika podczas testu. Wszystkie właściwości wyszukiwania razem reprezentują wartość właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> każdego elementu w technologii, która obejmuje każdy formant. Ponieważ kontrolka może wymagać znalezienia kilku razy w trakcie testu, ta metoda zapewnia menedżerowi technologii możliwość zoptymalizowania analizy właściwości wyszukiwania dla danego formantu. Ta metoda zwraca również plik cookie, który może być używany przez platformę do kolejnych wyszukiwań dla tej kontrolki. Ta implementacja metody używa metody <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>, aby przeanalizować właściwości wyszukiwania.

## <a name="matchelement-method"></a>MatchElement — Metoda
 Aby przeprowadzić wyszukiwanie kontrolki przez Menedżera technologii, można zaimplementować metodę <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName>, aby zwracała tablicę możliwych dopasowań lub zgłosić <xref:System.NotSupportedException>, co informuje platformę o użyciu własnego algorytmu wyszukiwania. W obu przypadkach należy zaimplementować metodę <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A>, w której ta implementacja ponownie używa metody <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.

## <a name="navigation-methods"></a>Metody nawigacji
 Te metody uzyskują elementy nadrzędne, podrzędne lub równorzędne podanego elementu z hierarchii interfejsu użytkownika. Kod jest prosty i jasno z komentarzem.

## <a name="getexcelelement-internal-method"></a>Metoda wewnętrzna metody GetExcelElement
 Ta metoda wewnętrzna przyjmuje uchwyt okna i informacje o elemencie programu Excel i zwraca żądany element programu Excel.

## <a name="see-also"></a>Zobacz też
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager><xref:System.NotSupportedException>
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
