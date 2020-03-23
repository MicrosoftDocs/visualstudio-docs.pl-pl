---
title: Co nowego w profilowaniu w programie Visual Studio 2017 | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "71128339"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15"></a>Co nowego w narzędziach profilowania w[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Narzędzia diagnostyczne zawierają nowe wizualizacje ułatwiające identyfikowanie problemów w aplikacji, które wymagają naprawienia. Narzędzia diagnostyczne obejmują teraz obsługę aplikacji ASP.NET.

Aby uzyskać dodatkowe informacje, zobacz [informacje o wersji . [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes)

Karta **Podsumowanie** została dodana do narzędzi, które pomagają skupić się na kluczowych obszarach analizy wydajności. Ta karta pokazuje, ile zdarzeń miało miejsce, umożliwia tworzenie migawek sterty i umożliwia szybkie włączanie zbierania danych użycia procesora CPU. W tym widoku są wyświetlane [wszystkie zdarzenia analizy aplikacji](/azure/azure-monitor/app/visual-studio) lub interfejsu [użytkownika.](/visualstudio/releasenotes/vs2017-relnotes) Ponadto w programie Visual Studio Enterprise w tym widoku są również wyświetlane zdarzenia IntelliTrace.

![Karta Podsumowanie narzędzi diagnostycznych](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

Narzędzie użycia procesora CPU ma [nowe wizualizacje ułatwiające](../profiling/Beginners-Guide-to-Performance-Profiling.md) identyfikację funkcji, które są najbardziej prawdopodobne, że przyczyną problemów z wydajnością. Nowy widok **wywołujący/wywoływany** umożliwia badanie kosztów wywołań funkcji wykonanych do i z wybranej funkcji.

![Diagnostyka Narzędzia wywołującego widok wywoływania](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee")

## <a name="see-also"></a>Zobacz też

- [Profil w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)