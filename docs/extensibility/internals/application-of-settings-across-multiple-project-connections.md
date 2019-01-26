---
title: Stosowanie ustawień do wielu połączeń projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d6810212b10052077ab5adeddbca69dbd5fb339
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976277"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Stosowanie ustawień do wielu połączeń projektu
Wtyczka do kontroli źródła utworzone przy użyciu źródła kontrolki wtyczki interfejsu API w wersji 1.2, można użyć operacji zbiorczej do wykonania tych samych operacji kontroli źródła, między wieloma projektami lub wielu kontekstach połączenia. Partie można wyeliminować nadmiarowy, okna dialogowe od środowiska użytkownika projektu.  
  
 Jeśli użytkownik umożliwia zaznaczenie wielu elementów, które należą do więcej niż jedno połączenie wtyczki kontroli źródła i utworzone przy użyciu źródła kontrolki wtyczki API wersji 1.1 (na przykład dwa projekty sieci web na maszynach inny udział plików) i sprawdza, czy je automatycznie, użytkownik zobaczy takie same okno dialogowe wielokrotnie. W tym scenariuszu występuje nawet wtedy, gdy użytkownik kliknie **Zastosuj do wszystkich** w oknie oknie dialogowym, ponieważ IDE resetuje stanu dla każdego kontekstu połączenia.  
  
## <a name="new-capability-flag"></a>Nową flagę funkcji  
 `SccBeginBatch` Funkcji zestawy `SCC_CAP_BATCH` flagi, aby wskazać, że trwa wykonywanie operacji przetwarzania wsadowego.  
  
## <a name="new-functions"></a>Nowe funkcje  
Następujące nowe funkcje obsługi operacji zbiorczej:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  

  
`SCCBeginBatch` Funkcja rozpoczyna grupy operacji kontroli źródła. `SccEndBatch` Funkcja zamyka grupy. Grupy nie mogą być zagnieżdżone.  
  
## <a name="see-also"></a>Zobacz także  
 [What's new in źródła kontrolki wtyczki API wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)