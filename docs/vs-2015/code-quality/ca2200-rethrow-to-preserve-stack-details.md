---
title: 'CA2200: ponownie zgłoś, aby zachować szczegóły stosu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6d63ef6ff3647742e931fd05f59c66b40059ad00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546370"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Ponowie zgłoś wyjątek, aby zachować szczegóły stosu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Wyjątek jest ponownie zgłaszany, a wyjątek jest jawnie określony w `throw` instrukcji.

## <a name="rule-description"></a>Opis reguły
 Po zgłoszeniu wyjątku część informacji, którą wykonuje, jest śladem stosu. Ślad stosu jest listą hierarchii wywołań metody, która rozpoczyna się od metody, która zgłasza wyjątek i kończą się metodą, która przechwytuje wyjątek. Jeśli wyjątek jest ponownie zgłaszany przez określenie wyjątku w `throw` instrukcji, ślad stosu zostanie ponownie uruchomiony w bieżącej metodzie, a lista wywołań metod między oryginalną metodą, która wywołała wyjątek, a bieżąca metoda zostanie utracona. Aby zachować oryginalne informacje śledzenia stosu z wyjątkiem, należy użyć `throw` instrukcji bez określenia wyjątku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, ponownie Zgłoś wyjątek bez określenia wyjątku jawnie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, `CatchAndRethrowExplicitly` która narusza regułę i metodę, `CatchAndRethrowImplicitly` , która spełnia kryteria.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
