---
title: IDebugProgram2::Terminate | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c4ef57e3cbc11eb6e1b8e266d1a0799ef46ba406
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872099"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Kończy program.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli to możliwe program zostanie zakończony i zwolnione z procesu; w przeciwnym razie aparat debugowania (DE) będzie wykonać wszelkie niezbędne czyszczenia.  
  
 Ta metoda lub [Zakończ](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) metoda jest wywoływana przez środowisko IDE, zwykle w odpowiedzi na użytkownika zatrzymywanie debugowania wszystkie. Implementacja tej metody w idealnym przypadku należy zakończyć program w ramach procesu. Jeśli nie jest to możliwe, DE powinien uniemożliwienie program dalszych w ramach tego procesu (i wykonaj wszelkie niezbędne czyszczenia). Jeśli `IDebugProcess2::Terminate` wywołano metodę IDE, cały proces zostanie zakończony jakiś czas po `IDebugProgram2::Terminate` metoda jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)