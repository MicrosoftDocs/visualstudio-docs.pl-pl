---
title: 'CA1720: identyfikatory nie powinny zawierać nazw typów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34ebe4848bbbe49b9a67449795f0aea7d104af8b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671636"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Identyfikatory nie powinny zawierać nazw typów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa parametru w widocznym na zewnątrz elemencie członkowskim zawiera nazwę typu danych.

 —lub—

 Nazwa widocznego na zewnątrz elementu członkowskiego zawiera nazwę typu danych specyficzną dla języka.

## <a name="rule-description"></a>Opis reguły
 Nazwy parametrów i składowych są lepiej używane do przekazywania ich znaczenia niż opisywanie ich typu, który powinien być udostępniany przez narzędzia deweloperskie. W przypadku nazw członków, jeśli nazwa typu danych musi być użyta, należy użyć nazwy niezależnej od języka, a nie dla konkretnego języka. Na przykład zamiast nazwy C# typu "int" należy użyć nazwy typu danych niezależnej od języka, Int32.

 Każdy token dyskretny w nazwie parametru lub elementu członkowskiego jest sprawdzany pod kątem następujących nazw typów danych specyficznych dla języka, w sposób niezależny od wielkości liter:

- Logiczna

- WChar

- Int8

- UInt8

- Wybierak

- UShort

- int

- UInt

- Liczba całkowita

- UInteger —

- Długo

- ULong

- Bajt

- Opatrzon

- Float

- Float32

- Float64

  Ponadto nazwy parametrów są również sprawdzane pod względem następujących nazw niezależnych od języka, bez uwzględniania wielkości liter:

- Obiekt

- Obiektów

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

- PTR

- Przytrzymaj

- UInptr

- UPtr

- UPointer

- Single

- Double

- Wartość dziesiętna

- Ident

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 **Jeśli jest uruchamiany dla parametru:**

 Zastąp identyfikator typu danych w nazwie parametru wyrażeniem, które lepiej opisuje jego znaczenie lub bardziej ogólny termin, na przykład "value".

 **Jeśli jest uruchamiany dla elementu członkowskiego:**

 Zastąp charakterystyczny dla języka Identyfikator typu danych w nazwie elementu członkowskiego terminem, który lepiej opisuje jego znaczenie, odpowiednik niezależny od języka lub bardziej ogólny termin, na przykład "value".

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Może być konieczne sporadyczne użycie nazw parametrów i elementów członkowskich opartych na typie. Jednak w przypadku nowych rozwiązań nie występują żadne znane scenariusze, w których należy pominąć ostrzeżenie z tej reguły. W przypadku bibliotek, które zostały wysłane wcześniej, może być konieczne pominięcie ostrzeżenia z tej reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Nazwy parametrów nie powinny odpowiadać nazwom składowych](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
