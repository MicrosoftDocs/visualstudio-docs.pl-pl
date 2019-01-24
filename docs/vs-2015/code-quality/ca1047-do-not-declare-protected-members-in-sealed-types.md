---
title: 'CA1047: Nie deklaruj chronionych elementów członkowskich w typach zapieczętowanych | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6d949a756dfe3ff22ba43d172078d35bfe706e14
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792699"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Nie deklaruj chronionych składowych w typach zapieczętowanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ publiczny jest `sealed` (`NotInheritable` w języku Visual basic) ale deklaruje chroniony element członkowski lub chronionego typu zagnieżdżonego. Ta zasada zgłasza naruszenia <xref:System.Object.Finalize%2A> metody, które muszą korzystać z tego wzoru.

## <a name="rule-description"></a>Opis reguły
 Chronione elementy członkowskie są zadeklarowane w typach tak, aby typy dziedziczące miały dostęp do elementu członkowskiego i mogły go zastąpić. Zgodnie z definicją nie może dziedziczyć od typu zapieczętowanego, co oznacza, że chroniony metod w typach zapieczętowanych nie można wywołać metody.

 Kompilator języka C# generuje ostrzeżenia dla tego błędu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zmień poziom dostępu składowej na prywatną, lub zmień typ dziedziczone.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Pozostawienie typ w jego bieżącym stanie może spowodować problemy z konserwacji i nie zapewnia żadnych korzyści.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę.

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]
