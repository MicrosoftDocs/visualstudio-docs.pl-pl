---
title: IDebugPointerObject3::GetPointerAddress | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetPointerAddress
- IDebugPointerObject3::GetPointerAddress
ms.assetid: 4cc5af04-9e70-420d-8230-ef3108df6d51
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8b770bea631d772280b227b3298a45acee66e51
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777778"
---
# <a name="idebugpointerobject3getpointeraddress"></a>IDebugPointerObject3::GetPointerAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera adres wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetPointerAddress (  
   UINT64* puAddress  
);  
```  
  
```csharp  
int GetPointerAddress (  
   out ulong puAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `puAddress`  
 [out] Zwraca adres wskaźnika.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)
