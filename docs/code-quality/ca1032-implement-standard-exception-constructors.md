---
title: 'CA1032: Zaimplementuj standardowe konstruktory wyjątków'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad062154b8213d021c8c265aaf287d3a9335d0e4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922881"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Zaimplementuj standardowe konstruktory wyjątków

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ rozciąga <xref:System.Exception?displayProperty=fullName> się, ale nie deklaruje wszystkich wymaganych konstruktorów.

## <a name="rule-description"></a>Opis reguły

Typy wyjątków muszą implementować następujące trzy konstruktory:

- Public NewException ()

- Public NewException (ciąg)

- Public NewException (ciąg, wyjątek)

Ponadto, jeśli używasz starszej analizy kodu statycznego FxCop w przeciwieństwie do [analizatorów FxCop opartych na Roslyn](../code-quality/roslyn-analyzers-overview.md), brak czwartego konstruktora również generuje naruszenie:

- chroniona lub prywatna NewException (SerializationInfo, StreamingContext)

Niepowodzenie podczas dostarczenia pełnego zestawu konstruktorów może utrudnić poprawną obsługę wyjątków. Na przykład Konstruktor, który ma sygnaturę `NewException(string, Exception)` , jest używany do tworzenia wyjątków, które są spowodowane innymi wyjątkami. Bez tego konstruktora nie można utworzyć i zgłosić wystąpienia wyjątku niestandardowego, który zawiera wewnętrzny (zagnieżdżony) wyjątek, który jest tym, jaki kod zarządzany powinien wykonać w takiej sytuacji.

Pierwsze trzy konstruktory wyjątków są publiczne według Konwencji. Czwarty Konstruktor jest chroniony w niezapieczętowanych klasach i prywatny w klasach zapieczętowanych. Aby uzyskać więcej informacji, [Zobacz CA2229: Implementuj konstruktory](../code-quality/ca2229-implement-serialization-constructors.md)serializacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Dodaj brakujące konstruktory do wyjątku i upewnij się, że mają one poprawną dostępność.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły, gdy naruszenie jest spowodowane przez użycie innego poziomu dostępu dla konstruktorów publicznych. Ponadto w przypadku kompilowania biblioteki klas przenośnych (PCL) `NewException(SerializationInfo, StreamingContext)` nie można pominąć ostrzeżenia dla konstruktora.

## <a name="example"></a>Przykład

Poniższy przykład zawiera typ wyjątku, który narusza tę regułę i typ wyjątku, który jest poprawnie zaimplementowany.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Zobacz także

[CA2229: Implementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)