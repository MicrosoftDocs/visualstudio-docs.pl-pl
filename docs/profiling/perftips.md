---
title: PerfTips | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93703bdd4bf2f0046176ceb1f6febd5564f61705
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "71128308"
---
# <a name="perftips"></a>Wskazówki dotyczące wydajności
Porady *dotyczące aplikerów* debugera programu Visual Studio i zintegrowane z debugerem **narzędzia diagnostyczne** ułatwiają monitorowanie i analizowanie wydajności aplikacji podczas debugowania.

 Mimo że narzędzia diagnostyczne zintegrowane z debugerem są doskonałym sposobem na uświadomienie sobie problemów z wydajnością podczas tworzenia, debuger może mieć znaczący wpływ na wydajność aplikacji. Aby zebrać dokładniejsze dane dotyczące wydajności, należy rozważyć użycie narzędzi diagnostycznych programu Visual Studio, które są uruchamiane poza debugerem jako dodatkową część badań wydajności. Zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>Wskazówki dotyczące wydajności
 Gdy debuger zatrzymuje wykonanie w punkcie przerwania lub operacji krokowej, czas, który upłynął między przerwą a poprzednim punktem przerwania pojawia się jako wskazówka w oknie edytora. Aby uzyskać więcej informacji, zobacz [Porady dotyczące wydajności: Informacje o wydajności w skrócie podczas debugowania za pomocą programu Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

 ![PerfTip (perfTip)](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Okno Narzędzia diagnostyczne
 Punkty przerwania i skojarzone dane chronometrażu są rejestrowane w oknie **Narzędzia diagnostyczne.**

 Na poniższej ilustracji przedstawiono okno **Narzędzia diagnostyczne** w programie Visual Studio 2015 Update 1:

 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

- Oś czasu **przerwania zdarzenia** oznaczyć punkty przerwania, które zostały trafione w sesji debugowania. Kliknij zdarzenie, aby wybrać listę szczegółów **debugera.**

- Wykres **wykorzystania procesora CPU** pokazuje zmiany w użyciu procesora CPU we wszystkich rdzeniach procesora w sesji debugowania.

- Lista **Zdarzeń** w okienku szczegółów **debugera** zawiera elementy dla każdego zdarzenia przerwania.

- W kolumnie **Czas trwania** zdarzenia przerwania jest wyświetlany czas, jaki upłynął między zdarzeniem a poprzednim punktem przerwania.

## <a name="turn-perftips-on-or-off"></a>Włączanie lub wyłączanie etykietek perf
 Aby włączyć lub wyłączyć porady dotyczące perf:

1. W menu **Debugowanie** wybierz polecenie **Opcje**.

2. Zaznacz lub wyczyść **pole wyboru Pokaż perfTip podczas debugowania**.

## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Włączanie lub wyłączanie okna Narzędzia diagnostyczne
 Aby włączyć lub wyłączyć okno Narzędzia diagnostyczne:

1. W menu **Debugowanie** wybierz polecenie **Opcje**.

2. Zaznacz lub **wyczyść pozycję Włącz narzędzia diagnostyczne podczas debugowania**.

## <a name="see-also"></a>Zobacz też
- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
