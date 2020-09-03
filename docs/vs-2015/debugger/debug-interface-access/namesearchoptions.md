---
title: Namesearchoptions — | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6d721ebc5849fc459d24173ad0500b4b1c12260f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182978"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa opcje wyszukiwania dla nazw symboli i plików.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Nie określono żadnych opcji.  
  
 `nsfCaseSensitive`  
 Stosuje dopasowanie nazw z uwzględnieniem wielkości liter.  
  
 `nsfCaseInsensitive`  
 Stosuje dopasowanie nazw bez uwzględniania wielkości liter.  
  
 `nsfFNameExt`  
 Traktuje nazwy jako ścieżki i stosuje dopasowanie nazwy pliku. ext.  
  
 `nsfRegularExpression`  
 Stosuje dopasowanie nazwy z uwzględnieniem wielkości liter przy użyciu gwiazdek (*) i znaków zapytania (?) jako symboli wieloznacznych.  
  
 `nsfUndecoratedName`  
 Dotyczy tylko symboli, które mają nazwy niedekoracyjne i dekoracyjne.  
  
## <a name="remarks"></a>Uwagi  
 Wartości z tego wyliczenia są przesyłane do następujących metod:  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2. h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession:: findChildren —](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession:: FindFile —](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
