---
title: 'CA1410: Metody rejestracji COM powinny być dopasowane'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c7c7c20ece08bc5167887727e423a3f7cdf7ee19
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440205"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Metody rejestracji COM powinny być dopasowane

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ deklaruje metodę, która jest oznaczona atrybutem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, ale nie deklaruje metody, która jest oznaczona za pomocą atrybutu <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> lub odwrotnie.

## <a name="rule-description"></a>Opis reguły

W przypadku klientów Component Object Model (COM) do tworzenia typu .NET należy najpierw zarejestrować typ. Jeśli jest dostępny, metoda oznaczona przy użyciu atrybutu <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> jest wywoływana podczas procesu rejestracji w celu uruchomienia kodu określonego przez użytkownika. Odpowiadająca metoda oznaczona atrybutem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> jest wywoływana podczas procesu wyrejestrowywania, aby wycofać operacje metody rejestracji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Dodaj odpowiednią metodę rejestracji lub wyrejestrowywania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ, który narusza regułę. Kod z komentarzem pokazuje poprawkę dla naruszenia.

[!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

[CA1411: Metody rejestracji modelu COM nie powinny być widoczne](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Rejestrowanie zestawów przy użyciu modelu COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (narzędzie rejestracji zestawów)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)
