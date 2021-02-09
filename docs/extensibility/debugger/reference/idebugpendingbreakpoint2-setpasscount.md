---
title: 'IDebugPendingBreakpoint2:: SetPassCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37aebea3e5dfa9e4693de8ed5b4b6b4b08557a2a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893883"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Ustawia lub zmienia liczbę przebiegów skojarzoną z oczekującym punktem przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Parametry
`bpPassCount`\
podczas Struktura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) , która zawiera liczbę przebiegów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` czy punkt przerwania został usunięty.

## <a name="remarks"></a>Uwagi
 Wszystkie liczby przebiegów, które wcześniej były skojarzone z oczekującym punktem przerwania, zostaną utracone. Wszystkie punkty przerwania powiązane z tym oczekującym punktem przerwania są wywoływane w celu ustawienia liczby przeskoków do `bpPassCount` parametru.

## <a name="see-also"></a>Zobacz też
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
