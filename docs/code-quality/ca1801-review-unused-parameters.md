---
title: 'CA1801: Dokonaj przeglądu nieużywanych parametrów'
ms.date: 06/24/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6de48bf273a5c93afcd14e7bab2c5d4c4c4b5a7c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233827"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Dokonaj przeglądu nieużywanych parametrów

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Rozdzielenie — Jeśli element członkowski nie jest widoczny poza zestawem, niezależnie od wprowadzonej zmiany.<br /><br /> Nieprzerwanie — Jeśli zmienisz element członkowski tak, aby używał parametru w jego treści.<br /><br /> Przerywanie — Jeśli parametr zostanie usunięty i będzie widoczny poza zestawem.|

## <a name="cause"></a>Przyczyna

Sygnatura metody zawiera parametr, który nie jest używany w treści metody.

Ta zasada nie bada następujących rodzajów metod:

- Metody, do których odwołuje się delegat.

- Metody używane jako programy obsługi zdarzeń.

- Metody zadeklarowane za `abstract` pomocą`MustOverride` modyfikatora (w Visual Basic).

- Metody zadeklarowane za `virtual` pomocą`Overridable` modyfikatora (w Visual Basic).

- Metody zadeklarowane za `override` pomocą`Overrides` modyfikatora (w Visual Basic).

- Metody zadeklarowane za `extern` pomocą`Declare` modyfikatora (instrukcja w Visual Basic).

Jeśli używasz [analizatorów FxCop](install-fxcop-analyzers.md), ta reguła nie flaguje parametrów, które są nazwane przy użyciu symbolu [odrzucenia](/dotnet/csharp/discards) , `_`na `_1`przykład,, i `_2`. Zmniejsza to szumu ostrzegawczego dotyczące parametrów, które są potrzebne do wymagań podpisu, na przykład metodę używaną jako delegat, parametr z atrybutami specjalnymi lub parametr, którego wartość jest niejawnie dostępna w czasie wykonywania przez platformę, ale nie odwołuje się do niej kodu.

## <a name="rule-description"></a>Opis reguły

Przejrzyj parametry w metodach niewirtualnych, które nie są używane w treści metody, aby upewnić się, że nie ma żadnych nieprawidłowych błędów dostępu do nich. Nieużywane parametry wiążą się z konserwacją i wydajnością.

Czasami naruszenie tej reguły może wskazywać na usterkę implementacji w metodzie. Na przykład parametr powinien zostać użyty w treści metody. Pomiń ostrzeżenia tej reguły, jeśli parametr musi istnieć ze względu na zgodność z poprzednimi wersjami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy usunąć nieużywany parametr (istotną zmianę) lub użyć parametru w treści metody (nieprzerwana zmiana).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły:

- W wcześniej dostarczonym kodzie, dla którego poprawka byłaby istotną zmianą.

- Dla parametru w niestandardowej metodzie rozszerzenia dla <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=nameWithType>. `this` Funkcje w <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> klasie są statyczne, więc nie ma potrzeby `this` uzyskiwania dostępu do parametru w treści metody.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia dwie metody. Jedna metoda narusza regułę, a druga metoda spełnia regułę.

[!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Powiązane reguły

[CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804: Usuń nieużywane elementy lokalne](../code-quality/ca1804-remove-unused-locals.md)
