---
title: 'IDiaDataSource:: get_lastError | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 231c6b082f7a641ee78d10003d544c3fb9644c1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468526"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
Pobiera nazwę pliku dla ostatniego błędu ładowania.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

określoną Zwraca ciąg zawierający nazwę pliku. pdb skojarzoną z ostatnim błędem ładowania.

## <a name="return-value"></a>Wartość zwracana
 Zwraca kod ostatniego błędu spowodowany operacją ładowania. Zwraca wartość `E_INVALIDARG` , jeśli `pRetVal` parametr jest `NULL` .

## <a name="example"></a>Przykład

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Zobacz też
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)