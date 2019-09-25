---
title: 'CA2214: Nie wywołuj w konstruktorach metod, które można przesłaniać'
ms.date: 05/29/2016
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8eb881da0a7ed243bda35079f617a314053f2d85
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231292"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Nie wywołuj w konstruktorach metod, które można przesłaniać

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Konstruktor niezapieczętowanego typu wywołuje metodę wirtualną zdefiniowaną w jej klasie.

## <a name="rule-description"></a>Opis reguły

Gdy wywoływana jest metoda wirtualna, faktyczny typ, który wykonuje metodę, nie jest wybierany do czasu wykonywania. Gdy Konstruktor wywołuje metodę wirtualną, istnieje możliwość, że Konstruktor wystąpienia, który wywołuje metodę, nie został wykonany.

> [!NOTE]
> Starsza implementacja analizy tej reguły ma inny komunikat diagnostyczny " **\[nazwa konstruktora] zawiera łańcuch wywołań, który powoduje wywołanie metody wirtualnej zdefiniowanej przez klasę. Przejrzyj następujący stos wywołań dla nieplanowanych konsekwencji**". Implementacja [FxCop analizatorów](install-fxcop-analyzers.md) dla tej reguły ma komunikat diagnostyczny "nie**wywołuj metod w konstruktorach**".

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, nie wywołuj metod wirtualnych typu z poziomu konstruktorów typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Konstruktor powinien zostać przeprojektowany w celu wyeliminowania wywołania metody wirtualnej.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje efekt naruszenia tej reguły. Aplikacja testowa tworzy wystąpienie `DerivedType`, które powoduje wykonanie jego konstruktora klasy bazowej (`BadlyConstructedType`). `BadlyConstructedType`Konstruktor niepoprawnie wywołuje metodę `DoSomething`wirtualną. Gdy dane wyjściowe są wyświetlane `DerivedType.DoSomething()` , wykonywane `DerivedType`przed konstruktorem wykonuje.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Ten przykład generuje następujące wyniki:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```