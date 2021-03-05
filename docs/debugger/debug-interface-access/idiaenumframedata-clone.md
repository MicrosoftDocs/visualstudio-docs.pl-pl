---
description: Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia co bieżący moduł wyliczający dane ramek.
title: 'IDiaEnumFrameData:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9a5df5295143e9a6fb815ddc78d103b910ccfda7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158086"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.

## <a name="syntax"></a>Składnia

```C++
HRESULT Clone( 
   IDiaEnumFrameData** ppenum
);
```

#### <a name="parameters"></a>Parametry
 ppenum

określoną Zwraca obiekt [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) , który zawiera duplikat modułu wyliczającego. Dane ramki nie są duplikowane, tylko moduł wyliczający.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
