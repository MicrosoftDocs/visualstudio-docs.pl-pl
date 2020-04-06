---
title: IEnumDebugAddresses::GetCount | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4610613b6fef5e80ae0fd36c3548b4dfdcbc8591
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717678"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
Ta metoda zwraca liczbę elementów w wyliczeniu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parametry
`pcelt`\
[na zewnątrz] Zwraca liczbę elementów w wyliczeniu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest częścią niestandardowego interfejsu wyliczenia COM, który określa, że należy zaimplementować tylko next, clone, skip i reset.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
