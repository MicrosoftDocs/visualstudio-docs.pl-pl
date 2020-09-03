---
title: 'IDebugProgram2:: Execute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 676a3a7d184c1f34cafcfc2b2a4dd7a1c3f81a95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387333"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kontynuuje działanie tego programu ze stanu zatrzymanego. Wszystkie poprzednie Stany wykonania (takie jak krok) są wyczyszczone, a program ponownie uruchamia wykonywanie.  
  
> [!NOTE]
> Ta metoda jest przestarzała. Zamiast tego użyj metody [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy użytkownik uruchamia wykonywanie z stanu zatrzymanego w innym wątku programu, ta metoda jest wywoływana w tym programie. Ta metoda jest również wywoływana, gdy użytkownik wybierze polecenie **Uruchom** z menu **DEBUGUJ** w środowisku IDE. Implementacja tej metody może być prosta jako wywołanie metody [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) w bieżącym wątku w programie.  
  
> [!WARNING]
> Nie wysyłaj zdarzenia zatrzymania ani bezpośredniego (synchronicznego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może przestać odpowiadać.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Wydarzen](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Wznawianie](../../../extensibility/debugger/reference/idebugthread2-resume.md)
