---
title: Basictype — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 891b83d6a43cb73fe8f38bb8b20201cbcfa230f6
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154085"
---
# <a name="basictype"></a>BasicType
Określa podstawowy typ symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31,  
   btChar16   = 32,  // char16_t
   btChar32   = 33,  // char32_t
};  
```  
  
## <a name="elements"></a>Elementy  
 btNoType  
 Nie typ podstawowy jest określony.  
  
 btVoid  
 Typ podstawowy jest `void`.  
  
 btChar  
 Typ podstawowy jest `char` (C/C++ typu).  
  
 btWChar  
 Typ podstawowy jest znakiem dwubajtowym (Unicode) (`WCHAR`).  
  
 btInt  
 Typ podstawowy jest `signed int` (C/C++ typu).  
  
 btUInt  
 Typ podstawowy jest `unsigned int` (C/C++ typu).  
  
 btFloat  
 Typ podstawowy jest liczba zmiennoprzecinkowa (`FLOAT`).  
  
 btBCD  
 Typ podstawowy jest kodowane dane binarne wartości dziesiętnej (`BCD`).  
  
 btBool  
 Typ podstawowy jest wartością logiczną (`BOOL`).  
  
 btLong  
 Typ podstawowy jest `long int` (C/C++ typu).  
  
 btULong  
 Typ podstawowy jest `unsigned long int` (C/C++ typu).  
  
 btCurrency  
 Typ podstawowy jest waluta.  
  
 btDate  
 Typ podstawowy jest daty/godziny (`DATE`).  
  
 btVariant  
 Typ podstawowy jest strukturą typu zmiennej (`VARIANT`).  
  
 btComplex  
 Typ podstawowy jest liczbą.  
  
 btBit  
 Typ podstawowy jest nieco.  
  
 btBSTR  
 Typ podstawowy jest ciągiem podstawowe lub binarny (`BSTR`).  
  
 btHresult  
 Typ podstawowy jest `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są zwracane przez [idiasymbol::get_basetype —](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol::get_basetype —](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
