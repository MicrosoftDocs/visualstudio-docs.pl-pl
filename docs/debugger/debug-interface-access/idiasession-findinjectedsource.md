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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a49af12ed317732271d755477a2f50e6bb424205
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855222"
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