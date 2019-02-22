---
title: 'DA0003: Wiele przykładów jądra | Dokumentacja firmy Microsoft'
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
ms.workload:
- multiple
ms.openlocfilehash: 84c44c8417247d4d33f66e8c56ed1775f6c895ac
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607840"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Wiele przykładów jądra

|||
|-|-|
|Identyfikator reguły|DA0003|
|Kategoria|Użycie narzędzia profilowania|
|Metod profilowania|Próbkowania|
|Komunikat|Masz dużą część próbek w trybie jądra. To może wskazywać dużą aktywność We/Wy lub wysokie tempo przełączania kontekstu. Należy wziąć pod uwagę w aplikacji z użyciem trybu instrumentacji.|
|Typ reguły|Informacje|

## <a name="cause"></a>Przyczyna
 Znaczna część przykłady stosu wywołań, które zostały zebrane dla aplikacji zostały wykonywania w trybie jądra. Należy wziąć pod uwagę, profilowanie aplikacji przy użyciu innej metody profilowania.

## <a name="rule-description"></a>Opis reguły
 W Windows kod może być wykonywana w trybie jądra lub w trybie użytkownika. (Tryb jądra jest również nazywane trybie uprzywilejowanym). Tylko kod niskiego poziomu systemu, takie jak sterownik urządzenia, działa w trybie jądra. Aplikacja w trybie użytkownika, można przejść do trybu jądra do wykonywania operacji We/Wy, poczekaj, aż wątek lub procesu synchronizacji w nim elementów podstawowych lub wykonać wywołania systemowe.

 Próbkowanie jest najbardziej efektywne w przypadku profilowania aplikacji, które spędzają większość czasu wykonywania pracy w trybie użytkownika. Liczba próbek, które zostały zebrane podczas wykonywania aplikacji w trybie jądra można wskazać częstych operacji We/Wy lub może wskazywać tego kontekstu, w których występują przełączników. Żadna z tych operacji można sprawdzić przy użyciu metody próbkowania. Podjęto zbyt wiele przykładów trybu jądra, dane z próbkowania może nie zawierać wystarczającej liczby próbek trybu użytkownika będzie statystycznie istotne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Należy wziąć pod uwagę profilowania aplikację ponownie przy użyciu jednego z następujących opcji:

-   Profile, przy użyciu metody instrumentacji.

-   Zwiększ częstotliwość próbkowania w celu próbuje zebrać więcej przykładów w trybie użytkownika.