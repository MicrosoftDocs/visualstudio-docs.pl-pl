---
title: IDebugProperty2::GetSize | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b55e6663ac1d9d679c2cdf524fbd7d1848dc22b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686499"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
Pobiera rozmiar w bajtach, wartość właściwości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

#### <a name="parameters"></a>Parametry
 `pdwSize`

 [out] Zwraca rozmiar w bajtach, wartość właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETSIZE_NO_SIZE` Jeśli właściwość ma rozmiar nie.

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)