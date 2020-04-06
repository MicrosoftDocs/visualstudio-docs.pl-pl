---
title: IEnumDebugPrograms2::Klon | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Clone
helpviewer_keywords:
- IEnumDebugPrograms2::Clone
ms.assetid: 880846c2-39d3-45cd-85c3-ad5409a3710f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26a099e84414afaf84d2505b35327ed86e125292
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715725"
---
# <a name="ienumdebugprograms2clone"></a>IEnumDebugPrograms2::Clone
Zwraca kopię bieżącego wyliczenia jako osobny obiekt.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Clone(
   IEnumDebugPrograms2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPrograms2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[na zewnątrz] Zwraca kopię tego wyliczenia jako oddzielny obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kopia wyliczenia ma taki sam stan jak oryginał w czasie, gdy ta metoda jest wywoływana. Jednak stany kopii i oryginału są oddzielne i mogą być zmieniane indywidualnie.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
