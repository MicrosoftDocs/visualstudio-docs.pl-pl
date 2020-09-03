---
title: 'IEnumDebugAddresses:: GetCount | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f90d1a24a084d054e612e3257b9009d4615deb06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191963"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda zwraca liczbę elementów w wyliczeniu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcelt`  
 określoną Zwraca liczbę elementów w wyliczeniu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest częścią niestandardowego interfejsu wyliczania modelu COM, który określa, że należy zaimplementować tylko następne, klonowanie, pomijanie i resetowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
