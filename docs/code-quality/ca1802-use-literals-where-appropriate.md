---
title: 'CA1802: Używaj literałów w odpowiednich miejscach'
ms.date: 03/11/2019
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
ms.openlocfilehash: dfa50fc6007c2313191b430e9ed5445e7fd72a88
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841562"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Używaj literałów w odpowiednich miejscach

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Pole jest zadeklarowane jako `static` i `readonly` (`Shared` i `ReadOnly` w języku Visual Basic) i jest inicjowany z wartością, która jest obliczana w czasie kompilacji.

Domyślnie ta reguła przegląda tylko pola widocznego na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Wartość `static readonly` pola jest obliczana w czasie wykonywania, gdy wywoływana jest konstruktor statyczny dla elementu typ deklarujący. Jeśli `static readonly` pola jest inicjowane, gdy jest on zadeklarowany jako statyczny Konstruktor nie został zadeklarowany jawnie, kompilator generuje Konstruktor statyczny do inicjowania pola.

Wartość `const` pola jest obliczane w czasie kompilacji i przechowywany w metadanych, co zwiększa wydajność środowiska uruchomieniowego w porównaniu z `static readonly` pola.

Ponieważ wartość przypisana do pola docelowego jest obliczana w czasie kompilacji, zmień deklarację do `const` tak, aby wartość jest obliczana w czasie kompilacji, a nie w czasie wykonywania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zastąpić `static` i `readonly` Modyfikatory z `const` modyfikator.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpiecznie Pomijaj ostrzeżeń dla tej reguły lub wyłączyć regułę, jeśli wydajność nie jest istotna.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1802.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (wydajność). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano typem `UseReadOnly`, który narusza regułę i typu `UseConstant`, odpowiadającej reguły.

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]