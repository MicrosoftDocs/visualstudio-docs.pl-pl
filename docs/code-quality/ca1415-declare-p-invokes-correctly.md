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
ms.openlocfilehash: c5cc12d5d0a62f8d2530f13fcf860aba4e118ca4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921853"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Poprawnie zadeklaruj elementy P/Invoke

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Bez przerywania — jeśli P/Invoke, które deklaruje parametr, nie mogą być widoczne poza zestawem. Przerywanie — jeśli P/Invoke, które deklaruje parametr, można zobaczyć poza zestawem.|

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