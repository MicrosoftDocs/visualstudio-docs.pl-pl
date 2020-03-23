---
title: Mierzenie wydajności kodu języka Python
description: Użyj profilera programu Visual Studio, aby sprawdzić wydajność kodu języka Python podczas korzystania z interpreterów opartych na CPython.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e31286a9b0ea3852ad1fe788d4ff6c4c66e7e4f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784286"
---
# <a name="profile-python-code"></a>Profil Kod Pythona

Można profilować aplikację Języka Python podczas korzystania z interpreterów opartych na CPython. (Zobacz [funkcje macierzy — profilowanie](overview-of-python-tools-for-visual-studio.md#matrix-profiling) dostępności tej funkcji dla różnych wersji programu Visual Studio.)

## <a name="profiling-for-cpython-based-interpreters"></a>Profilowanie dla tłumaczy na podstawie CPython

Profilowanie jest uruchamiane za pomocą polecenia menu > **Analizuj uruchamianie profilowania języka Python,** które otwiera okno dialogowe konfiguracji: **Analyze**

![Okno dialogowe konfiguracji profilowania](media/profiling-start.png)

Po wybraniu **przycisku OK**profiler uruchamia i otwiera raport wydajności, za pomocą którego można zbadać, jak czas spędza się w aplikacji:

![Profilowanie raportu o skuteczności](media/profiling-results.png)

> [!Note]
> Obecnie visual studio obsługuje tylko ten poziom profilowania pełnej aplikacji, ale z pewnością chcemy usłyszeć opinie na temat przyszłych możliwości. Użyj przycisku **Opinie o produkcie** u dołu tej strony.

## <a name="profiling-for-ironpython"></a>Profilowanie ironpython

Ponieważ IronPython nie jest interpreterem opartym na CPython, powyższa funkcja profilowania nie działa.

Zamiast tego należy użyć visual studio .NET profiler uruchamiając *ipy.exe* bezpośrednio jako aplikacji docelowej, przy użyciu odpowiednich argumentów, aby uruchomić skrypt startowy. Dołącz `-X:Debug` do wiersza polecenia, aby upewnić się, że cały kod języka Python może być debugowany i profilowane. Ten argument generuje raport wydajności, w tym czas spędzony zarówno w czasie wykonywania IronPython i kodu. Kod jest identyfikowany przy użyciu zniekształconych nazw.

Alternatywnie, IronPython ma niektóre z własnych wbudowanych profilowania, ale obecnie nie ma dobrego wizualizatora dla niego. Informacje na temat dostępnych informacji można znaleźć w programie [IronPython Profiler](https://blogs.msdn.microsoft.com/curth/2009/03/30/an-ironpython-profiler/) (blogi MSDN).
