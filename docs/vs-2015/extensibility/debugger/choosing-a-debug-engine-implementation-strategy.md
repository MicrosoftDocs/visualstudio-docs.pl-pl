---
title: Wybór strategii implementacji aparatu debugowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183470"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Wybieranie strategii implementacji aparatu debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj architektury czasu wykonywania, aby określić strategię implementacji aparatu debugowania (DE). Aparat debugowania może być utworzony w procesie w celu debugowania programu, przetwarzania w toku do Menedżera debugowania sesji programu Visual Studio (SDM) lub poza procesem do obu tych elementów. Poniższe wskazówki powinny pomóc w wyborze spośród tych trzech strategii.  
  
## <a name="guidelines"></a>Wytyczne  
 Chociaż istnieje możliwość, że stan "poza procesem" ma być debugowany, a program jest w stanie debugowania, zazwyczaj nie jest to konieczne. Wywołania między granicami procesu są stosunkowo wolne.  
  
 Aparaty debugowania są już udostępniane dla natywnego środowiska uruchomieniowego Win32 i dla środowiska CLR języka wspólnego. Jeśli konieczne jest zamienienie elementu DE dla dowolnego z tych środowisk, należy utworzyć w trakcie procesu w ramach modelu SDM.  
  
 W przeciwnym razie można wybrać opcję tworzenia w trakcie procesu w procesie do debugowania modelu SDM lub w procesie. Należy wziąć pod uwagę, czy ewaluatora wyrażeń dla wszystkich potrzeb często uzyskuje dostęp do magazynu symboli programu, oraz czy magazyn symboli może być ładowany do pamięci, aby uzyskać szybki dostęp. Rozważ również następujące elementy:  
  
- Jeśli nie ma wielu wywołań między ewaluatora wyrażeń i magazynem symboli, lub jeśli magazyn symboli można odczytać w przestrzeni pamięci modelu SDM, Utwórz w procesie proces do modelu SDM. Po dołączeniu do programu należy zwrócić identyfikator CLSID aparatu debugowania do modelu SDM. Model SDM używa tego identyfikatora CLSID do tworzenia wystąpienia w procesie dla DE.  
  
- Jeśli DE musi wywoływać program w celu uzyskania dostępu do magazynu symboli, należy utworzyć w trakcie procesu w programie. W takim przypadku program tworzy wystąpienie elementu DE.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
