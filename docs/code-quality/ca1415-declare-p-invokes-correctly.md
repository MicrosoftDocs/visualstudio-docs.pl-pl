---
title: 'CA1415: Poprawnie zadeklaruj elementy P-Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99274abee2c05a1bd33e34c9eb02cc928c1b54b0
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234614"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Poprawnie zadeklaruj elementy P/Invoke

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Bez przerywania — jeśli P/Invoke, które deklaruje parametr, nie mogą być widoczne poza zestawem. Przerywanie — jeśli P/Invoke, które deklaruje parametr, można zobaczyć poza zestawem.|

## <a name="cause"></a>Przyczyna
Metoda wywołania platformy jest nieprawidłowo zadeklarowana.

## <a name="rule-description"></a>Opis reguły
Metoda Invoke platformy uzyskuje dostęp do kodu niezarządzanego i jest definiowana `Declare` za pomocą [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] słowa kluczowego w lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Obecnie ta reguła szuka deklaracji metody wywołania platformy, które są ukierunkowane na funkcje Win32, które mają wskaźnik na nakładający się parametr struktury, a odpowiadający mu parametr zarządzany nie jest <xref:System.Threading.NativeOverlapped?displayProperty=fullName> wskaźnikiem do struktury.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy prawidłowo zadeklarować metodę wywołania platformy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje metody wywołania platformy, które naruszają regułę i spełniają regułę.

[!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Zobacz także
[Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)