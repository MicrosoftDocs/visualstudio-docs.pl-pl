---
title: 'CA1017: Oznacz zestawy atrybutem ComVisibleAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 85c3abdce2845cc46e92ae6b0c4c9d565562bcad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959281"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Oznacz zestawy atrybutem ComVisibleAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Zestaw nie ma <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> zastosowany do niego.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Atrybut określa, w jaki sposób klienci COM dostęp do kodu zarządzanego. Zasada dobrego projektowania nakazuje, aby zestawy jawnie wskazywały widoczność COM. Widoczność COM można ustawić dla całego zestawu i następnie zastąpić dla poszczególnych typów i elementów członkowskich typu. Jeśli ten atrybut nie jest obecny, zawartość zestawu są widoczne dla klientów modelu COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Dodaj atrybut do zestawu. Jeśli nie chcesz, zestawów, które mają być widoczne dla klientów modelu COM, zastosuj atrybut i ustawić jej wartość na `false`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Jeśli chcesz, aby zestaw był widoczny, zastosuj atrybut i ustawić jej wartość na `true`.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono zestaw, który ma <xref:System.Runtime.InteropServices.ComVisibleAttribute> zastosowany do uniemożliwić jest widoczny dla klientów modelu COM.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
- [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)