---
title: Idiadatasource::opensession — | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198601"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zostanie otwarta sesja zapytań symboli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 ppSession  
 [out] Zwraca [idiasession —](../../debugger/debug-interface-access/idiasession.md) obiekt reprezentujący Otwórz sesję.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|E_UNEXPECTED|[Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md) obiektu nie wcześniej została zainicjowana przy użyciu źródła symboli.|  
|E_INVALIDARG|Nieprawidłowy `ppSession` parametru.|  
|E_OUTOFMEMORY|Za mało pamięci, aby otworzyć sesji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda otwiera [idiasession —](../../debugger/debug-interface-access/idiasession.md) obiekt dla źródła danych.  
  
 `IDiaSession` obiekty zaimplementować zapytania do źródła danych. Sesja zarządza jednej przestrzeni adresowej dla każdego zestawu symboli debugowania. Jeśli plik .exe lub .dll, opisanego przez symbole źródło danych jest aktywny adres wielu zakresów (na przykład, ponieważ wiele procesów jest załadowany), a następnie używać jednej sesji dla każdego zakresu adresów.  
  
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
 [Omówienie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
