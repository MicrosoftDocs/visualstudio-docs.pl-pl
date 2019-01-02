---
title: 'CA2200: Ponownie, aby zachować szczegóły stosu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6b52d6d9081827de764e47399dc09159d29ad149
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915776"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Ponownie, aby zachować szczegóły stosu

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Wyjątek jest zgłaszany ponownie i jawnie określony wyjątek w `throw` instrukcji.

## <a name="rule-description"></a>Opis reguły

Gdy wyjątek jest generowany, część informacji, który prowadzi znajduje się ślad stosu. Ślad stosu znajduje się lista hierarchię wywołań metody, która rozpoczyna się od metody, która zgłasza wyjątek, a kończy się za pomocą metody, która przechwytuje wyjątek. Jeśli wyjątek zgłaszany ponownie przez określenie wyjątku w `throw` instrukcji, ślad stosu jest uruchamiany ponownie bieżącej metody i listy wywołań metod między pierwotną metodą, która zgłosiła wyjątek, a bieżąca metoda zostaną utracone. Aby zachować oryginalne informacje śledzenia stosu, z wyjątkiem, należy użyć `throw` instrukcji bez określenia wyjątku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, zgłoś ponownie wyjątek bez jawne określenie wyjątku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano metodę `CatchAndRethrowExplicitly`, który narusza regułę i metody `CatchAndRethrowImplicitly`, które spełniają reguły.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]