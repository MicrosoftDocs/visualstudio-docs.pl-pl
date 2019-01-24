---
title: 'Przykładowe rozszerzenie programu Excel: Klasa TechnologyManager | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 11
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4ab353f9c42eebe4af10f56f6ee4cda533069121
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779573"
---
# <a name="sample-excel-extension-technologymanager-class"></a>Przykładowe rozszerzenie programu Excel: TechnologyManager — Klasa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta klasa rozszerza <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> klasy i jest odpowiedzialny za dostarczającego usługi podstawowe dla [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] rozszerzenia. Chociaż klasa bazowa ma wiele metod, tylko część z nich jest używana w tym przykładzie.  
  
 Niektóre metody po prostu zwraca wartość właściwości. Wiele metod są przeznaczone do umożliwiania dla deweloperów zastąpić ustawienie domyślne, które algorytmy rozbudowuj aparat kodowanych testów interfejsu użytkownika. Te metody throw <xref:System.NotSupportedException> lub je zwracają `null`, informuje platformę, by używać algorytmu domyślne.  
  
 W zależności od złożoności podstawową używaną technologią tworzenia kodu manager technologia może potrwać od kilku tygodni do kilku miesięcy. Program Excel oferuje możliwość utworzenia potencjalnie bardzo rozbudowane technologii menedżera. W tym przykładzie jest celowo ograniczona do arkusza programu Excel i komórek i korzysta z ograniczoną formatowania.  
  
 Gdy jest to możliwe, kod Menedżera technologii korzysta z wywołaniem funkcji zdalnych .NET kanał otwarty przez `Communicator` klasy w celu wyodrębnienia informacji z dodatku działający w procesie programu Excel.  
  
## <a name="com-visibility"></a>Widoczność COM  
 Zwróć uwagę, że tej klasy, a każdy element klas rozszerzyć <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> klasy wszystkie mają <xref:System.Runtime.InteropServices.ComVisibleAttribute> o wartości `true` się upewnić, że klasy są widoczne dla modelu COM.  
  
## <a name="technologyname-property"></a>TechnologyName Property  
 To zastąpienie elementu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> właściwości należy podać unikatową i opisową nazwę, która określa podstawową używaną technologią dla każdego składnika, rozszerzenia. Dla tego rozszerzenia wartość to "Programu Excel".  
  
## <a name="getcontrolsupportlevel-method"></a>Metoda GetControlSupportLevel  
 To zastąpienie elementu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> metoda zwraca numer, który wskazuje poziom obsługi udostępniające przez Menedżera technologii dla kontrolki, reprezentowane przez podane dojście. Im większa wartość zwrócona więcej technologii manager może obsługiwać formant. W tym przypadku metoda sprawdza okna, który zawiera kontrolkę, a jeśli arkusza programu Excel, metoda zwraca najwyższą wartość; w przeciwnym razie zwraca zero, co oznacza, że nie jest obsługiwana.  
  
## <a name="methods-to-get-an-element"></a>Metody w celu uzyskania elementu  
 Dostępnych jest kilka ważnych metod, które są używane przez kodowanych testów interfejsu użytkownika można pobrać elementu specyficzne dla technologii, zapewniając uchwyt punkcie ekran lub element z różnych technologii. Kod dla tych metod nie wymaga wyjaśnień. Metod bazowych są następujące:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>Metoda ParseQueryId  
 Po utworzeniu kodowanego testu interfejsu użytkownika, użytkownik może określić wartości właściwości dla niektórych lub wszystkich kontrolek w teście. Wartości tych właściwości są używane przez strukturę testów do tworzenia pary nazwa wartość o nazwie właściwości wyszukiwania, które służą do znajdowania określonych kontrolek interfejsu użytkownika podczas testu. Właściwości wyszukiwania razem reprezentowanie wartości <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> właściwości każdego elementu w technologii, która zawiera każdy formant. Ponieważ formant może być konieczne można znaleźć kilka razy podczas testu, ta metoda zapewnia Menedżer technologii sposób na optymalizację analizowania właściwości wyszukiwania dla danej kontrolki. Ta metoda zwraca też wartość pliku cookie używanego przez platformę do kolejnych wyszukiwania dla tej kontrolki. Ta implementacja metody używa <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> metodę, aby przeanalizować właściwości wyszukiwania.  
  
## <a name="matchelement-method"></a>Metoda MatchElement  
 Aby wykonać wyszukiwanie sterowania przez Menedżera technologii, można zaimplementować <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> metodę, aby zwracało tablicę możliwych dopasowań lub zgłosić <xref:System.NotSupportedException>, informuje platformę, by używać własnej algorytmu wyszukiwania. W obu przypadkach należy zaimplementować <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> metody, których używa się tej implementacji ponownie <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> metody.  
  
## <a name="navigation-methods"></a>Metody nawigacji  
 Te metody nadrzędnego, elementy podrzędne lub elementów równorzędnych podany element uzyskiwanie hierarchii interfejsu użytkownika. Kod jest proste i wyraźnie komentarzem.  
  
## <a name="getexcelelement-internal-method"></a>Metoda wewnętrzna GetExcelElement  
 Ta metoda wewnętrznego przyjmuje uchwyt okna i informacje o elemencie programu Excel i zwraca żądany element w programie Excel.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
