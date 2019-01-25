---
title: Stosowanie ustawień do wielu połączeń projektu | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54833904"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Stosowanie ustawień do wielu połączeń projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wtyczka do kontroli źródła utworzone przy użyciu 1.2 interfejsu API wtyczki kontroli źródła, można użyć operacji zbiorczej do wykonania tych samych operacji kontroli źródła, między wieloma projektami lub wielu kontekstach połączenia. Partie można wyeliminować nadmiarowy, okna dialogowe od środowiska użytkownika projektu.  
  
 Jeśli użytkownik umożliwia zaznaczenie wielu elementów, które należą do więcej niż jedno połączenie wtyczki kontroli źródła i utworzone przy użyciu 1.1 interfejsu API wtyczki kontroli źródła o (na przykład dwa projekty sieci Web na maszynach inny udział plików) i sprawdza, czy je automatycznie, użytkownik zobaczy okno dialogowe w tym samym wielokrotnie. Dzieje się tak nawet wtedy, gdy użytkownik kliknie **Zastosuj do wszystkich** w oknie oknie dialogowym, ponieważ IDE resetuje stanu dla każdego kontekstu połączenia.  
  
## <a name="new-capability-flag"></a>Nową flagę funkcji  
 `SccBeginBatch` Funkcja ustawia `SCC_CAP_BATCH` flagi, aby wskazać, że trwa wykonywanie operacji wsadowych  
  
## <a name="new-functions"></a>Nowe funkcje  
 Następujące nowe funkcje obsługi operacji zbiorczej:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  `SCCBeginBatch` Funkcja rozpoczyna grupy operacji kontroli źródła. `SccEndBatch` Zamyka grupy. Grupy nie mogą być zagnieżdżone.  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
