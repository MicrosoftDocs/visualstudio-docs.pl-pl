---
title: IDebugSettingsCallback2::EnumEEs | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc9073ae5244b05234b3f37874bd6bcd6347954f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322156"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Wylicza ewaluatory wyrażeń dostępne, biorąc pod uwagę identyfikatorów języka i dostawcy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

## <a name="parameters"></a>Parametry
`celtBuffer`\
[in] Liczba elementów w `pceltEEs` buforu.

`rgguidLang`\
[out w] Unikatowy identyfikator dla języka programowania.

`rgguidVendor`\
[out w] Unikatowy identyfikator dla dostawcy.

`pceltEEs`\
[out w] Tablica ewaluatory wyrażeń.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)