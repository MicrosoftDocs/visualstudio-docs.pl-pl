---
title: 'CA1720: Identyfikatory nie powinny zawierać nazw typów'
ms.date: 03/11/2019
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
ms.openlocfilehash: c596ddfa36beec696c275ea13b662ceebf8bde2c
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841801"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Identyfikatory nie powinny zawierać nazw typów

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa parametru w elemencie członkowskim zawiera nazwę typu danych.

—lub—

Nazwa elementu członkowskiego zawiera nazwę typu danych specyficznych dla języka.

Domyślnie ta reguła przegląda tylko elementów członkowskich widocznych zewnętrznie, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Nazwy parametrów i składowych lepiej są używane do komunikowania się ich znaczenie niż na Opisz ich typu, który powinien być dostarczona przez narzędzia programistyczne. Dla nazwy elementów członkowskich Jeśli nazwa typu danych należy użyć, należy użyć nazwy niezależny od języka zamiast jednego określonego języka. Na przykład, zamiast z C# nazwy typu `int`, użyj nazwy typu danych niezależny od języka, `Int32`.

Każdy token dyskretnych nazwę parametru lub elementu członkowskiego jest porównywany następujące nazwy typu danych specyficznych dla języka bez uwzględniania wielkości liter:

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
- Float
- float32
- float64

Ponadto nazwy parametru również są porównywane z następujących nazw typu danych niezależny od języka bez uwzględniania wielkości liter:

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

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazewnictwa). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identyfikatory powinny różnić się przez więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719: Nazwy parametrów nie powinny odpowiadać nazwom elementu członkowskiego](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)