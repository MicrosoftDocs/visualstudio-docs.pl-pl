---
title: 'IDebugModuleLoadEvent2:: GetModule | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0083946051fe78fc1bd19ea877475465e0b6477f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163419"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera moduł, który jest ładowany lub zwolniony.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pModule`  
 określoną Zwraca obiekt [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , który reprezentuje moduł, który jest ładowany lub zwalnia.  
  
 `pbstrDebugMessage`  
 [in. out] Zwraca opcjonalny komunikat opisujący to zdarzenie. Jeśli ten parametr jest wartością null, nie jest wymagany żaden komunikat.  
  
 `pbLoad`  
 [in. out] Różna od zera ( `TRUE` ), jeśli moduł jest ładowany i zero ( `FALSE` ), jeśli moduł zostanie wyładowany. Jeśli ten parametr ma wartość null, nie jest wymagany żaden stan.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
