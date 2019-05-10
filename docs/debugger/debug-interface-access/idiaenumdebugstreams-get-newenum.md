---
title: IDiaEnumDebugStreams::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::get__NewEnum method
ms.assetid: 972372ff-abfc-4987-a302-7788fab90348
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4503e8129ba8fafa38bd2f00ec3ecde5bfe67f1f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838314"
---
# <a name="idiaenumdebugstreamsgetnewenum"></a>IDiaEnumDebugStreams::get__NewEnum
Pobiera <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> wersję tego modułu wyliczającego.

## <a name="syntax"></a>Składnia

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

[out] Zwraca `IUnknown` interfejs, który reprezentuje <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> wersję tego modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)