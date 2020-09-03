---
title: 'IDebugProgramDestroyEventFlags2:: GetFlags | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetFlags
- IDebugProgramDestroyEventFlags2::GetFlags
ms.assetid: dd53bd0c-459a-4077-ba81-780defb71e87
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 01401c14dde9ca0d4e76a9743464b42ebba2937d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182193"
---
# <a name="idebugprogramdestroyeventflags2getflags"></a>IDebugProgramDestroyEventFlags2::GetFlags
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera flagi niszczenia programów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetFlags(  
   PROGRAM_DESTROY_FLAGS* pdwFlags  
);  
```  
  
```csharp  
public int GetFlags(  
   out enum_PROGRAM_DESTROY_FLAGS pdwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwFlags`  
 określoną Reprezentuje flagi niszczenia programów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)   
 [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md)
