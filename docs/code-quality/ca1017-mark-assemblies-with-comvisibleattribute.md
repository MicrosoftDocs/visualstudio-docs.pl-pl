---
title: 'CA1017: Oznacz zestawy atrybutem ComVisibleAttribute'
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
ms.openlocfilehash: 073332738a01cb299b2b185c6fca20131222f981
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236255"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Oznacz zestawy atrybutem ComVisibleAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Zestaw nie ma <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> zastosowanego atrybutu.

## <a name="rule-description"></a>Opis reguły
Ten <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybut określa, w jaki sposób klienci com uzyskują dostęp do kodu zarządzanego. Zasada dobrego projektowania nakazuje, aby zestawy jawnie wskazywały widoczność COM. Widoczność COM można ustawić dla całego zestawu, a następnie przesłonić dla poszczególnych typów i elementów członkowskich typu. Jeśli atrybut nie jest obecny, zawartość zestawu jest widoczna dla klientów modelu COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Dodaj atrybut do zestawu. Jeśli nie chcesz, aby zestaw był widoczny dla klientów modelu COM, zastosuj atrybut i ustaw jego wartość na `false`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły. Jeśli zestaw ma być widoczny, zastosuj atrybut i ustaw jego wartość na `true`.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje zestaw, który ma atrybut zastosowany, <xref:System.Runtime.InteropServices.ComVisibleAttribute> aby zapobiec widocznym dla klientów modelu com.

[!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
[!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
- [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)