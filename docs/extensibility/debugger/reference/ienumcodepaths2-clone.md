---
title: IEnumCodePaths2::Klonowanie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Clone
helpviewer_keywords:
- IEnumCodePaths2::Clone
ms.assetid: 9d5c6bc6-7e72-4f1b-801c-7192458f3ba8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ae54e34f316fb404a1ec125c3922584d7218bc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717867"
---
# <a name="ienumcodepaths2clone"></a>IEnumCodePaths2::Clone
Zwraca kopię bieżącego wyliczenia jako osobny obiekt.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Clone(
   IEnumCodePaths2** ppEnum
);
```

```csharp
int Clone(
   out IEnumCodePaths2 ppEnum
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
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
