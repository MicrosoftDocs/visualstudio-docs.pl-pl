---
title: IDebugPortSupplier2::GetPortSupplierId | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPortSupplierId
helpviewer_keywords:
- IDebugPortSupplier2::GetPortSupplierId
ms.assetid: 741d0829-0943-49bf-b56e-61e836043006
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d9b8e1db99727427e18a12b5d159c61212f706be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188260"
---
# <a name="idebugportsupplier2getportsupplierid"></a>IDebugPortSupplier2::GetPortSupplierId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera identyfikator dostawcy portów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetPortSupplierId(   
   GUID* pguidPortSupplier  
);  
```  
  
```csharp  
HRESULT GetPortSupplierId(   
   out Guid pguidPortSupplier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pguidPortSupplier`  
 [out] Zwraca identyfikator GUID dostawcy portu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
