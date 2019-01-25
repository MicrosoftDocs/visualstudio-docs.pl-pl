---
title: Pakiet debugowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dda8b1ac6eaa2cd5352d441600ae720c3aac321c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793819"
---
# <a name="debug-package"></a>Pakiet debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakiet debugowania jest uruchamiane w powłoce programu Visual Studio i obsługuje cały interfejs użytkownika. On wykorzystuje interfejsy debugowania programu Visual Studio i komunikuje się z usługą Menedżer debugowania sesji (SDM).  
  
 Zdarzenia przerwania wysyłane za pośrednictwem SDM Przełącz debugera w trybie uruchamiania tryb przerwania i zmianie fokusu do programu, w którym wystąpiło przerwanie. Debugowanie pakietu śledzi ramki stosu i wątku z informacje wysyłane do niej przez zdarzenia.  
  
 Debugowanie pakietu nie ma języka lub zależności środowiska uruchomieniowego. Nie jest niezbędne do wdrożenia lub zmodyfikować pakiet debugowania.  
  
 Debugowanie pakietu jest implementowany przez vsdebug.dll.  
  
## <a name="see-also"></a>Zobacz też  
 [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)   
 [Ramki stosu](../../extensibility/debugger/stack-frames.md)   
 [Wątki](../../extensibility/debugger/threads.md)   
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)
