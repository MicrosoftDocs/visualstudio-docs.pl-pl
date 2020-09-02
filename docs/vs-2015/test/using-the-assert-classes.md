---
title: Korzystanie z klas potwierdzeń | Microsoft Docs
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
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d6a4f7f1631ac4bfc651f5df347db010cf47a656
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657135"
---
# <a name="using-the-assert-classes"></a>Korzystanie z klas potwierdzeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj klasy Assert w przestrzeni nazw UnitTestingFramework, aby sprawdzić określone funkcje. Metoda testowania jednostkowego wykonuje kod metody w kodzie deweloperskim, ale raportuje poprawność działania kodu tylko wtedy, gdy zawiera instrukcje Assert.

## <a name="kinds-of-asserts"></a>Rodzaje potwierdzeń
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>Przestrzeń nazw zawiera kilka rodzajów klasy Assert:

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

 W metodzie testowej można wywołać dowolną liczbę metod klasy Assert, takich jak Assert. AreEqual (). Klasa Assert ma wiele metod do wyboru, a wiele z tych metod ma kilka przeciążeń.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

 Użyj klasy CollectionAssert do porównywania kolekcji obiektów i sprawdzenia stanu co najmniej jednej kolekcji.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

 Użyj klasy StringAssert do porównywania ciągów. Ta klasa zawiera wiele przydatnych metod, takich jak StringAssert. Contains, StringAssert. dopasowań i StringAssert. StartsWith.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

 Wyjątek AssertFailedException jest zgłaszany za każdym razem, gdy test zakończy się niepowodzeniem. Test kończy się niepowodzeniem, jeśli zostanie przetworzony, zgłasza nieoczekiwany wyjątek lub zawiera instrukcję Assert, która generuje wynik niepowodzenie.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

 AssertInconclusiveException jest zgłaszany za każdym razem, gdy test generuje wynik niejednoznaczności. Zazwyczaj należy dodać instrukcję Assert. informowanie do testu, nad którym nadal pracujesz, aby wskazać, że nie jest jeszcze gotowy do uruchomienia.

> [!NOTE]
> Alternatywną strategią jest oznaczenie testu, który nie jest gotowy do uruchomienia z atrybutem Ignoruj. Jednak jest to wadą, że nie można łatwo wygenerować raportu dotyczącego liczby testów, które zostały pozostawione do zaimplementowania.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

 Jeśli piszesz nową klasę wyjątku potwierdzenia, że klasa dziedziczy z klasy bazowej UnitTestAssertException, ułatwia to zidentyfikowanie wyjątku jako nieoczekiwanego wyjątku, a nie błędu zgłoszonego przez test lub kod produkcyjny.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

 Dekorować metodę testową z atrybutem ExpectedExceptionAttribute, jeśli chcesz, aby metoda testowa mogła sprawdzić, czy wyjątek, który ma być zgłaszany przez metodę w kodzie programistycznym, jest faktycznie zgłaszany w tej metodzie.

## <a name="see-also"></a>Zobacz też
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>[Tworzenie i uruchamianie testów jednostkowych dla istniejącego kodu](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
