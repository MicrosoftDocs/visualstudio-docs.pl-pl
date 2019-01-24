---
title: IDebugProcess2::Detach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8bbbebc76d8301bd4632f95f8832ee657a3bce46
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801932"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Odłącza debuger z tego procesu przez odłączenie wszystkich programów w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie programy i proces nadal działa, ale nie są już częścią sesji debugowania. Operacja odłączenia po pełne, nie ma więcej debugowania, który będą wysyłane zdarzenia dla tego procesu (i jego programów).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
