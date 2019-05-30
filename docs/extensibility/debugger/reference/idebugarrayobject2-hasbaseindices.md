---
title: IDebugArrayObject2::HasBaseIndices | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- HasBaseIndices
- IDebugArrayObject2::HasBaseIndices
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75c29c5bf4dd3c809a219fe009266999ada39ddf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349694"
---
# <a name="idebugarrayobject2hasbaseindices"></a>IDebugArrayObject2::HasBaseIndices
Określa, czy tablica ma podstawowy indeksów (dolne granice) zdefiniowany.

## <a name="syntax"></a>Składnia

```cpp
HRESULT HasBaseIndices (
   BOOL* pfHasBaseIndices
);
```

```csharp
int HasBaseIndices (
   out bool pfHasBaseIndices
);
```

## <a name="parameters"></a>Parametry
`pfHasBaseIndices`\
[out] Wartość TRUE, aby określić, czy tablica ma podstawowy indeksów (dolne granice); w przeciwnym razie wartość FALSE.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.