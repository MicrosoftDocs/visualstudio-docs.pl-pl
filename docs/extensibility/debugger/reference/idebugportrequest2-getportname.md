---
description: Pobiera nazwę portu.
title: 'IDebugPortRequest2:: GetPortName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee0d0199a87dff6f29e82b691ed0a396f6d0162a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169252"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Pobiera nazwę portu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPortName( 
   BSTR* pbstrPortName
);
```

```csharp
int GetPortName( 
   out string pbstrPortName
);
```

## <a name="parameters"></a>Parametry
`pbstrPortName`\
określoną Zwraca nazwę portu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Interfejs [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) jest zwykle przesyłany z pakietu debugowania (klient) do dostawcy portu (serwera) w celu uzyskania połączenia z portem. Zarówno pakiet debugowania, jak i dostawca portów są świadomi możliwych wyborów dla portu. Jeśli prosty ciąg może opisywać port, `IDebugPortRequest2::GetPortName` Metoda zawiera wystarczające informacje, aby nawiązać połączenie. W przeciwnym razie dodatkowe interfejsy mogą być dostarczone przez klienta, który może zostać uzyskany przez serwer przy użyciu programu `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>Zobacz też
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
