---
title: IEnumCodePaths2::Clone | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2::Clone
helpviewer_keywords:
- IEnumCodePaths2::Clone
ms.assetid: 9d5c6bc6-7e72-4f1b-801c-7192458f3ba8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8dd02f49b7865bf92cce2f6cd5e48fdf8992b27
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863751"
---
# <a name="ienumcodepaths2clone"></a>IEnumCodePaths2::Clone
Zwraca kopię bieżącego wyliczenia jako oddzielny obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Clone(  
   IEnumCodePaths2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumCodePaths2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca kopię tego wyliczenia jako oddzielny obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kopię wyliczenia ma ten sam stan, co oryginalny w czasie, którego ta metoda jest wywoływana. Jednak stany kopiowania i oryginalne są niezależne i można zmieniać indywidualnie.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)