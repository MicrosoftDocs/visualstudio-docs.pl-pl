---
title: Dołączanie bezpośrednio do programu | Dokumentacja firmy Microsoft
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
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 01845979c838c065774aeab55abc9a1a2cfcde6c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773564"
---
# <a name="attaching-directly-to-a-program"></a>Dołączanie bezpośrednio do programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użytkownicy, którzy chcą do debugowania programów w procesie, który zazwyczaj jest już uruchomiony, wykonaj następujące czynności:  
  
1. W środowisku IDE, wybierz **debugowanie procesów** polecenia **narzędzia** menu.  
  
    **Procesy** pojawi się okno dialogowe.  
  
2. Wybierz proces, a następnie kliknij przycisk **Dołącz** przycisku.  
  
    **Dołączyć do procesu** pojawi się okno dialogowe, wyświetlanie listy wszystkich aparaty debugowania (DEs) zainstalowane na komputerze.  
  
3. Określ DEs na potrzeby debugowania wybranego procesu, a następnie kliknij przycisk **OK**.  
  
   Pakiet debugowania uruchamia sesję debugowania i przekazuje listę DEs do niego. Sesji debugowania z kolei przekazuje tej listy, wraz z funkcją wywołania zwrotnego do wybranego procesu, a następnie prosi procesu wyliczania jego uruchomione programy.  
  
   Programowe w odpowiedzi na żądanie użytkownika, debugowanie pakietu tworzy Menedżer debugowania sesji (SDM) i przekazuje listę wybranych DEs do niego. Wraz z listy, debugowanie pakietu przekazuje SDM [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfejsu. Debugowanie pakietu przekazuje listę DEs do wybranego procesu przez wywołanie metody [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Następnie wywołuje SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) na porcie wyliczyć programów uruchomionych w procesie.  
  
   Od tego momentu każdego silnika debugowania jest dołączony do programu dokładnie zgodnie z opisem w [dołączanie po Uruchom](../../extensibility/debugger/attaching-after-a-launch.md), z dwoma wyjątkami.  
  
   W celu zwiększenia wydajności DEs, które są wdrożone na udostępnianie przestrzeń adresową SDM są grupowane, aby każdy DE ma zestaw programów, które ma być dołączone do. W tym przypadku [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) wywołania [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) i przekazuje je tablicę programy można dołączyć do.  
  
   Drugi wyjątek to, że zdarzenia uruchamiania wysyłane przez DE, dołączając do programu, który jest już uruchomiony zwykle obejmuje zdarzenie punktu wejścia.  
  
## <a name="see-also"></a>Zobacz też  
 [Wysyłanie zdarzeń uruchamiania po uruchomieniu](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)

