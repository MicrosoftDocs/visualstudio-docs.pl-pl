---
title: 'CA2104: Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ff42cc2b8543fe8e1cf980a3574ae15922febf9b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521046"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ widoczny z zewnątrz zawiera widoczne na zewnątrz pole tylko do odczytu, które jest typu referencji zmiennej.

## <a name="rule-description"></a>Opis reguły
 Typ zmienny to typ, którego dane wystąpienia mogą być modyfikowane. <xref:System.Text.StringBuilder?displayProperty=fullName>Klasa jest przykładem modyfikowalnego typu odwołania. Zawiera elementy członkowskie, które mogą zmienić wartość wystąpienia klasy. Przykładem niezmiennego typu odwołania jest <xref:System.String?displayProperty=fullName> Klasa. Po utworzeniu wystąpienia jego wartość nie może ulec zmianie.

 Modyfikator tylko do odczytu ([ReadOnly](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) w języku C#, [tylko](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) do odczytu w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) w języku c++) w polu Typ odwołania (wskaźnik w języku c++) zapobiega zastąpieniu pola przez inne wystąpienie typu odwołania. Modyfikator nie zapobiega jednak modyfikowaniu danych wystąpienia pola za pośrednictwem typu referencyjnego.

 Pola tablicy tylko do odczytu są wykluczone z tej reguły, ale zamiast tego powodują naruszenie [CA2105: pola tablicy nie powinny być tylko do odczytu](../code-quality/ca2105-array-fields-should-not-be-read-only.md) .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń modyfikator tylko do odczytu lub, jeśli istotna zmiana jest akceptowalna, Zastąp pole niezmiennym typem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli typ pola jest niezmienny, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano deklarację pola, która powoduje naruszenie tej reguły.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
