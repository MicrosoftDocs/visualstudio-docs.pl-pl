---
title: IDiaDataSource::get_lastError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 34954cd32b350a7c5f9c176deffd9943f8e05100
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554199"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
Pobiera nazwę pliku dla ostatniego błędu ładowania.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

[out] Zwraca ciąg, który zawiera nazwę pliku .pdb, które są skojarzone z ostatniego błędu ładowania.

## <a name="return-value"></a>Wartość zwracana
 Zwraca kod ostatniego błędu spowodowanych operacji ładowania. Zwraca `E_INVALIDARG` Jeśli `pRetVal` parametr `NULL`.

## <a name="example"></a>Przykład

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Zobacz też
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)