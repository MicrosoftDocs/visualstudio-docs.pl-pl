---
title: Co nowego w profilowania w programie Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 0512c6e95f0a26184593f7af5ba08c31c33a3299
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128339"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15miscincludesvs_dev15_mdmd"></a>Co nowego w narzędziach profilowania w programie[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Narzędzia diagnostyczne zawierają nowe wizualizacje ułatwiające identyfikowanie problemów w aplikacji, które wymagają rozwiązania. Narzędzia diagnostyczne obejmują teraz obsługę aplikacji ASP.NET.

Aby uzyskać dodatkowe informacje, zobacz [Informacje o wersji [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]programu ](/visualstudio/releasenotes/vs2017-relnotes).

Dodano kartę **Podsumowanie** do narzędzi, które ułatwiają skoncentrowanie się na kluczowych obszarach analizy wydajności. Na tej karcie przedstawiono liczbę zdarzeń, które wystąpiły, umożliwia wykonanie migawek sterty i pozwala szybko włączyć zbieranie danych użycia procesora CPU. Ten widok przedstawia wszystkie zdarzenia usługi [Application Insights](/azure/azure-monitor/app/visual-studio) lub [analizy interfejsu użytkownika](/visualstudio/releasenotes/vs2017-relnotes) . Ponadto w przypadku Visual Studio Enterprise widok ten pokazuje także zdarzenia IntelliTrace.

![Karta Podsumowanie narzędzi diagnostycznych](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

Narzędzie użycie procesora CPU zawiera [nowe wizualizacje](../profiling/Beginners-Guide-to-Performance-Profiling.md) ułatwiające zidentyfikowanie funkcji, które najprawdopodobniej powodują problemy z wydajnością. Nowy widok **wywołujący/wywoływany** umożliwia badanie kosztów wywołań funkcji wykonanych do i z wybranej funkcji.

![Widok wywoływany przez obiekt wywołujący narzędzi diagnostycznych](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee")

## <a name="see-also"></a>Zobacz także

- [Profil w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)