---
title: 'CA1801: Przejrzyj nieużywane parametry'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b7fdbf4d842218b8a06146c777a1e468459d140
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921007"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Przejrzyj nieużywane parametry

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału — Jeśli element członkowski nie jest widoczna spoza zestawu, niezależnie od tego, zmiany wprowadzone.<br /><br /> Bez podziału — w przypadku zmiany należy użyć parametru w swojej treści.<br /><br /> Przerywanie — Usuń parametr, jeśli jest on widoczny spoza zestawu.|

## <a name="cause"></a>Przyczyna
 Podpis metody zawiera parametr, który nie jest używany w jej treści. Ta reguła analizuje następujących metod:

- Metody odwołuje się obiekt delegowany.

- Metody stosowane jako programów obsługi zdarzeń.

- Metody zadeklarowane za pomocą `abstract` (`MustOverride` w języku Visual Basic) modyfikator.

- Metody zadeklarowane za pomocą `virtual` (`Overridable` w języku Visual Basic) modyfikator.

- Metody zadeklarowane za pomocą `override` (`Overrides` w języku Visual Basic) modyfikator.

- Metody zadeklarowane za pomocą `extern` (`Declare` instrukcji w języku Visual Basic) modyfikator.

## <a name="rule-description"></a>Opis reguły
 Przejrzyj parametry w metod niewirtualnych, które nie są używane w treści metody, aby upewnić się, że nie poprawność istnieje wokół nie można uzyskać do nich dostęp. Nieużywane parametry ponosić kosztów konserwacji i wydajności.

 Czasami naruszenie tej zasady może wskazywać na błąd implementacji w metodzie. Na przykład parametr powinien mieć używany w treści metody. Pomijanie ostrzeżeń, tej reguły, jeśli parametr musi istnieć ze względu na zgodność z poprzednimi wersjami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń nieużywany parametr (istotnej zmiany), lub użyj parametru w treści metody (zmiany niepowodujące niezgodności).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły dla uprzednio wysłane kodu, dla których poprawki będą istotnej zmiany.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia dwa sposoby. Narusza regułę określającą jedną z metod i inne metody spełnia reguły.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)