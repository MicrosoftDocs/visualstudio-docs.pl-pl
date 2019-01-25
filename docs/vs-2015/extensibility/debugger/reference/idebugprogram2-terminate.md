---
title: IDebugProgram2::Terminate | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4673259e4a8ca0d4354037efbc35b63bedfcbc96
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799852"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kończy program.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
