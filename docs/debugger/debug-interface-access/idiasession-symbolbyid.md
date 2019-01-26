---
title: Idiasession::symbolbyid — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba13c62f5e72e7192572def7b48046be3e1a20c6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54964463"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Pobiera symbol według unikatowego identyfikatora.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [in] Unikatowy identyfikator.  
  
 `ppSymbol`  
 [out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) pobrać obiekt reprezentujący symbol.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Określony identyfikator jest unikatowa wartość używana wewnętrznie przez DIA SDK unikatowość wszystkie symbole.  
  
 Ta metoda może służyć, na przykład, można pobrać symboli reprezentujący typ symbolu innego (Zobacz przykład).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pobiera [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) reprezentujący typ symbolu innego. W tym przykładzie pokazano, jak używać `symbolById` metody w sesji. Prostszej metody jest wywołanie [idiasymbol::get_type —](../../debugger/debug-interface-access/idiasymbol-get-type.md) metodę, aby bezpośrednio pobrać symbol typu.  
  
```C++  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)