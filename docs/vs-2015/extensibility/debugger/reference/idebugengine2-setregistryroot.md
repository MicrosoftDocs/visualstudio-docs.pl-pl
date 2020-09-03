---
title: 'IDebugEngine2:: SetRegistryRoot | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39bb532301d34a3abf9988cfa909e1606c3c73e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195946"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ustawia katalog główny rejestru dla aparatu debugowania (Niemcy).  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszRegistryRoot`  
 podczas Katalog główny rejestru do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pozwala [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] określić alternatywny katalog główny rejestru, który powinien być używany do uzyskiwania ustawień rejestru, na przykład "HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0Exp".  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
