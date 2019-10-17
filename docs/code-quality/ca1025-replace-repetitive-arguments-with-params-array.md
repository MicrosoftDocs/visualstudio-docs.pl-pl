---
title: 'CA1025: Zastąp powtarzające się argumenty tabelą parametrów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6b6c45a8a56cab3927355fc4f03c541bcffc1cf
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446675"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Zastąp powtarzające się argumenty tabelą parametrów

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Kategoria|Microsoft. Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Metoda publiczna lub chroniona w typie publicznym ma więcej niż trzy parametry, a jego ostatnie trzy parametry są tego samego typu.

## <a name="rule-description"></a>Opis reguły
Użyj tablicy parametrów zamiast powtarzanych argumentów, gdy dokładna liczba argumentów jest nieznana, a argumenty zmiennych są tego samego typu lub mogą być przekazane jako ten sam typ. Na przykład Metoda <xref:System.Console.WriteLine%2A> zapewnia Przeciążenie ogólnego przeznaczenia, które używa tablicy parametrów do akceptowania dowolnej liczby argumentów <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zastąp powtarzalne argumenty tablicą parametrów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Zawsze można bezpiecznie pominąć ostrzeżenie z tej reguły. Jednak ten projekt może powodować problemy z użytecznością.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza tę regułę.

[!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]
