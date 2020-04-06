---
title: IEnumDebugFields::Klon | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1120e62d5dbed45f11b43ea0e131ee3173c1751c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716913"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
Ta metoda zwraca kopię bieżącego wyliczenia jako oddzielny obiekt.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Clone(
   IEnumDebugFields** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[na zewnątrz] Zwraca kopię tego wyliczenia jako oddzielny obiekt.

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kopia wyliczenia ma taki sam stan jak oryginał w czasie, gdy ta metoda jest wywoływana. Jednak stany kopii i oryginału są oddzielne i mogą być zmieniane indywidualnie.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
