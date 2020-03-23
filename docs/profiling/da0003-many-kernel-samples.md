---
title: 'DA0003: Wiele próbek jądra | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 69cd81943641e4e0585a67127c70d35a601a5396
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777741"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Wiele przykładów jądra

|||
|-|-|
|Identyfikator reguły|DA0003|
|Kategoria|Użycie narzędzi profilowania|
|Metody profilowania|Próbkowanie|
|Komunikat|Masz wysoki odsetek próbek w trybie jądra. Może to wskazywać na dużą liczbę działań we/wy lub wysoki wskaźnik przełączania kontekstu. Należy rozważyć profilowanie aplikacji ponownie za pomocą trybu instrumentacji.|
|Typ reguły|Informacje|

## <a name="cause"></a>Przyczyna
 Znaczna część próbek stosu wywołań, które zostały zebrane dla aplikacji były wykonywane w trybie jądra. Należy wziąć pod uwagę profilowanie aplikacji przy użyciu innej metody profilowania.

## <a name="rule-description"></a>Opis reguły
 W systemie Windows kod może być wykonywany w trybie jądra lub w trybie użytkownika. (Tryb jądra jest również nazywany trybem uprzywilejowanym). Tylko niski poziom kodu systemowego, takich jak sterownik urządzenia, działa w trybie jądra. Aplikacja w trybie użytkownika może przejść do trybu jądra, aby wykonywać operacje we/wy, czekać na pierwotne wiązki synchronizacji wątku lub procesu lub wykonywać wywołania systemowe.

 Próbkowanie jest najbardziej skuteczne podczas profilowania aplikacji, które spędzają większość czasu na wykonywaniu pracy w trybie użytkownika. Liczba próbek, które zostały zebrane podczas wykonywania aplikacji w trybie jądra, może wskazywać na częste operacje we/wy lub wskazać, że występują przełączniki kontekstu. Żadna z tych operacji nie może być zbadana przy użyciu metody pobierania próbek. Jeśli pobrano zbyt wiele próbek trybu jądra, dane próbkowania mogą nie zawierać wystarczającej liczby próbek trybu użytkownika, aby były statystycznie istotne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Rozważ ponowne profilowanie aplikacji przy użyciu jednej z następujących opcji:

- profilu za pomocą metody oprzyrządowania.

- Zwiększ częstotliwość próbkowania, aby spróbować zebrać więcej próbek w trybie użytkownika.
