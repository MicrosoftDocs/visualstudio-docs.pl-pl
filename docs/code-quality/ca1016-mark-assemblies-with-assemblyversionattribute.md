---
title: 'CA1016: Oznacz zestawy atrybutem AssemblyVersion'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 140037b025db88230762bc0d540d933cec7a5119
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236310"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Oznacz zestawy atrybutem AssemblyVersion

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Zestaw nie ma numeru wersji.

## <a name="rule-description"></a>Opis reguły

Tożsamość zestawu składa się z następujących informacji:

- Nazwa zestawu

- Numer wersji

- Kultura

- Klucz publiczny (dla zestawów o silnych nazwach).

Platforma .NET używa numeru wersji do unikatowego identyfikowania zestawu i powiązania z typami w zestawach o silnej nazwie. Numer wersji jest używany razem z zasadami wersji i wydawcy. Domyślnie aplikacje są uruchamiane tylko z wersji zestawu, z którego zostały zbudowane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Dodaj numer wersji do zestawu przy użyciu <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> atrybutu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżenia z tej reguły dla zestawów, które są używane przez strony trzecie lub w środowisku produkcyjnym.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje zestaw, do <xref:System.Reflection.AssemblyVersionAttribute> którego zastosowano atrybut.

[!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
[!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
[!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Zobacz także

- [Przechowywanie wersji zestawu](/dotnet/framework/app-domains/assembly-versioning)
- [Instrukcje: Tworzenie zasad wydawcy](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)