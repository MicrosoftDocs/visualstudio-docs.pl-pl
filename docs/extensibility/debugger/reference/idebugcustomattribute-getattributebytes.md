---
description: Pobiera informacje o atrybucie jako obiekt BLOB bajtów.
title: 'IDebugCustomAttribute:: GetAttributeBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7cfc3ba650ff8277bb6cb85f5d1530d202bd426
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163086"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Pobiera informacje o atrybucie jako obiekt BLOB bajtów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>Parametry
`ppBlob`\
[in. out] Tablica, która jest wypełniana przy użyciu atrybutu bajtów.

`pdwLen`\
[in. out] Określa maksymalną liczbę bajtów zwracanych w `ppBlob` tablicy i zwraca liczbę bajtów rzeczywiście zapisaną do tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ustaw `ppBlob` parametr na wartość null, aby zwrócić liczbę dostępnych bajtów atrybutów. Następnie przydziel tablicę i przekaż tę tablicę do `ppBlob` parametru.

 Atrybut bajty reprezentuje pierwotne dane atrybutu niestandardowego.

## <a name="see-also"></a>Zobacz też
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
