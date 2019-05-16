---
title: 'CA2104: Nie deklaruj odczytu modyfikowalnych typów referencyjnych tylko | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a4c6619bc5803c1b44e1c6b0516987c3110bbd30
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687416"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ widoczny z zewnątrz zawiera widoczne na zewnątrz pole tylko do odczytu, które jest typu referencji zmiennej.

## <a name="rule-description"></a>Opis reguły
 Typ zmienny to typ, którego dane wystąpienia mogą być modyfikowane. <xref:System.Text.StringBuilder?displayProperty=fullName> Klasy jest przykładem typu referencji zmiennej. Zawiera elementy członkowskie, które można zmienić wartość wystąpienia klasy. Na przykład typ referencyjny niezmienne <xref:System.String?displayProperty=fullName> klasy. Po utworzeniu wystąpienia, jego wartość nigdy nie można zmienić.

 Modyfikator tylko do odczytu ([tylko do odczytu](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) w języku C# [tylko do odczytu](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], i [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) w języku C++) na typ odwołania pola (wskaźnik w C++) uniemożliwia pola zastąpione przez inne wystąpienie typu referencyjnego. Jednak modyfikator nie uniemożliwia dane wystąpienia pola modyfikowana za pomocą typu odwołania.

 Pola tablicy tylko do odczytu są wykluczone z tej reguły, ale zamiast tego spowodować naruszenie [CA2105: Pola tablicy nie można odczytać tylko](../code-quality/ca2105-array-fields-should-not-be-read-only.md) reguły.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy usunąć modyfikatora tylko do odczytu lub, jeśli istotną zmianę, Zastąp pole z typem niezmienne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli typ pola jest niezmienny.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia deklarację pola, która powoduje naruszenie tej zasady.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
