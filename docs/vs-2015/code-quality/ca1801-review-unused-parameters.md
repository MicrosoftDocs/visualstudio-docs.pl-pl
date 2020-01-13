---
title: 'CA1801: Przejrzyj nieużywane parametry | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f5789b514d645fc670acf9307e4714c160c3b4c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918170"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Przejrzyj nieużywane parametry
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1801: przegląd nieużywanych parametrów](/visualstudio/code-quality/ca1801-review-unused-parameters).

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Rozdzielenie — Jeśli element członkowski nie jest widoczny poza zestawem, niezależnie od wprowadzonej zmiany.<br /><br /> Nieprzerwanie — Jeśli zmienisz element członkowski tak, aby używał parametru w jego treści.<br /><br /> Przerywanie — Jeśli parametr zostanie usunięty i będzie widoczny poza zestawem.|

## <a name="cause"></a>Przyczyna
 Podpis metody zawiera parametr, który nie jest używany w jej treści. Ta zasada nie bada następujących metod:

- Metody, do których odwołuje się delegat.

- Metody używane jako programy obsługi zdarzeń.

- Metody zadeklarowane za pomocą modyfikatora `abstract` (`MustOverride` w Visual Basic).

- Metody zadeklarowane za pomocą modyfikatora `virtual` (`Overridable` w Visual Basic).

- Metody zadeklarowane za pomocą modyfikatora `override` (`Overrides` w Visual Basic).

- Metody zadeklarowane za pomocą modyfikatora `extern` (`Declare` instrukcji in Visual Basic).

## <a name="rule-description"></a>Opis reguły
 Przejrzyj parametry w metodach niewirtualnych, które nie są używane w treści metody, aby upewnić się, że nie istnieje poprawność w przypadku niepowodzenia dostępu do nich. Nieużywane parametry wiążą się z konserwacją i wydajnością.

 Czasami naruszenie tej reguły może wskazywać na usterkę implementacji w metodzie. Na przykład parametr powinien zostać użyty w treści metody. Pomiń ostrzeżenia tej reguły, jeśli parametr musi istnieć ze względu na zgodność z poprzednimi wersjami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy usunąć nieużywany parametr (istotną zmianę) lub użyć parametru w treści metody (nieprzerwana zmiana).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły dla wcześniej dostarczonego kodu, dla którego poprawka byłaby istotną zmianą.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia dwie metody. Jedna metoda narusza regułę, a druga metoda spełnia regułę.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1811: Unikaj niewywoływanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)
