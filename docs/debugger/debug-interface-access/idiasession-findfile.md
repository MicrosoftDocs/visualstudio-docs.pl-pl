---
title: 'IDiaSession:: FindFile — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ba8422ed2be8f06ac64fb9c7fa81c5b1b3c3f3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465826"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Pobiera pliki źródłowe według jednostka kompilacji i nazwy.

## <a name="syntax"></a>Składnia

```C++
HRESULT findFile ( 
   IDiaSymbol*           pCompiland,
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSourceFiles** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `pCompiland`

podczas Obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) reprezentujący jednostka kompilacji, który ma być używany jako kontekst dla wyszukiwania. Ustaw ten parametr, aby `NULL` znaleźć pliki źródłowe we wszystkich compilands.

 `name`

podczas Określa nazwę pliku źródłowego, który ma zostać pobrany. Ustaw ten parametr na `NULL` dla wszystkich plików źródłowych do pobrania.

 `option`

podczas Określa opcje porównania stosowane w celu wyszukiwania nazw. Wartości z wyliczenia [namesearchoptions —](../../debugger/debug-interface-access/namesearchoptions.md) można użyć samodzielnie lub w połączeniu.

 `ppResult`

określoną Zwraca obiekt [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) , który zawiera listę pobranych plików źródłowych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions, wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md)