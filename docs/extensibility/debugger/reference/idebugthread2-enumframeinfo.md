---
title: IDebugThread2::EnumFrameInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b329dd0c7a1ef7451a40d36ecbb10690e7b70ca3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956535"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Pobiera listę ramek stosu dla tego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFieldSpec`  
 [in] Kombinacja flag z [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) wyliczenie, które określa, które pola [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury są do wypełniania. Określ `FIF_FUNCNAME_FORMAT` flagi do formatowania nazwy funkcji w jeden ciąg.  
  
 `nRadix`  
 [in] Podstawy używanych w formatowaniu wartości liczbowych informacji w moduł wyliczający.  
  
 `ppEnum`  
 [out] Zwraca [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) obiekt, który zawiera listę [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury opisujące ramki stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ramki dla wątku są wyliczane w kolejności, przy użyciu bieżącej ramki wyliczane najpierw i najstarsze ramki wyliczane ostatnio.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)