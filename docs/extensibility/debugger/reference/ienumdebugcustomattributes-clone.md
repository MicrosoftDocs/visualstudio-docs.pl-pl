---
title: IEnumDebugCustomAttributes::Klon | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Clone
helpviewer_keywords:
- IEnumDebugCustomAttributes::Clone
ms.assetid: e6825000-e195-42b4-b296-bfe1e533d79b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3c6cd55293bf34b0c2780dd76eaf8f4ee81bb69
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717260"
---
# <a name="ienumdebugcustomattributesclone"></a>IEnumDebugCustomAttributes::Clone
Tworzy wyliczenia, który zawiera ten sam stan wyliczenia jako bieżącego wylicznika.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Clone ( 
   IEnumCustomAttributes** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugCustomAttributes ppEnum
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
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
