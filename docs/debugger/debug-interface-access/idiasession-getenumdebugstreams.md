---
title: 'IDiaSession:: getEnumDebugStreams | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumDebugStreams method
ms.assetid: d294954b-80e9-476c-b9f0-5ca6fd575f68
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62088c1ff7dd3dea8016a18d7c41425fdd584661
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465441"
---
# <a name="idiasessiongetenumdebugstreams"></a>IDiaSession::getEnumDebugStreams
Pobiera wyliczaną sekwencję strumieni danych debugowania.

## <a name="syntax"></a>Składnia

```C++
HRESULT getEnumDebugStreams ( 
   IDiaEnumDebugStreams** ppEnumDebugStreams
)
```

#### <a name="parameters"></a>Parametry
 `ppEnumDebugStreams`

określoną Zwraca obiekt [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) , który zawiera listę strumieni debugowania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)