---
title: 'IDiaStackWalkHelper:: frameForVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::frameForVA method
ms.assetid: f35fc61b-f8dd-473a-b583-82c304059422
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28d9a7762cac1a63b40fa34118d4076403120763
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741423"
---
# <a name="idiastackwalkhelperframeforva"></a>IDiaStackWalkHelper::frameForVA
Pobiera ramkę stosu, która zawiera określony adres wirtualny.

## <a name="syntax"></a>Składnia

```C++
HRESULT frameForVA( 
   ULONGLONG        va,
   IDiaFrameData**  ppFrame
);
```

#### <a name="parameters"></a>Parametry
 `va`

podczas Adres wirtualny dla danych ramek.

 `ppFrame`

określoną Obiekt [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , który reprezentuje ramkę stosu o określonym adresie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)