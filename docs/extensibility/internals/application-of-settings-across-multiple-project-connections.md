---
title: Zastosuj ustawienia dla wielu połączeń projektów
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81448760f0417528fd630c4919ce516b32e518c8
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90034926"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Stosowanie ustawień w wielu połączeniach projektu
Wtyczka do kontroli źródła utworzona przy użyciu wtyczki kontroli źródła w wersji 1,2, może użyć operacji wsadowej do wykonania tej samej operacji kontroli źródła w wielu projektach lub wielu kontekstach połączenia. Partie mogą służyć do eliminowania nadmiarowych okien dialogowych dla projektu ze środowiska użytkownika.

 Jeśli użytkownik wybierze wiele elementów, które należą do więcej niż jednego połączenia w wtyczki kontroli źródła utworzonym przy użyciu interfejsu API dodatku plug-in kontroli źródła w wersji 1,1 (na przykład dwa projekty sieci Web na różnych maszynach udziałów plików) i sprawdza je, użytkownik zobaczy to samo okno dialogowe. Ten scenariusz występuje nawet wtedy, gdy użytkownik kliknie pole wyboru **Zastosuj do wszystkich** w oknie dialogowym, ponieważ IDE resetuje swój stan dla każdego kontekstu połączenia.

## <a name="new-capability-flag"></a>Nowa flaga możliwości
 `SccBeginBatch`Funkcja ustawia `SCC_CAP_BATCH` flagę, aby wskazać, że operacja wsadowa jest w toku.

## <a name="new-functions"></a>Nowe funkcje
Następujące nowe funkcje obsługują operację wsadową:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

`SCCBeginBatch`Funkcja uruchamia grupę operacji kontroli źródła. `SccEndBatch`Funkcja zamyka grupę. Grupy nie mogą być zagnieżdżane.

## <a name="see-also"></a>Zobacz także
- [Co nowego w interfejsie API dodatku plug-in kontroli źródła w wersji 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
