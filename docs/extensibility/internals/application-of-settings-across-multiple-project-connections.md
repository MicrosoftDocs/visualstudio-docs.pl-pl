---
title: Zastosuj ustawienia dla wielu połączeń projektów
description: Dowiedz się, jak stosować ustawienia dla wielu połączeń projektów przy użyciu wtyczki kontroli źródła do wykonywania operacji wsadowych.
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
ms.openlocfilehash: cd5b7af98470c1d9a82eb0504c333e74de8c004f
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190112"
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

## <a name="see-also"></a>Zobacz też
- [Co nowego w interfejsie API dodatku plug-in kontroli źródła w wersji 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
