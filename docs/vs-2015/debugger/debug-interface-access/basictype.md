---
title: Basictype | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38de89b9774ac20f67b91e4ba864534122f4cdb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580840"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa typ podstawowy symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Elementy  
 btNoType  
 Nie określono typu podstawowego.  
  
 btVoid  
 Typ podstawowy to `void` .  
  
 btChar  
 Typ podstawowy to `char` (typ C/C++).  
  
 btWChar  
 Typ podstawowy to szeroki (Unicode) znak ( `WCHAR` ).  
  
 btInt  
 Typ podstawowy to `signed int` (typ C/C++).  
  
 btUInt  
 Typ podstawowy to `unsigned int` (typ C/C++).  
  
 btFloat  
 Typ podstawowy to liczba zmiennoprzecinkowa ( `FLOAT` ).  
  
 btBCD  
 Typ podstawowy jest zakodowaną binarnie cyfrą ( `BCD` ).  
  
 btBool  
 Typ podstawowy jest wartością logiczną ( `BOOL` ).  
  
 btLong  
 Typ podstawowy to `long int` (typ C/C++).  
  
 btULong  
 Typ podstawowy to `unsigned long int` Typ (C/C++).  
  
 btCurrency  
 Typ podstawowy to waluta.  
  
 btDate  
 Typ podstawowy to data/godzina ( `DATE` ).  
  
 btVariant  
 Typ podstawowy jest strukturą typu zmiennej ( `VARIANT` ).  
  
 btComplex  
 Typ podstawowy jest liczbą zespoloną.  
  
 btBit  
 Typ podstawowy to bit.  
  
 btBSTR  
 Typ podstawowy to ciąg podstawowy lub binarny ( `BSTR` ).  
  
 btHresult  
 Typ podstawowy to `HRESULT` .  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są zwracane przez metodę [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst. h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
