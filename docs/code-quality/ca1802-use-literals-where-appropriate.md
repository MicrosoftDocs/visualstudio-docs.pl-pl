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
ms.openlocfilehash: c6512f02d13c2eeb441f5b374c4785deffe22a22
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547068"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Używaj literałów w odpowiednich miejscach

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Pole jest zadeklarowane `static` i `readonly` (`Shared` i `ReadOnly` w Visual Basic) i jest inicjowane z wartością, która jest obliczanej w czasie kompilacji.

Domyślnie ta reguła sprawdza tylko widoczne na zewnątrz pola, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Wartość `static readonly` pola jest obliczana w czasie wykonywania, gdy wywoływana jest statyczny Konstruktor dla typu deklarującego. `static readonly` Jeśli pole jest inicjowane, gdy jest zadeklarowany, a Konstruktor statyczny nie jest zadeklarowany jawnie, kompilator emituje konstruktora statycznego, aby zainicjować pole.

Wartość `const` pola jest obliczana w czasie kompilacji i przechowywana w metadanych, co zwiększa wydajność środowiska uruchomieniowego w porównaniu `static readonly` do pola.

Ponieważ wartość przypisana do pola Target jest obliczanej w czasie kompilacji, należy zmienić deklarację na `const` pole, aby wartość była obliczana w czasie kompilacji, a nie w środowisku uruchomieniowym.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Zastąp `static` modyfikator `const` i `readonly` modyfikator.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Istnieje możliwość bezpiecznego pomijania ostrzeżenia z tej reguły lub wyłączania reguły, jeśli wydajność nie jest istotna.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1802.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (wydajność). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ, `UseReadOnly`, który narusza regułę i typ, `UseConstant`który spełnia regułę.

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]