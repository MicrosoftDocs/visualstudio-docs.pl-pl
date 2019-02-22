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
ms.openlocfilehash: 4ddcbf414d70d5952c9b4c7b5cca4eb4cd35e28a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645696"
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
- [out w] Bufor, który jest wypełniane żądanych danych. Nie może być `NULL`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` przypadku nie PDATA dla określonego adresu. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 PDATA (sekcja o nazwie ".pdata") compiland — zawiera informacje dotyczące obsługi funkcji wyjątków.

 Obiekt wywołujący wie, jak dużo danych jest zwracane, więc nie trzeba zadać, jak dużo danych jest dostępna na obiekt wywołujący. Dlatego jest dopuszczalne związanych z implementacją tę metodę, aby zwrócić błąd, jeśli `pbData` parametr `NULL`.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)