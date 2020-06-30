---
title: 'CA1034: typy zagnieżdżone nie powinny być widoczne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04a982c993ffbb04a3e7600dfb93a00e80727b84
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542171"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Typy zagnieżdżone nie powinny być widoczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz zawiera niejawnie widoczną deklarację typu. Zagnieżdżone wyliczenia i typy chronione są wykluczone z tej reguły.

## <a name="rule-description"></a>Opis reguły
 Typ zagnieżdżony jest zadeklarowany w zakresie innego typu. Zagnieżdżone typy są przydatne do hermetyzowania prywatnych szczegółów implementacji typu zawierającego. Używane w tym celu typy zagnieżdżone nie powinny być widoczne na zewnątrz.

 Nie należy używać widocznych na zewnątrz zagnieżdżonych typów dla logicznego grupowania lub w celu uniknięcia kolizji nazw; Zamiast tego należy użyć przestrzeni nazw.

 Zagnieżdżone typy obejmują pojęcie dostępności elementów członkowskich, które nie są jasno zrozumiałe dla niektórych programistów.

 Typy chronione mogą być używane w podklasach i zagnieżdżonych typach w scenariuszach dostosowywania z wyprzedzeniem.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Jeśli typ zagnieżdżony nie ma być widoczny na zewnątrz, Zmień dostępność typu. W przeciwnym razie Usuń Typ zagnieżdżony z jego elementu nadrzędnego. Jeśli celem zagnieżdżenia jest kategoryzowanie typu zagnieżdżonego, zamiast tego należy użyć przestrzeni nazw do utworzenia hierarchii.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]
