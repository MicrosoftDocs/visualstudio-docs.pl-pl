---
title: Załącznik z systemem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09a6b39bef9ba6af098bf92d779a490e22492209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203166"
---
# <a name="launch-based-attachment"></a>Dołączanie na podstawie uruchamiania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Przymocowanie na podstawie uruchamiania do programu jest automatyczne. Gdy proces hostujący program jest uruchamiany przez model SDM, przystawka na podstawie uruchamiania następuje po ścieżce podobnej do metody ręcznego załączników. Aby uzyskać więcej informacji, zobacz [dołączanie do programu](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Proces dołączania  
 Główną różnicą jest sekwencja zdarzeń po wywołaniu **Attach** w następujący sposób:  
  
1. Wyślij obiekt zdarzenia **IDebugEngineCreateEvent2** do modelu SDM. Aby uzyskać szczegółowe informacje, zobacz [wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).  
  
2. Wywołaj `IDebugProgram2::GetProgramId` metodę w interfejsie **IDebugProgram2** przekazaną do metody **Attach** .  
  
3. Wyślij obiekt zdarzenia **IDebugProgramCreateEvent2** , aby powiadomić model SDM, że lokalny obiekt **IDebugProgram2** został utworzony, aby reprezentować program do de.  
  
4. Wyślij obiekt zdarzenia [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) , aby powiadomić model SDM o utworzeniu nowego wątku dla uruchomionego procesu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wysyłanie wymaganych zdarzeń](../../extensibility/debugger/sending-the-required-events.md)   
 [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
