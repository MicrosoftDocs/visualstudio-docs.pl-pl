---
title: Klasy i metody potwierdzeń MSTest
description: Dowiedz się, jak za pomocą instrukcji Assert sprawdzić poprawność działania kodu podczas testu jednostkowego kodu aplikacji.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c5401fb15a19d069c0bf454661d6d9283abb2585
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598201"
---
# <a name="use-assert-classes-for-unit-testing"></a>Korzystanie z klas potwierdzeń do testowania jednostek

Użyj klas Assert w <xref:Microsoft.VisualStudio.TestTools.UnitTesting> przestrzeni nazw, aby zweryfikować konkretne funkcje. Metoda testowania jednostkowego wykonuje kod metody w kodzie aplikacji, ale raportuje poprawność zachowania kodu tylko wtedy, gdy zawiera instrukcje Assert.

## <a name="kinds-of-asserts"></a>Rodzaje potwierdzeń

<xref:Microsoft.VisualStudio.TestTools.UnitTesting>Przestrzeń nazw zawiera kilka rodzajów klas potwierdzeń.

W metodzie testowej można wywołać dowolną metodę <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> klasy, na przykład <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> . <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>Klasa ma wiele metod do wyboru, a wiele metod ma kilka przeciążeń.

### <a name="compare-strings-and-collections"></a>Porównanie ciągów i kolekcji

Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> klasy, aby porównać kolekcje obiektów lub sprawdzić stan kolekcji.

Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> klasy, aby porównać i przeanalizować ciągi. Ta klasa zawiera wiele przydatnych metod, takich jak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType> , <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType> , i <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType> .

### <a name="exceptions"></a>Wyjątki

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>Wyjątek jest zgłaszany za każdym razem, gdy test zakończy się niepowodzeniem. Test kończy się niepowodzeniem, jeśli zostanie przetworzony, zgłasza nieoczekiwany wyjątek lub zawiera instrukcję Assert, która generuje wynik **Niepowodzenie** .

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>Jest zgłaszany za każdym razem, gdy test generuje wynik **niejednoznaczności**. Zazwyczaj należy dodać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> instrukcję do testu, nad którym nadal pracujesz, aby wskazać, że nie jest jeszcze gotowy do uruchomienia.

> [!NOTE]
> Alternatywną strategią jest oznaczenie testu, który nie jest gotowy do uruchomienia z <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> atrybutem. Jednak jest to wadą, że nie można łatwo wygenerować raportu na liczbę testów, które nie zostały zaimplementowane.

Jeśli piszesz nową klasę wyjątku potwierdzenia, Dziedzicz z klasy podstawowej, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> Aby ułatwić zidentyfikowanie wyjątku jako nieoczekiwanego wyjątku, a nie zgłoszono błędu z kodu testowego lub produkcyjnego.

Aby sprawdzić, czy wyjątek, który ma być zgłaszany przez metodę w kodzie aplikacji, został faktycznie wygenerowany, użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> metody.

## <a name="see-also"></a>Zobacz także

- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
