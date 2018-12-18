---
title: Dołączanie na podstawie uruchamiania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c3d361d9e8b99467e0a8a131e9d30be5db30b9d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792453"
---
# <a name="launch-based-attachment"></a>Dołączanie na podstawie uruchamiania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Na podstawie uruchamiania załącznika do programu odbywa się automatycznie. Podczas procesu hostingu program jest uruchamiany przez SDM, na podstawie uruchamiania załącznika poniżej ścieżką podobną do tej metody ręcznego załącznika. Aby uzyskać informacje, zobacz [dołączanie do programu](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Dołączanie procesu  
 Główna różnica polega na sekwencję zdarzeń po **Dołącz** wywołań w następujący sposób:  
  
1.  Wyślij **IDebugEngineCreateEvent2** obiekt zdarzenia do SDM. Aby uzyskać więcej informacji, zobacz [wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).  
  
2.  Wywołania `IDebugProgram2::GetProgramId` metody **IDebugProgram2** interfejsu przekazany do **Dołącz** metody.  
  
3.  Wyślij **IDebugProgramCreateEvent2** zdarzeń obiektowi powiadomić SDM, lokalnej **IDebugProgram2** do reprezentowania program DE został utworzony obiekt.  
  
4.  Wyślij [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) obiektu zdarzenia, aby powiadomić SDM, utworzenia nowego wątku dla procesu, który uruchomił.  
  
## <a name="see-also"></a>Zobacz też  
 [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md)   
 [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

