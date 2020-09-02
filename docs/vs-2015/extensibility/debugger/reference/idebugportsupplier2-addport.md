---
title: 'IDebugPortSupplier2:: AddPort | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf5bf281e794bde04ae0c2e86c6d27edb7edc5a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188298"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Dodaje port.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```csharp  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRequest`  
 podczas Obiekt [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) , który opisuje port, który ma zostać dodany.  
  
 `ppPort`  
 określoną Zwraca obiekt [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , który reprezentuje port.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda w rzeczywistości tworzy żądany port, a także dodaje go do wewnętrznej listy aktywnych portów dostawcy portów. Metodę [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) można wywołać w pierwszej kolejności, aby uniknąć potencjalnych czasochłonnych opóźnień.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
