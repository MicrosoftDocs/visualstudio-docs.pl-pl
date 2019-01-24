---
title: 'CA2200: Ponownie, aby zachować szczegóły stosu | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed2dd2884268511ae05ac89c132f73fdf8b2771e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786568"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Ponowie zgłoś wyjątek, aby zachować szczegóły stosu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Ponownie zgłoszony wyjątek i wyjątek jest jawnie określona w `throw` instrukcji.

## <a name="rule-description"></a>Opis reguły
 Gdy wyjątek jest generowany, część informacji, który prowadzi znajduje się ślad stosu. Ślad stosu znajduje się lista hierarchię wywołań metody, która rozpoczyna się od metody, która zgłasza wyjątek, a kończy się za pomocą metody, która przechwytuje wyjątek. Jeśli wyjątek zgłaszany ponownie przez określenie wyjątku w `throw` instrukcji, ślad stosu jest uruchamiany ponownie bieżącej metody i listy wywołań metod między pierwotną metodą, która zgłosiła wyjątek, a bieżąca metoda zostaną utracone. Aby zachować oryginalne informacje śledzenia stosu, z wyjątkiem, należy użyć `throw` instrukcji bez określenia wyjątku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy ponownie zgłosić wyjątek bez jawne określenie wyjątku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano metodę `CatchAndRethrowExplicitly`, który narusza regułę i metody `CatchAndRethrowImplicitly`, które spełniają reguły.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
