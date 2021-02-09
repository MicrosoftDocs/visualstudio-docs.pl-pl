---
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
ms.openlocfilehash: c63d38e1b4d79227cfdc694dc6d8c154a01532f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853213"
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
