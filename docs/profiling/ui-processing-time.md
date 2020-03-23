---
title: Czas przetwarzania interfejsu użytkownika | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 391b4582d03e32e738f0eade823326e72a662a43
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "63004454"
---
# <a name="ui-processing-time"></a>Czas przetwarzania interfejsu użytkownika
Te segmenty na osi czasu są skojarzone z czasami blokowania, które są klasyfikowane jako przetwarzanie interfejsu użytkownika. Oznacza to, że wątek pompuje komunikaty systemu Windows lub wykonuje pracę innego interfejsu użytkownika.This implies that a thread is pumping Windows messages or performing other user interface (UI) work. W tym czasie wątek został zablokowany w interfejsie API, który wizualizator współbieżności jest zliczanie jako przetwarzanie interfejsu użytkownika. Interfejsy API, `GetMessage()` `MsgWaitForMultipleObjects()` takie jak i należą do tej grupy.

 Jeśli nie zdefiniowano wstępnie zdefiniowanego interfejsu API blokowania, przejrzyj stosy wywołań i raporty profilu, aby określić podstawowe przyczyny opóźnienia.

 Kategoria Przetwarzanie interfejsu użytkownika pomaga zrozumieć szybkość reakcji aplikacji gui i jest pożądane w aplikacjach, które zależą od reakcji interfejsu użytkownika. Na przykład jeśli wątek interfejsu użytkownika w aplikacji osiąga 100% czasu w przetwarzaniu interfejsu użytkownika, prawdopodobnie jest responsywny. Jeśli jednak wątek interfejsu użytkownika spędza dużo czasu w innych kategoriach, poszukaj przyczyn źródłowych i rozważ opcje zmniejszania kategorii innych niż interfejsu użytkownika w tym wątku.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)