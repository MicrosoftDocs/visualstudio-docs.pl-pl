---
title: 'CA2211: pola niebędące stałymi nie powinny być widoczne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: db2c667d0a3823460a084dc1e4806501d9b26693
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662957"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Niestałe pola nie powinny być widoczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Publiczne lub chronione pole statyczne nie jest stałą ani nie jest tylko do odczytu.

## <a name="rule-description"></a>Opis reguły
 Pola statyczne, które nie są ani stałe, ani tylko do odczytu, nie obsługują wielowątkowości. Dostęp do takiego pola musi być starannie kontrolowany i wymaga zaawansowanych technik programowania do synchronizowania dostępu do obiektu klasy. Ponieważ są one trudnymi umiejętnościami do uczenia się i opanowania, a testowanie takich obiektów stanowi własne wyzwania, pola statyczne są najlepiej używane do przechowywania danych, które nie są zmieniane. Ta reguła ma zastosowanie do bibliotek programu; aplikacje nie powinny ujawniać żadnych pól.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, ustaw stałą pole statyczne lub tylko do odczytu. Jeśli nie jest to możliwe, należy zaprojektować typ, aby użyć alternatywnego mechanizmu, takiego jak Właściwość bezpieczna wątkowo, która zarządza bezpiecznym wątkem dostępu do pola bazowego. Należy pamiętać, że problemy, takie jak rywalizacja o blokady i zakleszczenie, mogą mieć wpływ na wydajność i zachowanie biblioteki.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli tworzysz aplikację i masz pełną kontrolę nad dostępem do typu, który zawiera pole statyczne, można bezpiecznie pominąć ostrzeżenie z tej reguły. Projektanci bibliotek nie powinny pomijać ostrzeżenia z tej reguły. Używanie pól statycznych innych niż stałe może sprawiać, że użycie biblioteki jest trudne do poprawnego użycia przez deweloperów.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]
