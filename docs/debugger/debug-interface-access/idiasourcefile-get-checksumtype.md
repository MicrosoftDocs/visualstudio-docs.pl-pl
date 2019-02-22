---
title: IDiaSourceFile::get_checksumType | Microsoft Docs
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
ms.openlocfilehash: 35e5719d285e9e99e5f7429685fa04a2c6d7f3ab
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646398"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
Pobiera typ sumy kontrolnej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_checksumType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca typ sumy kontrolnej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Typ sumy kontrolnej to wartości, które mogą być mapowane do algorytmu sumy kontrolnej. Na przykład standardowy format pliku PDB zazwyczaj może mieć jedną z następujących wartości:

|Typ sumy kontrolnej|CryptoAPI Label|Opis|
|-------------------|---------------------|-----------------|
|0|\<Brak >|Nie istnieje sumy kontrolnej.|
|1|`CALG_MD5`|Suma kontrolna jest generowany przy użyciu algorytmu wyznaczania wartości skrótu MD5.|
|2|`CALG_SHA1`|Suma kontrolna jest generowany przy użyciu algorytmu wyznaczania wartości skrótu SHA1.|

 `CryptoAPI` Etykiety są z `ALG_ID` wyliczenia. Aby uzyskać więcej informacji na temat algorytmy wyznaczania wartości skrótu, zapoznaj się `CryptoAPI` sekcji Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].

 Aby uzyskać bajtów rzeczywista suma kontrolna pliku źródłowego, należy wywołać [idiasourcefile::get_checksum —](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)