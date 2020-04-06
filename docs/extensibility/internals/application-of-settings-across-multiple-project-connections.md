---
title: Stosowanie ustawień w wielu połączeniach projektu | Dokumenty firmy Microsoft
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
ms.openlocfilehash: bcaed0f7f2380dd36bcbffd776839025fe9efa16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710058"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Stosowanie ustawień w wielu połączeniach projektu
Wtyczka kontroli źródła zbudowana przy użyciu interfejsu API wtyczki kontroli źródła w wersji 1.2 może używać operacji wsadowej do wykonywania tej samej operacji kontroli źródła w wielu projektach lub w wielu kontekstach połączeń. Partie mogą służyć do wyeliminowania nadmiarowych okien dialogowych dla projektu z środowiska użytkownika.

 Jeśli użytkownik wybierze wiele elementów, które należą do więcej niż jednego połączenia w usłudze kontroli źródła wbudowanej przy użyciu interfejsu API wtyczki kontroli źródła w wersji 1.1 (na przykład dwa projekty sieci Web na różnych komputerach współużytkujących pliki) i wyewidencjonowuje je, użytkownik wielokrotnie widzi to samo okno dialogowe. W tym scenariuszu występuje, nawet jeśli użytkownik kliknie zastosuj **do wszystkich** pole wyboru w oknie dialogowym, ponieważ IDE resetuje swój stan dla każdego kontekstu połączenia.

## <a name="new-capability-flag"></a>Flaga nowych możliwości
 Funkcja `SccBeginBatch` ustawia `SCC_CAP_BATCH` flagę, aby wskazać, że operacja wsadowa jest w toku.

## <a name="new-functions"></a>Nowe funkcje
Następujące nowe funkcje obsługują operację wsadowego:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

Funkcja `SCCBeginBatch` uruchamia grupę operacji kontroli źródła. Funkcja `SccEndBatch` zamyka grupę. Grupy nie mogą być zagnieżdżone.

## <a name="see-also"></a>Zobacz też
- [Co nowego w interfejsie API wtyczki kontroli źródła w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
