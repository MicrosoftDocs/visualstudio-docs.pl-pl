---
title: Idiaenumsegments::clone — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Clone method
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9992b17155601284387981a9b424a77d3d9b5580
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829670"
---
# <a name="idiaenumsegmentsclone"></a>IDiaEnumSegments::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.

## <a name="syntax"></a>Składnia

```C++
HRESULT Clone ( 
   IDiaEnumSegments** ppenum
);
```

#### <a name="parameters"></a>Parametry
 ppenum

[out] Zwraca [idiaenumsegments —](../../debugger/debug-interface-access/idiaenumsegments.md) obiekt, który zawiera zduplikowane modułu wyliczającego. Segmenty nie są duplikowane, tylko moduł wyliczający.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)