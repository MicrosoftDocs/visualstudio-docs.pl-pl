---
title: 'CA2200: Ponowie zgłoś wyjątek, aby zachować szczegóły stosu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5cf7fc6e31b9250392fc3ea447a5b91225640a50
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231909"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Ponowie zgłoś wyjątek, aby zachować szczegóły stosu

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Wyjątek jest ponownie zgłaszany, a wyjątek jest jawnie określony w `throw` instrukcji.

## <a name="rule-description"></a>Opis reguły

Po zgłoszeniu wyjątku część informacji, którą wykonuje, jest śladem stosu. Ślad stosu jest listą hierarchii wywołań metody, która rozpoczyna się od metody, która zgłasza wyjątek i kończą się metodą, która przechwytuje wyjątek. Jeśli wyjątek jest ponownie zgłaszany przez określenie wyjątku w `throw` instrukcji, ślad stosu zostanie ponownie uruchomiony w bieżącej metodzie, a lista wywołań metod między oryginalną metodą, która wywołała wyjątek, a bieżąca metoda zostanie utracona. Aby zachować oryginalne informacje śledzenia stosu z wyjątkiem, należy użyć `throw` instrukcji bez określenia wyjątku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, ponownie Zgłoś wyjątek bez podania wyjątku jawnie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia metodę, `CatchAndRethrowExplicitly`która narusza regułę i metodę, `CatchAndRethrowImplicitly`, która spełnia kryteria.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]