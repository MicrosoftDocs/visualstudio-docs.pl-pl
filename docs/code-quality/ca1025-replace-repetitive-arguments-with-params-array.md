---
title: 'CA1025: Zastąp powtarzalne argumenty tablicą params'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: de109dddf3bc0ddb8cd50df8dc27e81111d4b6df
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938513"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Zastąp powtarzalne argumenty tablicą params

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona w typie publicznym ma więcej niż trzy parametry, a jego trzy ostatnie parametry są tego samego typu.

## <a name="rule-description"></a>Opis reguły
 Użyj tablicy parametrów zamiast powtarzających się argumentów, jeśli dokładna liczba argumentów jest nieznany i argumenty zmiennych są tego samego typu lub mogą być przekazywane jako tego samego typu. Na przykład <xref:System.Console.WriteLine%2A> metoda zapewnia ogólnego przeznaczenia przeciążenia, które używa tablicy parametrów, aby zaakceptować dowolną liczbę <xref:System.Object> argumentów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Zastąp powtarzające się argumenty tablicą parametrów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest zawsze bezpieczne ostrzeżenia od tej reguły; Jednak ten projekt może spowodować problemy z użytecznością.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]