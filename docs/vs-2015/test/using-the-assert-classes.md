---
title: Korzystanie z klas potwierdzeń | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 29
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 338a18bb48c20c20fa1f89583ed0d4af84c99d5e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408394"
---
# <a name="using-the-assert-classes"></a>Korzystanie z klas potwierdzeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby sprawdzić określonych funkcji, należy użyć klas potwierdzeń UnitTestingFramework przestrzeni nazw. Metodę testu jednostkowego wykonuje kod do metody w kodzie rozwoju, ale raporty poprawność zachowania kodu, tylko wtedy, gdy zawierają Assert-instrukcje.  
  
## <a name="kinds-of-asserts"></a>Rodzaje z asercji  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Przestrzeń nazw zawiera kilka rodzajów klas potwierdzeń:  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 W metodzie testowej można wywołać dowolną liczbę metod klasy potwierdzeń, takich jak Assert.AreEqual(). Klasy potwierdzeń ma wiele metod do wyboru, a wiele z tych metod ma kilka przeciążeń.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 Porównywanie kolekcji obiektów i zweryfikuj stan co najmniej jednej kolekcji, należy użyć klasy funkcji CollectionAssert.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 Klasa StringAssert służy do porównywania ciągów. Ta klasa zawiera różne przydatne metody takie jak StringAssert.Contains, StringAssert.Matches i StringAssert.StartsWith.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 Zawsze wtedy, gdy test zakończy się niepowodzeniem, jest zgłaszany wyjątek AssertFailedException. Test zakończy się niepowodzeniem, jeśli upłynie limit czasu, nieoczekiwany wyjątek lub zawiera instrukcję Assert, który daje wynik nie powiodło się.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 AssertInconclusiveException jest generowany, gdy testu wygeneruje wynik w postaci niejednoznaczny. Zazwyczaj dodajesz instrukcję Assert.Inconclusive do testu, która nadal jest wykonywane w celu wskazania, że nie jest jeszcze gotowy do uruchomienia.  
  
> [!NOTE]
> Strategia alternatywna byłoby oznaczyć test, który nie jest gotowy do uruchomienia z atrybutem ignorowania. Ma to jednak wadą, który nie może łatwo wygenerować raport liczby testów, że pozostało do zaimplementowania.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 Jeśli piszesz nową klasę wyjątków Assert, posiadanie tej klasy, które dziedziczą z klasy bazowej UnitTestAssertException sprawia, że łatwiej zidentyfikować wyjątku, ponieważ wystąpił błąd asercji zamiast nieoczekiwany wyjątek zgłaszany w kodzie testowym lub produkcyjnym.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 Dekoracji metodę testową z atrybutem ExpectedExceptionAttribute, jeśli chcesz, aby metody testowej, aby sprawdzić, czy oczekiwanych wyrzucone przez metodę w kodzie rozwoju jest rzeczywiście jest wyjątek w tej metodzie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [Tworzenie i Uruchamianie testów jednostkowych dla istniejącego kodu](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
