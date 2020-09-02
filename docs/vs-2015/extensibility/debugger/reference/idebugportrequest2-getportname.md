---
title: 'IDebugPortRequest2:: GetPortName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: afed0bb700f41f7c39551f1a9bc7779f36b0ae57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188365"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera nazwę portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrPortName`  
 określoną Zwraca nazwę portu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Interfejs [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) jest zwykle przesyłany z pakietu debugowania (klient) do dostawcy portu (serwera) w celu uzyskania połączenia z portem. Zarówno pakiet debugowania, jak i dostawca portów są świadomi możliwych wyborów dla portu. Jeśli prosty ciąg może opisywać port, `IDebugPortRequest2::GetPortName` Metoda zawiera wystarczające informacje, aby nawiązać połączenie. W przeciwnym razie dodatkowe interfejsy mogą być dostarczone przez klienta, który może zostać uzyskany przez serwer przy użyciu programu `IDebugPortRequest2::QueryInterface` .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
