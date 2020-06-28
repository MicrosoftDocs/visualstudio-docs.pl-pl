---
title: 'IDiaLineNumber:: get_sourceFileId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_sourceFileId method
ms.assetid: 4f482a1e-e85f-4173-98de-8e5f7622554b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5a0151a8cd5bcc10fb306b34762ad5d1bb698f4
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466855"
---
# <a name="idialinenumberget_sourcefileid"></a>IDiaLineNumber::get_sourceFileId
Pobiera unikatowy identyfikator pliku źródłowego dla pliku źródłowego, który został wniesiony przez ten wiersz.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_sourceFileId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca unikatowy identyfikator pliku źródłowego dla pliku źródłowego, który został wniesiony przez ten wiersz.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)