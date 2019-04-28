---
title: What's New in profilowania w programie Visual Studio 2017 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8fcd01198877ef06eb398ce99fe467deb923546c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999221"
---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Co nowego w narzędziach profilowania w [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Narzędzia diagnostyczne zawierają nowe wizualizacje, aby pomóc w zidentyfikowaniu problemów w aplikacji, które wymagają ustalania. Narzędzia diagnostyczne obejmują teraz obsługę aplikacji programu ASP.NET.

Aby uzyskać więcej informacji, zobacz [informacje o wersji programu [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes).

A **Podsumowanie** karta została dodana do narzędzia, które pomaga skoncentrować się na kluczowych obszarach analizy wydajności. Ta karta pokazuje, ile zdarzenia wystąpiły pozwala korzystać z migawki sterty i pozwala na szybkie włączenie zbierania danych użycia procesora CPU. Ten widok przedstawia dowolne [usługi Application insights](/azure/azure-monitor/app/visual-studio) lub [analiza interfejsu użytkownika](/visualstudio/releasenotes/vs2017-relnotes) zdarzenia. Ponadto dla programu Visual Studio Enterprise, ten widok również przedstawia zdarzenia funkcji IntelliTrace.

![Karta podsumowania narzędzia diagnostyczne](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

Narzędzie użycie procesora CPU ma [nowe wizualizacje](../profiling/Beginners-Guide-to-Performance-Profiling.md) ułatwiający zidentyfikowanie funkcji, które z największym prawdopodobieństwem mogą być przyczyną problemów z wydajnością. Nowy **wywołujący/wywoływany** widoku pozwala na badanie kosztów wywołań funkcji wykonanych do i z wybranej funkcji.

![Widok wywoływany obiekt wywołujący narzędzia diagnostyczne](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee")

## <a name="see-also"></a>Zobacz także

- [Profil w programie Visual Studio](../profiling/index.md)
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)