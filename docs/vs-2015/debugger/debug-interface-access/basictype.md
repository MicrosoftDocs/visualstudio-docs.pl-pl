---
title: Basictype — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 633fb76a8177f239b988554a5d15bee09e00c2d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745023"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa podstawowy typ symbolu.  
  
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



