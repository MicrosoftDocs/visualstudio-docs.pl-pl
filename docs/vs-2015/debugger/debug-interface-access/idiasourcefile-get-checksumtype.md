---
title: 'IDiaSourceFile:: get_checksumType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f859bce63e2976b23ab613e249dad41b2bc63486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190703"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera typ sumy kontrolnej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca typ sumy kontrolnej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Typ sumy kontrolnej to wartość, którą można zamapować na algorytm sumy kontrolnej. Na przykład standardowy format pliku PDB może zazwyczaj mieć jedną z następujących wartości:  
  
|Typ sumy kontrolnej|Etykieta interfejsu CryptoAPI|Opis|  
|-------------------|---------------------|-----------------|  
|0|\<none>|Brak sumy kontrolnej.|  
|1|`CALG_MD5`|Wygenerowano sumę kontrolną z algorytmem wyznaczania wartości skrótu MD5.|  
|2|`CALG_SHA1`|Wygenerowano sumę kontrolną z algorytmem skrótu SHA1.|  
  
 `CryptoAPI`Etykiety pochodzą z `ALG_ID` wyliczenia. Aby uzyskać więcej informacji na temat algorytmów wyznaczania wartości skrótu, zapoznaj się z `CryptoAPI` sekcją firmy Microsoft [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] .  
  
 Aby uzyskać rzeczywiste bajty sumy kontrolnej dla pliku źródłowego, wywołaj metodę [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)
