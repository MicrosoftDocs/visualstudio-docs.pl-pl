---
title: IDebugFunctionPosition2::GetOffset | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2::GetOffset
helpviewer_keywords:
- IDebugFunctionPosition2::GetOffset
ms.assetid: 60943782-aec7-4be2-b222-1984ed53a543
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecff2d4bc287cb4ece9989dc3ed371c7786264e2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788520"
---
# <a name="idebugfunctionposition2getoffset"></a>IDebugFunctionPosition2::GetOffset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera pozycję funkcji w dokumencie źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetOffset(   
   TEXT_POSITION* pPosition  
);  
```  
  
```csharp  
int GetOffset(  
   TEXT_POSITION[] pPosition  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pPosition`  
 [out w] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) strukturę, która jest wypełniane pozycję funkcji w dokumencie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
