---
title: Idiasectioncontrib::get_relocationscrc — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_relocationsCrc method
ms.assetid: 8c29c91a-062d-4566-a9b7-49251036a15a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a57c46bef62039241c7d0cc064753199440893e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839514"
---
# <a name="idiasectioncontribgetrelocationscrc"></a>IDiaSectionContrib::get_relocationsCrc
Pobiera wyboru cyklicznej kontroli nadmiarowości (CRC) przenoszenia informacji w sekcji.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_relocationsCrc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca wartość sumy kontrolnej przenoszenia informacji w sekcji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)