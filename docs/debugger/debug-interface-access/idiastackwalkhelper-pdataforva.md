---
title: IDiaStackWalkHelper::pdataForVA | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6315032a36369eff7a5d43241ae4968a64ad42cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831898"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Zwraca skojarzony z wirtualnym adresem bloku danych PDATA.

## <a name="syntax"></a>Składnia

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>Parametry
 `va`

[in] Określa adres wirtualny danych w celu uzyskania.

 `cbData`

[in] Rozmiar danych w bajtach, aby uzyskać.

 `pcbData`

[out] Zwraca rzeczywisty rozmiar danych w bajtach, które zostały pobrane.

 `pbData`

[out w] Bufor, który jest wypełniane żądanych danych. Nie może być `NULL`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` przypadku nie PDATA dla określonego adresu. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 PDATA (sekcja o nazwie ".pdata") compiland — zawiera informacje dotyczące obsługi funkcji wyjątków.

 Obiekt wywołujący wie, jak dużo danych jest zwracane, więc nie trzeba zadać, jak dużo danych jest dostępna na obiekt wywołujący. Dlatego jest dopuszczalne związanych z implementacją tę metodę, aby zwrócić błąd, jeśli `pbData` parametr `NULL`.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)