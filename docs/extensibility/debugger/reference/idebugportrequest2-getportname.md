---
title: IDebugPortRequest2::GetPortName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8663e9e7d8c0428b362bbdbb099141ac86d01ee1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918084"
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

#### <a name="parameters"></a>Parametry
 `pbstrPortName`

 [out] Zwraca nazwę portu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interfejsu jest zwykle przekazywany z pakietu debugowania (klienta) do dostawcy portu (serwera), można uzyskać połączenia do portu. Zarówno pakietu debugowania, jak i dostawcy portu sobie sprawę z możliwych opcji dla portu. Jeśli prosty ciąg opisujący portu, a następnie `IDebugPortRequest2::GetPortName` metoda ma za mało informacji do nawiązania połączenia. W przeciwnym razie można podać dodatkowe interfejsy przez klienta, który można uzyskać za pomocą serwera `IDebugPortRequest2::QueryInterface`.

## <a name="see-also"></a>Zobacz też
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)