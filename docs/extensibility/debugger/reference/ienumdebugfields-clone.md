---
description: Ta metoda zwraca kopię bieżącego wyliczenia pól jako osobnego obiektu.
title: 'IEnumDebugFields:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 965bc201646c7e068c58f9238dccba9a9e587d26
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224905"
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
określoną Zwraca kopię tego wyliczenia jako oddzielny obiekt.

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kopia wyliczenia ma taki sam stan jak oryginał w momencie wywołania tej metody. Jednak kopia i stan pierwotny są oddzielone i mogą być zmieniane indywidualnie.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
