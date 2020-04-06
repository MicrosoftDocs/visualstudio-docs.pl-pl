---
title: IDebugObject::IsReadOnly | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19546550f916e9d42adf634b0d85958ce9697d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726412"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Określa, czy ten obiekt jest tylko do odczytu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Parametry
`pfIsReadOnly`\
[na zewnątrz] Zwraca wartość niezerową (`TRUE`), jeśli ten obiekt jest tylko do odczytu; w przeciwnym razie`FALSE`zwraca zero ( ).

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obiekt tylko do odczytu nie może mieć jego wartość zmieniona po jego utworzeniu.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
