---
title: 'CA1802: Używaj literałów w odpowiednich miejscach'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4f6b469ccce9cc5297cf9c328b05822aef9e3e29
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55925257"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Używaj literałów w odpowiednich miejscach

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Pole jest zadeklarowane jako `static` i `readonly` (`Shared` i `ReadOnly` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) i jest inicjowany z wartością, która jest obliczana w czasie kompilacji.

## <a name="rule-description"></a>Opis reguły
 Wartość `static``readonly` pola jest obliczana w czasie wykonywania, gdy wywoływana jest konstruktor statyczny dla elementu typ deklarujący. Jeśli `static``readonly` pola jest inicjowane, gdy jest on zadeklarowany jako statyczny Konstruktor nie został zadeklarowany jawnie, kompilator generuje Konstruktor statyczny do inicjowania pola.

 Wartość `const` pola jest obliczane w czasie kompilacji i przechowywany w metadanych, co zwiększa wydajność środowiska uruchomieniowego w porównaniu z `static``readonly` pola.

 Ponieważ wartość przypisana do pola docelowego jest obliczana w czasie kompilacji, zmień deklarację do `const` tak, aby wartość jest obliczana w czasie kompilacji, a nie w czasie wykonywania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zastąpić `static` i `readonly` Modyfikatory z `const` modyfikator.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpiecznie Pomijaj ostrzeżeń dla tej reguły lub wyłączyć regułę, jeśli wydajność nie jest istotna.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typem `UseReadOnly`, który narusza regułę i typu `UseConstant`, odpowiadającej reguły.

 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]