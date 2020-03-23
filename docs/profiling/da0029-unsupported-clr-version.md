---
title: 'DA0029: Nieobsługiwała wersja CLR | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dbc0bfcdb49557e56711b60dca11977a3504d907
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777518"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nieobsługiwała wersja CLR

|||
|-|-|
|Identyfikator reguły|DA0029|
|Kategoria|Użycie narzędzi profilowania|
|Metoda profilowania|Profilowanie z wiersza polecenia|
|Komunikat|Podczas zbierania wykryto nieobsługiconą wersję CLR. Zarządzane symbole mogą nie zostać poprawnie rozwiązane.|
|Typ reguły|Informacji.|

## <a name="cause"></a>Przyczyna
 Próbujesz profilować aplikację, która [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] używa tego, co nie jest obsługiwane przez narzędzia profilowania.

## <a name="rule-description"></a>Opis reguły
 To ostrzeżenie występuje, ponieważ narzędzia profilowania nie będzie w stanie rozpoznać symboli dla kodu zarządzanego uruchomionego w aplikacji. Narzędzia profilowania nie mogą rozpoznać symboli kodu [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)]zarządzanego dla aplikacji z systemem .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Brak.
