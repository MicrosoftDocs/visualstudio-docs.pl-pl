---
title: 'CA2222: Nie obniżaj dziedziczonej widoczności składowych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c737a30569ab4cd59931a3fca0e500ebe96e62de
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230982"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Nie obniżaj dziedziczonej widoczności składowych

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Metoda prywatna w niezapieczętowanym typie ma sygnaturę identyczną z metodą publiczną zadeklarowaną w typie podstawowym. Metoda prywatna nie jest końcowa.

## <a name="rule-description"></a>Opis reguły

Nie zmieniaj modyfikatora dostępu dla dziedziczonych elementów członkowskich. Zmiana dziedziczonej składowej na prywatną nie uniemożliwia wywołującym uzyskania dostępu do implementacji metody klasy podstawowej. Jeśli element członkowski jest prywatny i typ jest niezapieczętowany, dziedziczenie typów może wywołać ostatnią publiczną implementację metody w hierarchii dziedziczenia. Jeśli konieczna jest zmiana modyfikatora dostępu, metoda powinna być oznaczona jako końcowa lub jej typ powinien być zapieczętowany, aby zapobiec zastąpieniu metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Zmień dostęp na nieprywatny. Alternatywnie, jeśli używany jest język programowania, można ustawić ostateczną metodę.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ, który narusza tę regułę.

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]