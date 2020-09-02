---
title: 'IDebugProcess3:: Continue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 92a36bb7e89d8afaa6d76f7d7b3772bd1714ffa7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386241"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kontynuuje wykonywanie tego procesu ze stanu zatrzymanego. Wszystkie poprzednie Stany wykonania (takie jak krok) są zachowywane i proces zostaje uruchomiony ponownie.  
  
> [!NOTE]
> Ta metoda powinna być używana zamiast [Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
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
 podczas Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) reprezentujący wątek, który ma być kontynuowany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana w tym procesie bez względu na liczbę debugowanych procesów lub proces wygenerował zdarzenie zatrzymania. Implementacja musi zachować poprzedni stan wykonania (na przykład krok) i kontynuować wykonywanie, tak jakby nigdy nie zostało zatrzymane przed ukończeniem jego wcześniejszego wykonania. Oznacza to, że jeśli wątek w tym procesie wykonywał operację krok po kroku i został zatrzymany, ponieważ jakiś inny proces został zatrzymany, a następnie `Continue` został wywołany, określony wątek musi wykonać pierwotną operację krok po kroku.  
  
 **Ostrzeżenie** Nie wysyłaj zdarzenia zatrzymania ani bezpośredniego (synchronicznego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może przestać odpowiadać.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
