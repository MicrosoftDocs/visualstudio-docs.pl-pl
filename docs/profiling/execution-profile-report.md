---
title: Raport profilu wykonania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25886ad4f7c31ea02c8dab2d45d8709a362a5a69
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969995"
---
# <a name="execution-profile-report"></a>Raport profilu wykonania
Raport profilu wykonania jest tradycyjnym profilem próbkowania. Próbki są pobierane w przybliżeniu co milisekundę w okresach, gdy wątek jest uruchomiony na rdzeniu logicznym, a wizualizator współbieżności tworzy typowe drzewo wywołań przez zestawienie skumulowanego zestawu stosów próbek. Na dane w tej tabeli może mieć wpływ bieżący zakres czasu i ukryte wątki oraz te filtry, które mogą zostać zastosowane:

- Jeśli zaznaczona jest opcja Tylko mój kod, wyświetlane są tylko ramki stosu, które mają kod użytkownika oraz jeden poziom poniżej kodu użytkownika.

- Jeśli ustawiona jest wartość redukcji szumów, zestawione stosy, które mają mniej niż określoną częstotliwość, są filtrowane z raportu

  W poniższej tabeli przedstawiono kolumny w raporcie.

|Kolumna|Opis|
|------------|-----------------|
|Nazwa|Nazwa funkcji dla każdego poziomu stosu wywołań.|
|Próbki włączające|Całkowita liczba próbek, które są zbierane dla wszystkich stosów, które są rzutowania do tego poziomu drzewa stosu wywołań. Liczba włącznie jest sumą próbek wyłącznych dla tej funkcji i liczników włącznie dla wszystkich węzłów podrzędnych.|
|Ekskluzywne próbki|Całkowita liczba pobranych próbek, dla których ta funkcja jest najniższy poziom stosu wywołań.|
|% włącznie|Procent całkowitej liczby próbek, który jest wyświetlany w kolumnie przykłady włącznie. Wartości procentowe są zaokrąglane do dwóch miejsc po przecinku.|
|% wyłączności|Procent całkowitej liczby próbek, który jest wyświetlany w kolumnie próbki wyłączności. Wartości procentowe są zaokrąglane do dwóch miejsc po przecinku.|
|Szczegóły|W pełni kwalifikowana nazwa funkcji. Obejmuje to liczbę wierszy, gdy jest ona dostępna.|

 Ta tabela raportu można zobaczyć w czasie [wykonywania (widok wątków)](../profiling/execution-time-threads-view.md) widok.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)