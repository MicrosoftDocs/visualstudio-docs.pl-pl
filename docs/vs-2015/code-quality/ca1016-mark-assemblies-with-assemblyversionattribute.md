---
title: 'CA1016: Oznacz zestawy za pomocą AssemblyVersionAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f1498624d4f79a60854a624ee5c4053a3343f515
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663171"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Oznacz zestawy za pomocą AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Zestaw nie ma numeru wersji.

## <a name="rule-description"></a>Opis reguły
 Tożsamość zestawu składa się z następujących informacji:

- Nazwa zestawu

- Numer wersji

- dziedzinie

- Klucz publiczny (dla zestawów o silnych nazwach).

  @No__t_0 używa numeru wersji do unikatowego identyfikowania zestawu i powiązania z typami w zestawach o silnej nazwie. Numer wersji jest używany razem z zasadami wersji i wydawcy. Domyślnie aplikacje są uruchamiane tylko z wersji zestawu, z którego zostały zbudowane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj numer wersji do zestawu przy użyciu atrybutu <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>. Zobacz Poniższy przykład.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły dla zestawów, które są używane przez strony trzecie lub w środowisku produkcyjnym.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje zestaw, który ma zastosowany atrybut <xref:System.Reflection.AssemblyVersionAttribute>.

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>Zobacz też
 [Przechowywanie wersji zestawu](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [instrukcje: Tworzenie zasad wydawcy](https://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)
