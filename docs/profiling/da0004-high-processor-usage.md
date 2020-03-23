---
title: 'DA0004: Wysokie zużycie procesora | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b324d26d21920bae9f03f909b2eab0c1ce7ab419
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777728"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Znaczące wykorzystanie czasu procesora

|||
|-|-|
|Identyfikator reguły|DA0004|
|Kategoria|Użycie narzędzi profilowania|
|Metody profilowania|Oprzyrządowanie<br /><br /> Próbkowanie|
|Komunikat|Użycie procesora jest stale powyżej 75%. Należy rozważyć użycie trybu próbkowania dla aplikacji związanych z procesorem CPU.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Wykorzystanie procesora (CPU) było wysokie w danych profilowania, które zostały zebrane przy użyciu metody instrumentacji. Należy rozważyć użycie metody profilowania próbkowania podczas profilowania aplikacji związanej z procesorem CPU.

## <a name="rule-description"></a>Opis reguły
 Podczas tego przebiegu profilowania procesor (lub procesory) był stale zajęty. Wysokie wykorzystanie procesora CPU może wskazywać na aplikację związaną z procesorem CPU. Profili instrumentowanych nie są najskuteczniejszym sposobem zbadania scenariuszy użycia procesora CPU. Próbkowanie jest bardziej skuteczne podczas profilowania aplikacji, które spędzają dużo czasu na wykonywaniu instrukcji na procesorze.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Należy rozważyć profilowanie aplikacji ponownie przy użyciu metody próbkowania zamiast metody instrumentacji, chyba że wymagają chronometrażu funkcji lub jesteś bardziej zainteresowany zrozumieniem danych wejściowych/wyjściowych niż wąskich gardeł procesora.
