---
title: 'IDiaSourceFile:: get_checksumType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c85c6ce8f03534c3ed810e530dbd12d8c6d115be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741828"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
Pobiera typ sumy kontrolnej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_checksumType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca typ sumy kontrolnej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Typ sumy kontrolnej to wartość, którą można zamapować na algorytm sumy kontrolnej. Na przykład standardowy format pliku PDB może zazwyczaj mieć jedną z następujących wartości:

|Typ sumy kontrolnej|Etykieta interfejsu CryptoAPI|Opis|
|-------------------|---------------------|-----------------|
|0|\<none >|Brak sumy kontrolnej.|
|1|`CALG_MD5`|Wygenerowano sumę kontrolną z algorytmem wyznaczania wartości skrótu MD5.|
|2|`CALG_SHA1`|Wygenerowano sumę kontrolną z algorytmem skrótu SHA1.|

 Etykiety `CryptoAPI` pochodzą z wyliczenia `ALG_ID`. Aby uzyskać więcej informacji na temat algorytmów wyznaczania wartości skrótu, zapoznaj się z sekcją `CryptoAPI` w programie Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].

 Aby uzyskać rzeczywiste bajty sumy kontrolnej dla pliku źródłowego, wywołaj metodę [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) .

## <a name="see-also"></a>Zobacz także
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)