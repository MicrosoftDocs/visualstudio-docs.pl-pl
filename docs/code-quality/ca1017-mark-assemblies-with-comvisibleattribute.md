---
title: 'CA1017: Oznacz zestawy za pomocą ComVisibleAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: daf9da821178e9e17ed5f0693d4d268b04ca337c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441624"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Oznacz zestawy za pomocą ComVisibleAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Kategoria|Microsoft. Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Zestaw nie ma zastosowanego atrybutu <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
Atrybut <xref:System.Runtime.InteropServices.ComVisibleAttribute> Określa, jak klienci COM uzyskują dostęp do kodu zarządzanego. Zasada dobrego projektowania nakazuje, aby zestawy jawnie wskazywały widoczność COM. Widoczność COM można ustawić dla całego zestawu, a następnie przesłonić dla poszczególnych typów i elementów członkowskich typu. Jeśli atrybut nie jest obecny, zawartość zestawu jest widoczna dla klientów modelu COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Dodaj atrybut do zestawu. Jeśli nie chcesz, aby zestaw był widoczny dla klientów modelu COM, zastosuj atrybut i ustaw jego wartość na `false`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły. Jeśli zestaw ma być widoczny, zastosuj atrybut i ustaw jego wartość na `true`.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje zestaw, który ma atrybut <xref:System.Runtime.InteropServices.ComVisibleAttribute> zastosowany, aby zapobiec widocznym dla klientów modelu COM.

[!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
[!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
- [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
