---
title: Namesearchoptions — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bbe801b749b60cd22ce8a980ea78b7713fa4422
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973892"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Określa opcje wyszukiwania dla nazwy symboli i plików.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>Elementy  
 `nsNone`  
 Nie określono opcji.  
  
 `nsfCaseSensitive`  
 Stosuje musi odpowiadać nazwie uwzględniana wielkość liter.  
  
 `nsfCaseInsensitive`  
 Stosuje dopasowanie bez uwzględniania wielkości liter nazwy.  
  
 `nsfFNameExt`  
 Traktuje nazw jako ścieżki, a następnie stosuje musi odpowiadać nazwie nazwa_pliku.Ext.  
  
 `nsfRegularExpression`  
 Stosuje dopasowanie liter nazwy przy użyciu gwiazdki (*) i znaki zapytania (?) jako symboli wieloznacznych.  
  
 `nsfUndecoratedName`  
 Dotyczy tylko symbole, które mają zarówno niedekorowanego i nazw ozdobionych.  
  
## <a name="remarks"></a>Uwagi  
 Wartości z tego wyliczenia są przekazywane do następujących metod:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasession::findchildren —](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Idiasession::FindFile —](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)