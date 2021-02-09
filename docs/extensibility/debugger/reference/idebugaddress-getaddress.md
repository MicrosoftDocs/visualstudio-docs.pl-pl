---
title: 'IDebugAddress:: GetAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df4eb1278a0fe436899c1da989c4c63cfa98cac3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853015"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
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

## <a name="parameters"></a>Parametry
`pAddress`\
[in. out] Struktura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) , która jest wypełniana przez tę metodę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Struktura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) jest przenoszona do tej metody, a następnie wypełnia ją odpowiednimi informacjami. Sposób interpretacji tych informacji zależy od rodzaju zwracanych informacji oraz od samego programu obsługi symboli. Aby uzyskać więcej informacji, zobacz [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .

## <a name="see-also"></a>Zobacz też
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
