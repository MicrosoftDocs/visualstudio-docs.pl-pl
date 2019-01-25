---
title: IDebugProcess2::GetProcessId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f500f06178ae98c0426c08b9cca0320c01d860d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790822"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera identyfikator GUID dla tego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```csharp  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pguidProcessId`  
 [out] Zwraca identyfikator GUID dla tego procesu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Globalnie unikatowy identyfikator (GUID) identyfikuje ten proces z innych procesów w systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
