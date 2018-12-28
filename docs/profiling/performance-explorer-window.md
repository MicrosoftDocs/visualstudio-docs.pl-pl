---
title: Okno Eksploratora wydajności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6077b17aa89754b3334bd6906a47e422bbd28ab
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684308"
---
# <a name="performance-explorer-window"></a>Okno Eksploratora wydajności

**Eksplorator wydajności** okna w środowisku IDE programu Visual Studio pozwala skonfigurować i uruchomić sesji wydajności przy użyciu programu Visual Studio Profiling Tools. Jeśli potrzebujesz otworzyć okno, postępuj zgodnie z instrukcjami wyświetlanymi w [początkujących przewodnik dotyczący profilowanie wydajności](../profiling/beginners-guide-to-cpu-sampling.md).

## <a name="performance-explorer-toolbar"></a>Pasek narzędzi Eksploratora wydajności

Poniższe opcje są dostępne na **Eksplorator wydajności** narzędzi:

- **Uruchom Kreatora wydajności** -wyświetla Kreatora wydajności w celu dodania nowej sesji wydajności w oknie Eksploratora wydajności.

- **Nowa sesja wydajności** — dodaje sesję wydajności puste okno Eksploratora wydajności.

- **Uruchom** — **Uruchom** polecenia Lista przycisk umożliwia uruchamianie aplikacji docelowej, która ma natychmiast włączono profilowanie (**Uruchom za pomocą profilowania**) lub za pomocą profilowania zawieszone ( **Wstrzymano uruchamiania za pomocą profilowania**).

- **Metoda** -Określa, czy metody profilowania sesji jest próbkowania i instrumentacji.

- **Zatrzymaj** — natychmiast kończy działanie aplikacji docelowej i profiler.

- **Dołącz/Odłącz** -Wyświetla **dołączyć Profiler do procesu** okno dialogowe Wybieranie uruchomionego procesu, dla której chcesz dołączyć program profilujący.

## <a name="performance-explorer-window"></a>Okno Eksploratora wydajności

**Eksplorator wydajności** okno zawiera formant drzewa, który wyświetla pliki binarne i pliki danych raportu z co najmniej jednej sesji wydajności.

- **Nazwa sesji** — główny drzewa zawiera nazwę sesji. Kliknij prawym przyciskiem myszy nazwę sesji, można ustawić właściwości sesji lub uruchomić aplikacji docelowej i programem profilującym.

- **Obiekty docelowe** -Wyświetla nazwy plików binarnych, które mają być profilowane w sesji. Kliknij prawym przyciskiem myszy **cele** Aby dodać lub usunąć plik binarny, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu lub witryny sieci Web. Kliknij prawym przyciskiem myszy nazwę docelowej, aby ustawić właściwości dla poszczególnych pliku binarnego.

- **Raporty** -Wyświetla nazwy plików danych profilera, które są generowane dla sesji. Kliknij prawym przyciskiem myszy **raporty** Dodawanie istniejącego raportu lub do porównywania dwóch plików danych profilera. Kliknij prawym przyciskiem myszy nazwę raportu, aby otworzyć, usunąć lub wyeksportować do pliku danych profilera.

## <a name="see-also"></a>Zobacz także

[Omówienia](../profiling/overviews-performance-tools.md)  
[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
[Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)