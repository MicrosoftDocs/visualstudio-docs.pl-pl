---
title: MSTest assert klasy i metody
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c36916c79bd783ed2c6ce960b068e85478b9971d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592051"
---
# <a name="use-assert-classes-for-unit-testing"></a>Użyj assert klas do testowania jednostkowego

Użyj Assert klasy <xref:Microsoft.VisualStudio.TestTools.UnitTesting> obszaru nazw, aby zweryfikować określone funkcje. Metoda testu jednostkowego wykonuje kod metody w kodzie aplikacji, ale raportuje poprawność zachowania kodu tylko wtedy, gdy dodasz Assert instrukcji.

## <a name="kinds-of-asserts"></a>Rodzaje aserdów

Obszar <xref:Microsoft.VisualStudio.TestTools.UnitTesting> nazw zawiera kilka rodzajów Assert klasy.

W metodzie testowej można wywołać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> dowolne <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>metody klasy, takie jak . Klasa <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> ma wiele metod do wyboru, a wiele metod ma kilka przeciążeń.

### <a name="compare-strings-and-collections"></a>Porównywanie ciągów i kolekcji

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> Klasa służy do porównywania kolekcji obiektów lub do weryfikacji stanu kolekcji.

Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> klasy, aby porównać i zbadać ciągi. Ta klasa zawiera wiele przydatnych metod, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType>takich <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>jak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, i .

### <a name="exceptions"></a>Wyjątki

Wyjątek <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> jest zgłaszany, gdy test zakończy się niepowodzeniem. Test kończy się niepowodzeniem, jeśli upłynie czas, zgłasza nieoczekiwany wyjątek lub zawiera instrukcję assert, która daje wynik **failed.**

Jest <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> wyrzucany, gdy test daje wynik **Niejednoznaczne**. Zazwyczaj można dodać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> instrukcję do testu, który nadal pracujesz, aby wskazać, że nie jest jeszcze gotowy do uruchomienia.

> [!NOTE]
> Alternatywną strategią jest oznaczenie testu, który <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> nie jest gotowy do uruchomienia z atrybutem. Jednak ma to wadę, że nie można łatwo wygenerować raport na temat liczby testów, które nie są implementowane.

Jeśli piszesz nową klasę wyjątku assert, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> dziedziczyj z klasy podstawowej, aby ułatwić identyfikowanie wyjątku jako błąd potwierdzenia zamiast nieoczekiwanego wyjątku zgłaszanego z kodu testowego lub produkcyjnego.

Aby sprawdzić, czy wyjątek, który ma zostać zgłoszony przez metodę <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> w kodzie aplikacji jest faktycznie zgłaszany, należy użyć metody.

## <a name="see-also"></a>Zobacz też

- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)
