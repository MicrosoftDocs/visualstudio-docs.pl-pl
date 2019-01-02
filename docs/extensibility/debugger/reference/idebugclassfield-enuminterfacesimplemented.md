---
title: IDebugClassField::EnumInterfacesImplemented | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a58914186b09fe25fe67c8c6f914d3515615bd2a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871047"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Tworzy moduł wyliczający interfejsy implementowane przez tę klasę.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listy interfejsów implementowanych. Zwraca wartość null, jeśli brak interfejsów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli żadne interfejsy implementowane w tej klasie. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Każdy element wyliczenia jest [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Obiekt opisujący interfejs. Należy zauważyć, że niezarządzane [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] kod nie używa interfejsów jako osobne jednostki, ta metoda zawsze zwraca wartość null dla niezarządzanych [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)