---
title: 'CA2119: Pieczętuj metody, które spełniają wymagania interfejsów prywatnych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4c019e98e7f1311b6521dff563cb8e7bb0a2356e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62544025"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Pieczętuj metody, które spełniają wymagania interfejsów prywatnych

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Dziedziczny typ publiczny dostarcza zastępowalną implementację metody `internal` (`Friend` w języku Visual Basic) interfejsu.

## <a name="rule-description"></a>Opis reguły
 Metody interfejsu muszą powszechnej dostępności, której nie można zmienić w typie implementującym. Interfejs wewnętrzny tworzy kontraktu, który nie jest przeznaczony do implementacji spoza zestawu, który definiuje interfejs. Publiczny typ, który implementuje metodę interfejsu wewnętrznego przy użyciu `virtual` (`Overridable` w języku Visual Basic) modyfikator umożliwia metody do zastąpienia przez typ pochodny, który znajduje się poza zestaw. Jeśli drugi typ w zestawie definiujące wywołuje metodę i oczekuje, że kontrakt wyłącznie wewnętrznym, zachowanie jest zagrożona podczas zamiast tego przesłonięte metody w zestawie poza jest wykonywany. Spowoduje to utworzenie luki w zabezpieczeniach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zapobiegania metody zastępowaniu spoza zestawu przy użyciu jednej z następujących czynności:

- Zmień typ deklarujący `sealed` (`NotInheritable` w języku Visual Basic).

- Zmień dostępność elementu typ deklarujący `internal` (`Friend` w języku Visual Basic).

- Usuń wszystkich konstruktorów publicznych z typ deklarujący.

- Implementuje metody bez używania `virtual` modyfikator.

- Jawnie implementować metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Bezpiecznie ostrzeżenia z tej reguły, jeśli po dokładnej przeglądu żadnych problemów z zabezpieczeniami istnieją, które może być możliwe, jeśli metoda zostanie przesłonięta spoza zestawu.

## <a name="example-1"></a>Przykład 1
 W poniższym przykładzie pokazano typu `BaseImplementation`, który narusza tę regułę.

 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>Przykład 2
 Poniższy przykład wykorzystuje metodę wirtualną wykonania poprzedniego przykładu.

 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>Zobacz także

- [Interfejsy](/dotnet/csharp/programming-guide/interfaces/index)
- [Interfejsy](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)