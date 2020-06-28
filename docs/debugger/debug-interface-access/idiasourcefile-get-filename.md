---
title: 'IDiaSourceFile:: get_fileName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_fileName method
ms.assetid: a5cb8927-23c6-469e-8f78-f2787d85dba4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35935f3f61fbbdc4ded91c7f1ec2f3d03e6cefab
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465294"
---
# <a name="idiasourcefileget_filename"></a>IDiaSourceFile::get_fileName
Pobiera nazwę pliku źródłowego.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_fileName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca nazwę pliku źródłowego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)