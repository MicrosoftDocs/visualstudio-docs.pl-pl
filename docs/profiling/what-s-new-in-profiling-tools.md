---
title: What's New in profilowania | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b1822ec74903c8baa75ce437b0115cecdfb911c3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026948"
---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Co nowego w narzędziach profilowania w [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Narzędzia diagnostyczne zawierają nowe wizualizacje, aby pomóc w zidentyfikowaniu problemów w aplikacji, które wymagają ustalania. Narzędzia diagnostyczne obejmują teraz obsługę aplikacji programu ASP.NET.

Aby uzyskać więcej informacji, zobacz [informacje o wersji programu [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes#debuggingdiag).

A **Podsumowanie** karta została dodana do narzędzia, które pomaga skoncentrować się na kluczowych obszarach analizy wydajności. Ta karta pokazuje, ile zdarzenia wystąpiły pozwala korzystać z migawki sterty i pozwala na szybkie włączenie zbierania danych użycia procesora CPU. Ten widok przedstawia dowolne [usługi Application insights](/azure/azure-monitor/app/visual-studio) lub [analiza interfejsu użytkownika](/visualstudio/releasenotes/vs2017-relnotes#UIAnalysis) zdarzenia. Ponadto dla programu Visual Studio Enterprise, ten widok również przedstawia zdarzenia funkcji IntelliTrace.

![Karta podsumowania narzędzia diagnostyczne](../profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

Narzędzie użycie procesora CPU ma [nowe wizualizacje](../profiling/Beginners-Guide-to-Performance-Profiling.md) ułatwiający zidentyfikowanie funkcji, które z największym prawdopodobieństwem mogą być przyczyną problemów z wydajnością. Nowy **wywołujący/wywoływany** widoku pozwala na badanie kosztów wywołań funkcji wykonanych do i z wybranej funkcji.

![Widok wywoływany obiekt wywołujący narzędzia diagnostyczne](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")

## <a name="see-also"></a>Zobacz także

- [Profil w programie Visual Studio](../profiling/index.md)
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)