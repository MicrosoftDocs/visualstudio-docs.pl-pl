---
title: 'IEnumDebugModules2:: Clone | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Clone
helpviewer_keywords:
- IEnumDebugModules2::Clone
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5ee06d72c5b8dcf5e1d504a44e0306da957ccce3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161004"
---
# <a name="ienumdebugmodules2clone"></a>IEnumDebugModules2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zwraca kopię bieżącego wyliczenia jako oddzielny obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugModules2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugModules2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 określoną Zwraca kopię tego wyliczenia jako oddzielny obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kopia wyliczenia ma taki sam stan jak oryginał w momencie wywołania tej metody. Jednak kopia i stan pierwotny są oddzielone i mogą być zmieniane indywidualnie.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
