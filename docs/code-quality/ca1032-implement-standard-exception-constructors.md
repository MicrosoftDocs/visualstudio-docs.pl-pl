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
ms.openlocfilehash: 7baf13eb9125b273ad8fb1265a65eb7b053238a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779127"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Zaimplementuj standardowe konstruktory wyjątków

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Rozszerza typ <xref:System.Exception?displayProperty=fullName> , ale nie deklaruje wymagane konstruktorów.

## <a name="rule-description"></a>Opis reguły

Typy wyjątków należy zaimplementować następujące trzy konstruktory:

- NewException() publiczne

- NewException(string) publiczne

- publiczne NewException (ciąg, wyjątku)

Ponadto, jeśli używasz starszej wersji programu FxCop statycznej analizy kodu jako przeciwieństwie do [analizatory FxCop analizujące kod z oparte na programie Roslyn](../code-quality/roslyn-analyzers-overview.md), braku czwarty Konstruktor generuje również naruszenie zasad:

- NewException chroniona lub prywatnej (SerializationInfo, StreamingContext)

Niepowodzenie podczas dostarczenia pełnego zestawu konstruktorów może utrudnić poprawną obsługę wyjątków. Na przykład konstruktora, który ma podpis `NewException(string, Exception)` służy do tworzenia wyjątków, które są spowodowane przez inne wyjątki. Bez tego konstruktora nie można utworzyć i zgłosić wystąpienie usługi niestandardowy wyjątek, który zawiera wewnętrzny wyjątek (zagnieżdżona), czyli jakich kodu zarządzanego, należy wykonać w takiej sytuacji.

Pierwsze konstruktory wyjątku trzech są publiczne przez Konwencję. Czwarty Konstruktor jest chronione niezapieczętowanych klas i prywatny w klasach zapieczętowanych. Aby uzyskać więcej informacji, zobacz [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Dodaj brakujące konstruktory wyjątek i upewnij się, że poprawne ułatwień dostępu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli naruszenie jest spowodowany przez przy użyciu poziomu różny dostęp dla konstruktorów publicznych. Ponadto nie szkodzi pominąć ostrzeżenie dotyczące `NewException(SerializationInfo, StreamingContext)` konstruktora, jeśli tworzysz biblioteki klas przenośnych (PCL).

## <a name="example"></a>Przykład

Poniższy przykład zawiera typ wyjątku, który narusza tę regułę i typ wyjątku, który jest implementowana prawidłowo.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Zobacz także

[CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)