---
title: 'CA1720: Identyfikatory nie powinny zawierać nazw typów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f233863667ea7be6ecef088537fde9a104b19906
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920759"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Identyfikatory nie powinny zawierać nazw typów

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa parametru w widocznego na zewnątrz elemencie członkowskim zawiera nazwę typu danych.

 —lub—

 Nazwa widocznego na zewnątrz elementu członkowskiego zawiera nazwę typu danych specyficznych dla języka.

## <a name="rule-description"></a>Opis reguły
 Nazwy parametrów i składowych lepiej są używane do komunikowania się ich znaczenie niż na Opisz ich typu, który powinien być dostarczona przez narzędzia programistyczne. Dla nazwy elementów członkowskich Jeśli nazwa typu danych należy użyć, należy użyć nazwy niezależny od języka zamiast jednego określonego języka. Na przykład zamiast C# typu nazwy "int", należy użyć nazwę typu danych niezależny od języka, Int32.

 Każdy token dyskretnych nazwę parametru lub elementu członkowskiego jest porównywany następujące nazwy typów danych specyficznych dla języka, bez uwzględniania wielkości liter:

- Bool

- WChar

- Int8

- UInt8

- Krótkie

- UShort

- int

- UInt

- Liczba całkowita

- Uinteger —

- Długie

- ULong

- Bez znaku

- Podpisany

- float

- float32

- float64

Ponadto nazwy parametru również są porównywane z następujących nazw typu danych niezależny od języka, bez uwzględniania wielkości liter:

- Obiekt

- Obj

- Boolean

- Char

- String

- SByte

- Byte

- UByte

- Int16

- UInt16

- Int32

- UInt32

- Int64

- UInt64

- IntPtr

- Ptr

- Wskaźnik

- UInptr

- UPtr

- UPointer

- Single

- Double

- Wartość dziesiętna

- Guid

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 **Jeśli uruchamiany dla parametru:**

 Zamień na nazwę parametru identyfikatora typu danych terminu, który lepiej opis znaczenia lub terminem bardziej ogólnym, na przykład "value".

 **Jeśli uruchamiane względem elementu członkowskiego:**

 Zastąpienie identyfikatora typu danych specyficznych dla języka nazwę elementu członkowskiego terminem, lepiej opisującą jego znaczenie, odpowiednik niezależny od języka lub terminem bardziej ogólnym, na przykład "value".

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Sporadyczne użycie nazwy parametru i elementów członkowskich na podstawie typu może być odpowiednie. Jednak w przypadku nowych wdrożeń, Brak znanego scenariusze wystąpić, gdy powinna Pomijaj ostrzeżeń dla tej reguły. W przypadku bibliotek, które wcześniej zostały dostarczone może być ostrzeżenia od tej reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identyfikatory powinny różnić się przez więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Nazwy parametrów nie powinny odpowiadać nazwom elementu członkowskiego](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
