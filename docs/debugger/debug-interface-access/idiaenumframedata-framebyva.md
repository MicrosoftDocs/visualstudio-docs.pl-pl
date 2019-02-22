---
title: Idiaenumframedata::framebyva — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62999d8b8dc0313e9ca5086dc4737d7a41db1c87
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623414"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Przywraca ramkę adresów wirtualnych (oceny luk w zabezpieczeniach).

## <a name="syntax"></a>Składnia

```C++
HRESULT frameByVA( 
   ULONGLONG       virtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Parametry
 virtualAddress

[in] Oceny luk w zabezpieczeniach ramki zainteresowania.

 ramowe

[out] Zwraca [idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md) obiekt reprezentujący ramkę, która zawiera podany adres.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli brak danych ramki odpowiadających podanym adresem. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)