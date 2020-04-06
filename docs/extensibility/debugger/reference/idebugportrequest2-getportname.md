---
title: IDebugPortRequest2::GetPortName | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67121e98f2d506aa16c2b4dc3fff2ad5128fb93b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724813"
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
[na zewnątrz] Zwraca nazwę portu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Interfejs [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) jest zwykle przekazywany z pakietu debugowania (klienta) do dostawcy portu (serwera) w celu uzyskania połączenia z portem. Zarówno pakiet debugowania, jak i dostawca portu są świadomi możliwych wyborów dla portu. Jeśli prosty ciąg można opisać port, a następnie metoda ma wystarczającą `IDebugPortRequest2::GetPortName` ilość informacji, aby nawiązać połączenie. W przeciwnym razie klient może dostarczyć dodatkowe interfejsy, które `IDebugPortRequest2::QueryInterface`mogą uzyskać serwer za pomocą programu .

## <a name="see-also"></a>Zobacz też
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
