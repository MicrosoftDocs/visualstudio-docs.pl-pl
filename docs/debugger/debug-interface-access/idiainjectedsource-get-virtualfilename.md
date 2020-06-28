---
title: 'IDiaInjectedSource:: get_virtualFilename | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_virtualFilename method
ms.assetid: b9977075-8fd1-4b11-bfff-d87e9f2586dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f883d22e677d4401e6bee476cf88527a24787145
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467016"
---
# <a name="idiainjectedsourceget_virtualfilename"></a>IDiaInjectedSource::get_virtualFilename
Pobiera nazwę nadaną dla kodu źródłowego niezwiązanego z plikiem; oznacza to, że kod został wstrzyknięty.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_virtualFilename ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca nazwę nadaną do wstrzykniętego kodu źródłowego, który nie jest plikiem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)