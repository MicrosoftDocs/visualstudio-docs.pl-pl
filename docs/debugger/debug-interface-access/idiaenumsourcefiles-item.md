---
title: 'IDiaEnumSourceFiles:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5175d38da97a0b3e64ad94692c62425ba6e9cc83
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467919"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Pobiera plik źródłowy przy użyciu indeksu.

## <a name="syntax"></a>Składnia

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaSourceFile** sourceFile
);
```

#### <a name="parameters"></a>Parametry
 index

podczas Indeks obiektu [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) do pobrania. Indeks znajduje się w zakresie od 0 do `count` -1, gdzie `count` jest zwracany przez metodę [IDiaEnumSourceFiles:: get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) .

 sourceFile

określoną Zwraca obiekt [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) reprezentujący żądany plik źródłowy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)