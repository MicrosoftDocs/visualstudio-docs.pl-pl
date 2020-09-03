---
title: Debuguj pakiet | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181291"
---
# <a name="debug-package"></a>Pakiet debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakiet debugowania działa w programie Visual Studio Shell i obsługuje cały interfejs użytkownika. Korzysta ona z interfejsów debugowania programu Visual Studio i komunikuje się z menedżerem debugowania sesji (SDM).  
  
 Zdarzenia przerwania wysyłane przez model SDM przełączają debuger z trybu uruchamiania do trybu przerwania i zmieniają fokus w programie, w którym wystąpiła przerwanie. Pakiet debugowania śledzi ramkę stosu i wątek z informacji wysyłanych do niego przez zdarzenia.  
  
 Pakiet debugowania nie ma zależności w języku ani środowisku czasu wykonywania. Nie trzeba implementować ani modyfikować pakietu debugowania.  
  
 Pakiet debugowania jest implementowany przez vsdebug.dll.  
  
## <a name="see-also"></a>Zobacz też  
 [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)   
 [Ramki stosu](../../extensibility/debugger/stack-frames.md)   
 [Wątk](../../extensibility/debugger/threads.md)   
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)
