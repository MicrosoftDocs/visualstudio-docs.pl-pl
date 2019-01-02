---
title: Idiasourcefile::get_checksumtype — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 750d48cad07251f34e988fa8a6ced618821c443d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825917"
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
  
|Typ sumy kontrolnej|Etykieta interfejsu CryptoAPI|Opis|  
|-------------------|---------------------|-----------------|  
|0|\<Brak >|Nie istnieje sumy kontrolnej.|  
|1|`CALG_MD5`|Suma kontrolna jest generowany przy użyciu algorytmu wyznaczania wartości skrótu MD5.|  
|2|`CALG_SHA1`|Suma kontrolna jest generowany przy użyciu algorytmu wyznaczania wartości skrótu SHA1.|  
  
 `CryptoAPI` Etykiety są z `ALG_ID` wyliczenia. Aby uzyskać więcej informacji na temat algorytmy wyznaczania wartości skrótu, zapoznaj się `CryptoAPI` sekcji Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Aby uzyskać bajtów rzeczywista suma kontrolna pliku źródłowego, należy wywołać [idiasourcefile::get_checksum —](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)