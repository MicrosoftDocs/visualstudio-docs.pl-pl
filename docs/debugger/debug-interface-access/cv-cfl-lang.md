---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fb684d0ff68e5ede6b0847ef9aeba1821ecafcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745335"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
Określa język kodu źródłowego aplikacji lub połączonego modułu.

## <a name="syntax"></a>Składnia

```C++
typedef enum CV_CFL_LANG {
    CV_CFL_C       = 0x00,
    CV_CFL_CXX     = 0x01,
    CV_CFL_FORTRAN = 0x02,
    CV_CFL_MASM    = 0x03,
    CV_CFL_PASCAL  = 0x04,
    CV_CFL_BASIC   = 0x05,
    CV_CFL_COBOL   = 0x06,
    CV_CFL_LINK    = 0x07,
    CV_CFL_CVTRES  = 0x08,
    CV_CFL_CVTPGD  = 0x09,
    CV_CFL_CSHARP  = 0x0A,
    CV_CFL_VB      = 0x0B,
    CV_CFL_ILASM   = 0x0C,
    CV_CFL_JAVA    = 0x0D,
    CV_CFL_JSCRIPT = 0x0E,
    CV_CFL_MSIL    = 0x0F,
    CV_CFL_HLSL    = 0x10
} CV_CFL_LANG;
```

## <a name="elements"></a>Elementy
Język aplikacji CV_CFL_C to C.

Język aplikacji CV_CFL_CXX C++.

Język aplikacji CV_CFL_FORTRAN to Pascal.

Język aplikacji CV_CFL_MASM to asembler programu Microsoft Macro.

Język aplikacji CV_CFL_PASCAL to Pascal.

Język aplikacji CV_CFL_BASIC jest podstawowy.

Język aplikacji CV_CFL_COBOL to COBOL.

Aplikacja CV_CFL_LINK jest modułem wygenerowanym przez konsolidator.

Aplikacja CV_CFL_CVTRES to moduł zasobów przekonwertowany za pomocą narzędzia CVTRES.

Aplikacja CV_CFL_CVTPGD to moduł zoptymalizowany środowisko URUCHOMIENIOWE Pogo wygenerowany przy użyciu narzędzia CVTPGD.

Język aplikacji CV_CFL_CSHARP C#.

Język aplikacji CV_CFL_VB jest Visual Basic.

Język aplikacji CV_CFL_ILASM jest zestawem języka pośredniego (czyli zestawem środowiska uruchomieniowego języka wspólnego (CLR)).

Język aplikacji CV_CFL_JAVA to Java.

Język aplikacji CV_CFL_JSCRIPT to JScript.

Język aplikacji CV_CFL_MSIL jest nieznanego języka pośredniego firmy Microsoft (MSIL), prawdopodobnie w wyniku użycia przełącznika [/LTCG (w czasie konsolidacji)](/cpp/build/reference/ltcg-link-time-code-generation) .

Język aplikacji CV_CFL_HLSL to język cieniowania wysokiego poziomu.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez wywołanie metody [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz także
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
