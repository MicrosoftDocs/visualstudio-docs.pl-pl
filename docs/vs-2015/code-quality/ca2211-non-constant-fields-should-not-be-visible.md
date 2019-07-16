---
title: 'CA2211: Pola niebędące stałymi nie powinny być widoczne | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 48d1a449301c422aa457346d1eb3d48d2f395f2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142495"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Pola niebędące stałymi nie powinny być widoczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Statyczne pole publiczne lub chronione nie jest stały, ani nie jest tylko do odczytu.

## <a name="rule-description"></a>Opis reguły
 Pola statyczne, które nie są ani stałe, ani tylko do odczytu, nie obsługują wielowątkowości. Dostęp do takich pól musi być starannie kontrolowany i wymaga zaawansowanych technik programowania do synchronizowania dostępu do obiektu klasy. Ponieważ są to trudne umiejętności, aby dowiedzieć się więcej i główny i testowania taki obiekt stanowi swój własny wyzwania, pola statyczne najlepiej są używane do przechowywania danych, która nie zmienia. Ta reguła ma zastosowanie do bibliotek; aplikacje nie powinny uwidaczniać żadnych pól.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy pole statyczne, stałe, lub tylko do odczytu. Jeśli nie jest to możliwe, należy ponownie zaprojektować typu do użycia alternatywny mechanizm, takie jak właściwość metodą o bezpiecznych wątkach, która zarządza dostępem wątków z polem. Należy pamiętać, że problemy, takie jak Rywalizacja o blokady i zakleszczenia mogą mieć wpływ na wydajność i zachowanie biblioteki.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne Pomijaj ostrzeżeń dla tej reguły, jeśli tworzysz aplikację i dlatego mają pełną kontrolę nad dostępem do typu, który zawiera pole statyczne. Projektanci biblioteki nie ma pomijać ostrzeżenie od tej reguły; za pomocą pola statyczne niestałe ułatwia korzystanie z biblioteki, które są trudne dla deweloperów, aby prawidłowo używać.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]
