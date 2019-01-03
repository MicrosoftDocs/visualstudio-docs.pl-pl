---
title: MSTest assert klasy i metody
ms.date: 06/07/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8e6dcd374426cc8f5e7fd218ac33e570f1ef57dc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989519"
---
# <a name="use-assert-classes-for-unit-testing"></a>Użyj klas potwierdzeń testów jednostkowych

Korzystanie z klas potwierdzeń z <xref:Microsoft.VisualStudio.TestTools.UnitTesting> przestrzeni nazw w celu sprawdzenia określonych funkcji. Metodę testu jednostkowego wykonuje kod do metody w kodzie twojej aplikacji, ale raporty poprawność zachowania kodu, tylko wtedy, gdy zawierają Assert-instrukcje.

## <a name="kinds-of-asserts"></a>Rodzaje z asercji

<xref:Microsoft.VisualStudio.TestTools.UnitTesting> Przestrzeń nazw zawiera kilka rodzajów klas potwierdzeń.

W metodzie testowej, można wywołać dowolnej metody <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> klasy, takie jak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> Klasa ma wiele metod do wyboru, a wiele metod ma kilka przeciążeń.

### <a name="compare-strings-and-collections"></a>Porównanie ciągów i zbiorów

Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> klasy, aby porównać kolekcje obiektów lub aby zweryfikować stan kolekcji.

Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> klasy do porównywania i zbadać ciągów. Ta klasa zawiera różne przydatne metody <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType>, i <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Wyjątki

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> Wyjątek jest zgłaszany, gdy test zakończy się niepowodzeniem. Test kończy się niepowodzeniem, jeśli przekroczy limit czasu, wygeneruje nieoczekiwany wyjątek lub zawiera instrukcję assert, która powoduje **niepowodzenie**.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> Jest generowany, gdy test wygeneruje wynik w postaci **niejednoznaczny**. Zazwyczaj dodajesz <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> instrukcję, aby test, który nadal pracujesz, aby wskazać, nie jest jeszcze gotowy do uruchomienia.

> [!NOTE]
> Strategia alternatywna jest do oznaczania test, który nie jest gotowy do uruchomienia przy użyciu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> atrybutu. Ma to jednak wadą, który nie może łatwo wygenerować raport dotyczący liczby testów, które nie są implementowane.

Jeśli piszesz nowy assert klasy wyjątku, dziedziczą z klasy bazowej <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> aby ułatwić identyfikację wyjątku, ponieważ wystąpił błąd asercji zamiast nieoczekiwany wyjątek zgłaszany w kodzie testowym lub produkcyjnym.

Dekoracji metodę testową z <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atrybutu, jeśli chcesz, aby metody testowej, aby sprawdzić, czy faktycznie jest zgłaszany wyjątek oczekujesz, że będzie zgłaszany przez metodę w kodzie aplikacji.

## <a name="see-also"></a>Zobacz także

- [Kod testu jednostkowego](../test/unit-test-your-code.md)