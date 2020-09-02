---
title: 'IDebugAddress:: GetAddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d3263ca020f491e0c1cf20ee49792cacfbc362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186686"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zwraca strukturę opisującą obiekt i jego lokalizację w zakresie lub kontenerze.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [in. out] Struktura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) , która jest wypełniana przez tę metodę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Struktura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) jest przenoszona do tej metody, a następnie wypełnia ją odpowiednimi informacjami. Sposób interpretacji tych informacji zależy od rodzaju zwracanych informacji oraz od samego programu obsługi symboli. Aby uzyskać więcej informacji, zobacz [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
