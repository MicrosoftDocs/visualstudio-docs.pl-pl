---
title: Kończenie pracy programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f0b9ad248751af0885fa4edc0275be2ede5ddd9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421866"
---
# <a name="terminating-a-program"></a>Kończenie programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniżej znajduje się opis zakończenia pojedynczego programu z jednym wątkiem.  
  
## <a name="termination-process"></a>Proces kończenia  
  
1. Element DE wysyła [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) z prawidłowym [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. Element DE wysyła [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) z prawidłowym [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   IDE przechodzi do trybu projektowania. Aparat debugowania lub środowisko uruchomieniowe wywołuje [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) w celu usunięcia programu z portu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
