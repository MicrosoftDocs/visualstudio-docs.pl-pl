---
title: IDebugProperty2::GetSize | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b76a6a563a4a9ecd63c81c897a1ba21b3a977b80
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314649"
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

## <a name="parameters"></a>Parametry
`pdwSize`\
[out] Zwraca rozmiar w bajtach, wartość właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETSIZE_NO_SIZE` Jeśli właściwość ma rozmiar nie.

## <a name="see-also"></a>Zobacz także
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)