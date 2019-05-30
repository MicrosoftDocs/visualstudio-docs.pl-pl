---
title: IDebugPortRequest2::GetPortName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e8017237af68b3dc414dc64bf6ae077387f0a600
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340382"
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
[out] Zwraca nazwę portu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interfejsu jest zwykle przekazywany z pakietu debugowania (klienta) do dostawcy portu (serwera), można uzyskać połączenia do portu. Zarówno pakietu debugowania, jak i dostawcy portu sobie sprawę z możliwych opcji dla portu. Jeśli prosty ciąg opisujący portu, a następnie `IDebugPortRequest2::GetPortName` metoda ma za mało informacji do nawiązania połączenia. W przeciwnym razie można podać dodatkowe interfejsy przez klienta, który można uzyskać za pomocą serwera `IDebugPortRequest2::QueryInterface`.

## <a name="see-also"></a>Zobacz także
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)