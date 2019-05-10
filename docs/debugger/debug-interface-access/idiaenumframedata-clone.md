---
title: Idiaenumframedata::clone — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5c86d9f4f8eb02b0389e7ea28b5858f8576f6c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838405"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.

## <a name="syntax"></a>Składnia

```C++
HRESULT Clone( 
   IDiaEnumFrameData** ppenum
);
```

#### <a name="parameters"></a>Parametry
 ppenum

[out] Zwraca [idiaenumframedata —](../../debugger/debug-interface-access/idiaenumframedata.md) obiekt, który zawiera zduplikowane modułu wyliczającego. Ramki, w których dane są duplikowane tylko moduł wyliczający.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)