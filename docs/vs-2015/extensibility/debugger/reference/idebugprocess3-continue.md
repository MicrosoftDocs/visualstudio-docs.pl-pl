---
title: IDebugProcess3::Continue | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ae71aa79aba54b8954e309131f4b5e82357e1555
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817116"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kontynuuje, uruchomienie tego procesu w stanie zatrzymania. Dowolnego poprzedniego stanu wykonywania (np. krok) są zachowywane, a proces jest uruchamiany ponownie wykonywania.  
  
> [!NOTE]
>  Ta metoda powinna być używana zamiast [Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt reprezentujący wątek będzie kontynuowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana na temat tego procesu, niezależnie od tego, jak wiele procesów są debugowane lub proces, który wygenerował zdarzenie zatrzymywania. Wdrożenie musi zachować poprzedni stan wykonania (np. krok) i kontynuować wykonywanie, tak, jakby nigdy nie przestała się przed wykonaniem jego wcześniejszego wykonania. Oznacza to, jeśli wątek w ten proces wykonywanych operacji przejścia i została zatrzymana z powodu jakiś inny proces jest zatrzymana, a następnie `Continue` została wywołana, określonego wątku, należy wykonać operację przejścia.  
  
 **Ostrzeżenie** nie będą wysyłane zdarzenia zatrzymywania lub natychmiastowego zdarzeń (synchroniczne) [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może się zawiesić.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

