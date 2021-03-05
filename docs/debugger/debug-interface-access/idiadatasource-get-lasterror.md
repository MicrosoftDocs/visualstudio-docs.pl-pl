---
description: Pobiera nazwę pliku dla ostatniego błędu ładowania.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7edce9a2af6c849371360526d617d20738973cba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158316"
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

## <a name="see-also"></a>Zobacz także
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
