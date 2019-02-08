---
title: 'CA2214: Nie wywołuj w konstruktorach metod, które można przesłaniać'
ms.date: 11/04/2016
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
ms.openlocfilehash: ef2a5631247f882a70ae94877da02f576ff04a5d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55946031"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Nie wywołuj w konstruktorach metod, które można przesłaniać

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Konstruktor obiektu niezapieczętowanego typu wywołuje metody wirtualnej zdefiniowanej w swojej klasie.

## <a name="rule-description"></a>Opis reguły

Po wywołaniu metody wirtualnej rzeczywisty typ, który wykonuje metodę nie jest zaznaczone do czasu wykonywania. Gdy Konstruktor wywołuje metodę wirtualną, jest możliwe, że Konstruktor wystąpienia, które wywołuje metodę nie zostało wykonane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, nie wywołuj metody wirtualne typu z konstruktorów typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Konstruktor powinien przeprojektowane, aby wyeliminować wywołanie wirtualnej metody.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje efekt naruszenie tej zasady. Aplikacja testowa tworzy wystąpienie `DerivedType`, co powoduje, że jej klasa podstawowa (`BadlyConstructedType`) Konstruktor do wykonania. `BadlyConstructedType`jego Konstruktor niepoprawnie wywołuje metodę wirtualną `DoSomething`. Dane wyjściowe pokazują, `DerivedType.DoSomething()` wykonuje, a więc przed jest `DerivedType`przez konstruktora.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Ten przykład generuje następujące wyniki:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```