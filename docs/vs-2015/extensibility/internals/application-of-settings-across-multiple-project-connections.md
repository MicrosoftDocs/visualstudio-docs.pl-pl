---
title: Stosowanie ustawień dla wielu połączeń projektów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bca17fdc440fc373d0d4811ed57cd5d27a6c201a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203848"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Stosowanie ustawień do wielu połączeń projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wtyczka do kontroli źródła utworzona przy użyciu interfejsu API dodatku plug-in kontroli źródła 1,2, może użyć operacji wsadowej do wykonania tej samej operacji kontroli źródła w wielu projektach lub wielu kontekstach połączenia. Partie mogą służyć do eliminowania nadmiarowych okien dialogowych dla projektu ze środowiska użytkownika.  
  
 Jeśli użytkownik wybierze wiele elementów, które należą do więcej niż jednego połączenia w wtyczki kontroli źródła utworzonym przy użyciu wtyczki kontroli źródła w interfejsie API 1,1 (na przykład dwa projekty sieci Web na różnych maszynach udziałów plików) i sprawdza je, użytkownik zobaczy to samo okno dialogowe. Dzieje się tak nawet wtedy, gdy użytkownik kliknie pole wyboru **Zastosuj do wszystkich** w oknie dialogowym, ponieważ IDE resetuje swój stan dla każdego kontekstu połączenia.  
  
## <a name="new-capability-flag"></a>Nowa flaga możliwości  
 `SccBeginBatch` Funkcja ustawia `SCC_CAP_BATCH` flagę wskazującą, że operacja wsadowa jest w toku  
  
## <a name="new-functions"></a>Nowe funkcje  
 Następujące nowe funkcje obsługują operację wsadową:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  `SCCBeginBatch`Funkcja uruchamia grupę operacji kontroli źródła. `SccEndBatch` zamyka grupę. Grupy nie mogą być zagnieżdżane.  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
