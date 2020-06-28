---
title: 'IDiaSession:: findInjectedSource | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 315c09c29f99d8fe148f9795879193b2cb1f9e49
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465819"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Pobiera listę źródeł umieszczonych w magazynie symboli według dostawców atrybutów lub innych składników procesu kompilacji.

## <a name="syntax"></a>Składnia

```C++
HRESULT findInjectedSource ( 
   LPCOLESTR                 srcFile,
   IDiaEnumInjectedSources** ppResult
);
```

#### <a name="parameters"></a>Parametry
 srcFile

podczas Nazwa pliku źródłowego, który ma zostać wyszukany.

 ppResult

określoną Zwraca obiekt [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) , który zawiera listę wszystkich wprowadzonych źródeł.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)