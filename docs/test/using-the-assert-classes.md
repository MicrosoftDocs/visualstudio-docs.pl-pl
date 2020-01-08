---
title: Klasy i metody potwierdzeń MSTest
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592051"
---
# <a name="use-assert-classes-for-unit-testing"></a>Korzystanie z klas potwierdzeń do testowania jednostek

Użyj klas potwierdzeń przestrzeni nazw <xref:Microsoft.VisualStudio.TestTools.UnitTesting>, aby zweryfikować konkretne funkcje. Metoda testowania jednostkowego wykonuje kod metody w kodzie aplikacji, ale raportuje poprawność zachowania kodu tylko wtedy, gdy zawiera instrukcje Assert.

## <a name="kinds-of-asserts"></a>Rodzaje potwierdzeń

Przestrzeń nazw <xref:Microsoft.VisualStudio.TestTools.UnitTesting> zawiera kilka rodzajów klas potwierdzeń.

W metodzie testowej można wywołać wszystkie metody klasy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>, takie jak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>. Klasa <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> ma wiele metod do wyboru, a wiele metod ma kilka przeciążeń.

### <a name="compare-strings-and-collections"></a>Porównanie ciągów i kolekcji

Użyj klasy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>, aby porównać kolekcje obiektów lub sprawdzić stan kolekcji.

Użyj klasy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>, aby porównać i przeanalizować ciągi. Ta klasa zawiera różne użyteczne metody, takie jak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType>i <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Wyjątki

Wyjątek <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> jest zgłaszany za każdym razem, gdy test zakończy się niepowodzeniem. Test kończy się niepowodzeniem, jeśli przekroczy limit czasu, wygeneruje nieoczekiwany wyjątek lub zawiera instrukcję assert, która powoduje **niepowodzenie**.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> jest zgłaszany za każdym razem, gdy test da wynik **niejednoznaczny**. Zazwyczaj należy dodać instrukcję <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> do testu, nad którym pracujesz, aby wskazać, że nie jest jeszcze gotowy do uruchomienia.

> [!NOTE]
> Alternatywną strategią jest oznaczenie testu, który nie jest gotowy do uruchomienia z atrybutem <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>. Jednak jest to wadą, że nie można łatwo wygenerować raportu na liczbę testów, które nie zostały zaimplementowane.

Jeśli piszesz nową klasę wyjątku potwierdzenia, Dziedzicz z klasy bazowej <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>, aby ułatwić zidentyfikowanie wyjątku jako nieoczekiwanego wyjątku, a nie zgłoszono błędu z kodu testowego lub produkcyjnego.

Aby sprawdzić, czy wyjątek, który powinien być zgłoszony przez metodę w kodzie aplikacji, jest faktycznie zgłaszany, użyj metody <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz także

- [Kod testu jednostkowego](../test/unit-test-your-code.md)
