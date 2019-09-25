---
title: 'CA1811: Unikaj niewywołanego kodu prywatnego'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a7542499eceeccbd62ce327b386dc099b726b2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233621"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Unikaj niewywołanego kodu prywatnego

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Kategoria|Microsoft.Performance|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Element członkowski prywatny lub wewnętrzny (poziom zestawu) nie ma elementów wywołujących w zestawie, nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego i nie jest wywoływany przez delegata. Następujące elementy członkowskie nie są sprawdzane przez tę regułę:

- Jawne elementy członkowskie interfejsu.

- Konstruktory statyczne.

- Konstruktory serializacji.

- Metody oznaczone <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atrybutem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>or.

- Elementy członkowskie, które są zastępują.

## <a name="rule-description"></a>Opis reguły
Ta reguła może zgłosić fałszywie dodatnie, jeśli występują punkty wejścia, które nie są obecnie identyfikowane przez logikę reguł. Ponadto kompilator może emitować niewywołujący kod do zestawu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, Usuń kod niewywołujący lub Dodaj kod, który go wywołuje.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="related-rules"></a>Powiązane reguły
[CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Usuń nieużywane elementy lokalne](../code-quality/ca1804-remove-unused-locals.md)