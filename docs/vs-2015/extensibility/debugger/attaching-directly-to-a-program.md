---
title: Dołączanie bezpośrednio do programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab49163fc1474b541df3bc1b54d336574761baa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147996"
---
# <a name="attaching-directly-to-a-program"></a>Dołączanie bezpośrednio do programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użytkownicy, którzy chcą debugować programy w procesie, który jest już uruchomiony, zwykle wykonują ten proces:  
  
1. W środowisku IDE wybierz polecenie **Debuguj procesy** z menu **Narzędzia** .  
  
    Zostanie wyświetlone okno dialogowe **procesy** .  
  
2. Wybierz proces i kliknij przycisk **Dołącz** .  
  
    Zostanie wyświetlone okno dialogowe **Dołącz do procesu** z listą wszystkich aparatów debugowania (des) zainstalowanych na komputerze.  
  
3. Określ algorytm DEs, który ma być używany do debugowania wybranego procesu, a następnie kliknij przycisk **OK**.  
  
   Pakiet debugowania uruchamia sesję debugowania i przekazuje do niej listę DEs. Sesja debugowania z kolei przekazuje tę listę wraz z funkcją wywołania zwrotnego do wybranego procesu, a następnie prosi proces o Wyliczenie jego uruchomionych programów.  
  
   Programowo, w odpowiedzi na żądanie użytkownika, pakiet debugowania tworzy wystąpienie Menedżera debugowania sesji (SDM) i przekazuje listę wybranych dla niego algorytmu DEs. Wraz z listą pakiet debugowania przekazuje interfejs SDM [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) . Pakiet debugowania przekazuje listę DEs do wybranego procesu przez wywołanie [IDebugProcess2:: Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Model SDM następnie wywołuje [IDebugProcess2:: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) na porcie w celu wyliczenia programów uruchomionych w procesie.  
  
   Od tego momentu każdy aparat debugowania jest dołączany do programu dokładnie tak, jak opisano w temacie [dołączanie po uruchomieniu](../../extensibility/debugger/attaching-after-a-launch.md), z dwoma wyjątkami.  
  
   Ze względu na wydajność algorytm DEs wdrożony w celu udostępnienia przestrzeni adresowej z modelem SDM jest grupowany, dzięki czemu każda z nich ma zestaw programów, do których zostanie dołączona. W tym przypadku [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) wywołuje [IDebugEngine2:: dołączanie](../../extensibility/debugger/reference/idebugengine2-attach.md) i przekazanie do niego tablicy programów do dołączenia.  
  
   Drugi wyjątek polega na tym, że zdarzenia uruchamiania wysyłane przez DE dołączenia do programu, który jest już uruchomiony, zazwyczaj nie obejmują zdarzenia punktu wejścia.  
  
## <a name="see-also"></a>Zobacz też  
 [Wysyłanie zdarzeń uruchamiania po uruchomieniu](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
