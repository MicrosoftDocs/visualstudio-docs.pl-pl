---
title: 'IDiaDataSource:: openSession | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7dd6ab61db3e3bafd594298aa41d32bce64d4941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744917"
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
Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.

|Wartość|Opis|
|-----------|-----------------|
|E_UNEXPECTED|Obiekt [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) nie został wcześniej zainicjowany ze źródłem symboli.|
|E_INVALIDARG|Nieprawidłowy parametr `ppSession`.|
|E_OUTOFMEMORY|Za mało pamięci, aby otworzyć sesję.|

## <a name="remarks"></a>Uwagi
Ta metoda otwiera obiekt [IDiaSession](../../debugger/debug-interface-access/idiasession.md) dla źródła danych.

obiekty `IDiaSession` implementują zapytania do źródła danych. Sesja zarządza jedną przestrzenią adresową dla każdego zestawu symboli debugowania. Jeśli plik exe lub dll opisany przez symbole źródła danych jest aktywny w wielu zakresach adresów (na przykład, ponieważ załadowano wiele procesów), należy użyć jednej sesji dla każdego zakresu adresów.

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
