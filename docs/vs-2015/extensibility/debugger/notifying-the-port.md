---
title: Powiadamianie portu | Dokumentacja firmy Microsoft
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
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3cfcc4ee357301aa0e38468b13b983c3d5ca55a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763375"
---
# <a name="notifying-the-port"></a>Powiadamianie portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po uruchomieniu programu, numer portu musi być powiadomiony, w następujący sposób:  
  
1. Gdy port otrzymuje nowy węzeł program, wysyła zdarzenie tworzenia programu do sesji debugowania. Zdarzenie niesie ze sobą interfejs, który reprezentuje program.  
  
2. Program dla identyfikatora aparat debugowania (DE), który można dołączyć do wysyła zapytanie do sesji debugowania.  
  
3. Sesja debugowania sprawdza, czy DE na liście dopuszczalnych DEs dla tego programu. Sesja debugowania pobiera tej listy z aktywnym programem ustawień rozwiązania pierwotnie przekazana do niej przy użyciu pakietu debugowania.  
  
    DE musi znajdować się na liście dopuszczalny rozmiar, w przeciwnym razie DE nie zostanie dołączony do programu.  
  
   Programowo, gdy port otrzymuje najpierw nowego węzła programu, tworzy [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfejsu do reprezentowania program.  
  
> [!NOTE]
>  To nie należy mylić z `IDebugProgram2` interfejsu utworzone później przez aparat debugowania (DE).  
  
 Port wysyła [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzenie tworzenia programu do Menedżer debugowania sesji (SDM) za pomocą COM `IConnectionPoint` interfejsu.  
  
> [!NOTE]
>  To nie należy mylić z `IDebugProgramCreateEvent2` interfejsu, która jest wysyłana później przez DE.  
  
 Wraz z samego interfejsu do zdarzenia, wysyła port [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), i [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfejsów, które reprezentują port, przetwarzania, i Program, odpowiednio. Wywołania SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) można pobrać identyfikatora GUID DE, który można debugować program. Identyfikator GUID początkowo zostały pobrane z [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu.  
  
 SDM sprawdza, czy DE na liście dopuszczalnych DEs. SDM pobiera tej listy z aktywnym programem ustawień rozwiązania pierwotnie przekazana do niej przy użyciu pakietu debugowania. DE musi znajdować się na liście dopuszczalny rozmiar, w przeciwnym razie nie można dołączyć do programu.  
  
 Tożsamość DE jest znany, SDM po chcesz dołączyć do programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)   
 [Dołączanie po uruchomieniu](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)

