---
title: 'CA1411: Metody rejestracji modelu COM nie powinny być widoczne'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e9582fb6bbdbda8aefbb60e2c69d16380eec3dff
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234754"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Metody rejestracji modelu COM nie powinny być widoczne

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Metoda oznaczona przy użyciu <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> lub atrybutu jest widoczna na zewnątrz.

## <a name="rule-description"></a>Opis reguły
Gdy zestaw jest zarejestrowany w Component Object Model (COM), wpisy są dodawane do rejestru dla każdego typu widocznego dla modelu COM w zestawie. Metody, które są oznaczone <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atrybutem and <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> , są wywoływane odpowiednio w procesach rejestracji i wyrejestrowywania, aby uruchomić kod użytkownika, który jest specyficzny dla rejestracji/wyrejestrowywania tych typów. Tego kodu nie należy wywoływać poza tymi procesami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zmień dostępność metody `private` na lub `internal` (`Friend` w programie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia dwie metody naruszające regułę.

[!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA1410: Metody rejestracji modelu COM powinny być dopasowane](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Rejestrowanie zestawów do użycia z modelem COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (narzędzie rejestracji zestawów)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)