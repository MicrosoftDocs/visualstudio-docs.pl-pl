---
title: 'IDiaLineNumber:: get_columnNumber | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51763dea01039ce084804bfa007fd8f0577cb9e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192375"
---
# <a name="idialinenumberget_columnnumber"></a>IDiaLineNumber::get_columnNumber
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera numer kolumny, w której rozpoczyna się wyrażenie lub instrukcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
[C++]  
HRESULT get_columnNumber (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca numer kolumny, w której rozpoczyna się wyrażenie lub instrukcję. Jeśli wartość jest równa zero, wówczas informacje o kolumnie nie są obecne.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wartość kolumny zwracana przez tę metodę jest przesunięciem bajtów do wiersza do pierwszego znaku instrukcji w wierszu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
