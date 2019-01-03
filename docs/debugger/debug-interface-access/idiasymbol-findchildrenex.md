---
title: IDiaSymbol::findChildrenEx | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7014bf0b42e9fcaab313c6b89d0caf1f1678a297
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928714"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
Pobiera elementy podrzędne symbolu. Symbole lokalne, które są zwracane obejmują informacje dotyczące zakresów na żywo, jeśli program został skompilowany z optymalizacji na.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findChildrenEx (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `symtag`  
 [in] Określa tagi symboli elementów podrzędnych, które mają zostać pobrane, zgodnie z definicją w [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md). Ustaw `SymTagNull` dla wszystkich elementów podrzędnych do pobrania.  
  
 `name`  
 [in] Określa nazwę elementy podrzędne, które mają zostać pobrane. Ustaw `NULL` dla wszystkich elementów podrzędnych do pobrania.  
  
 `compareFlags`  
 [in] Określa opcje porównywania, która ma zostać zastosowany do dopasowania nazwy. Wartości z kolekcji [namesearchoptions — wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md) wyliczenia można samodzielnie lub w połączeniu.  
  
 `ppResult`  
 [out] Zwraca [idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md) pobrać obiekt, który zawiera listę symbolami podrzędnymi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` Jeśli co najmniej jeden element podrzędny symbol został znaleziony lub zwraca `S_FALSE` Jeśli żadne elementy podrzędne nie znaleziono; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzona wersja [idiasymbol::findchildren —](../../debugger/debug-interface-access/idiasymbol-findchildren.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2.h  
  
 Biblioteka: diaguids.lib  
  
 Biblioteki DLL: msdia100.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)   
 [Idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession::findchildren —](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions, wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md)