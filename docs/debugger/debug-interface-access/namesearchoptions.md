---
description: Określa opcje wyszukiwania dla nazw symboli i plików.
title: Namesearchoptions — | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bd074de0c44803a06d5399f2bd4dc1e3c43618a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155349"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Określa opcje wyszukiwania dla nazw symboli i plików.

## <a name="syntax"></a>Składnia

```C++
enum NameSearchOptions {
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
`nsNone` Nie określono żadnych opcji.

`nsfCaseSensitive` Stosuje dopasowanie nazw z uwzględnieniem wielkości liter.

`nsfCaseInsensitive` Stosuje dopasowanie nazw bez uwzględniania wielkości liter.

`nsfFNameExt` Traktuje nazwy jako ścieżki i stosuje dopasowanie nazwy pliku. ext.

`nsfRegularExpression` Stosuje dopasowanie nazwy z uwzględnieniem wielkości liter przy użyciu gwiazdek (*) i znaków zapytania (?) jako symboli wieloznacznych. (Inne typowe znaki wyrażenia regularnego nie są obsługiwane).

`nsfUndecoratedName` Dotyczy tylko symboli, które mają nazwy niedekoracyjne i dekoracyjne.

## <a name="remarks"></a>Uwagi
Wartości z tego wyliczenia są przesyłane do następujących metod:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Wymagania
Nagłówek: dia2. h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
