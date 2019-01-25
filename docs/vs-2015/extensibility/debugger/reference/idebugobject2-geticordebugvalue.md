---
title: IDebugObject2::GetICorDebugValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6fdf426058390aef2a0c8abf2590123572bbc3b1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758870"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera obiekt zarządzany kod reprezentujący wartość skojarzoną z tym obiektem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppUnk`  
 [out] `IUnknown` interfejs, który reprezentuje ten alias. Ten interfejs może być odpytywany dla `ICorDebugValue` interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugValue` Obiektu jest interfejsem środowiska uruchomieniowego języka wspólnego, który reprezentuje wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
