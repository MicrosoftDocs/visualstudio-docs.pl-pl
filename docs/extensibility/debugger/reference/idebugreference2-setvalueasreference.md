---
description: Ustawia wartość odwołania z innego odwołania.
title: 'IDebugReference2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84117f4a9eb925b442be86a73736479a05818ca1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165946"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Ustawia wartość odwołania z innego odwołania. Zarezerwowane do użytku w przyszłości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parametry
`rgpArgs`\
podczas Tablica obiektów [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) służąca do określenia, jak ustawić wartość referencyjną.

`dwArgCount`\
podczas Liczba odwołań w tablicy.

`pValue`\
podczas Obiekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , z którego ma zostać ustawiona wartość właściwości.

`dwTimeout`\
podczas Maksymalny czas oczekiwania (w milisekundach) przed powrotem z tej metody. Użyj `INFINITE` , aby czekać w nieskończoność.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca wartość `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz też
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
