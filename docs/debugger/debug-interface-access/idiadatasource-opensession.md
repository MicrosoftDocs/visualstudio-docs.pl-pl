---
description: Otwiera sesję do wykonywania zapytań o symbole.
title: 'IDiaDataSource:: openSession | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d31e30c2044332d1e299d6a734ee5fecb22ec686
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158240"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Otwiera sesję do wykonywania zapytań o symbole.

## <a name="syntax"></a>Składnia

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Parametry
ppSession

określoną Zwraca obiekt [IDiaSession](../../debugger/debug-interface-access/idiasession.md) reprezentujący otwartą sesję.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.

|Wartość|Opis|
|-----------|-----------------|
|E_UNEXPECTED|Obiekt [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) nie został wcześniej zainicjowany ze źródłem symboli.|
|E_INVALIDARG|Nieprawidłowy `ppSession` parametr.|
|E_OUTOFMEMORY|Za mało pamięci, aby otworzyć sesję.|

## <a name="remarks"></a>Uwagi
Ta metoda otwiera obiekt [IDiaSession](../../debugger/debug-interface-access/idiasession.md) dla źródła danych.

`IDiaSession` obiekty implementują zapytania do źródła danych. Sesja zarządza jedną przestrzenią adresową dla każdego zestawu symboli debugowania. Jeśli plik exe lub dll opisany przez symbole źródła danych jest aktywny w wielu zakresach adresów (na przykład, ponieważ załadowano wiele procesów), należy użyć jednej sesji dla każdego zakresu adresów.

## <a name="example"></a>Przykład

```C++
IDiaSession* pSession;
HRESULT hr = pSource->openSession( &pSession );
if (FAILED(hr))
{
   // report error
}
```

## <a name="see-also"></a>Zobacz także
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [Omówienie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
