---
title: 'IDiaDataSource:: openSession | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bec5507d15374e6e88afd4567d4b0fec9ca6cb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198601"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otwiera sesję do wykonywania zapytań o symbole.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Podsumowanie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
