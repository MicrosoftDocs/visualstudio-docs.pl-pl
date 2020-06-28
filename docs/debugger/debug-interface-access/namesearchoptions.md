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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 696ad3e659b503b27da73056dafb57c5852d5133
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461176"
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
`nsNone`Nie określono żadnych opcji.

`nsfCaseSensitive`Stosuje dopasowanie nazw z uwzględnieniem wielkości liter.

`nsfCaseInsensitive`Stosuje dopasowanie nazw bez uwzględniania wielkości liter.

`nsfFNameExt`Traktuje nazwy jako ścieżki i stosuje dopasowanie nazwy pliku. ext.

`nsfRegularExpression`Stosuje dopasowanie nazwy z uwzględnieniem wielkości liter przy użyciu gwiazdek (*) i znaków zapytania (?) jako symboli wieloznacznych. (Inne typowe znaki wyrażenia regularnego nie są obsługiwane).

`nsfUndecoratedName`Dotyczy tylko symboli, które mają nazwy niedekoracyjne i dekoracyjne.

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
