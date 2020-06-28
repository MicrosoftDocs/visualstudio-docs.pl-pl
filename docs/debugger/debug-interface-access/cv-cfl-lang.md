---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: ac8910ebe012e1edbaa6c26695027214db4e66c2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462135"
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

Język aplikacji CV_CFL_CXX to C++.

Język aplikacji CV_CFL_FORTRAN to Pascal.

Język aplikacji CV_CFL_MASM to asembler programu Microsoft Macro.

Język aplikacji CV_CFL_PASCAL to Pascal.

Język aplikacji CV_CFL_BASIC jest podstawowy.

Język aplikacji CV_CFL_COBOL to COBOL.

Aplikacja CV_CFL_LINK jest modułem wygenerowanym przez konsolidator.

Aplikacja CV_CFL_CVTRES to moduł zasobów przekonwertowany za pomocą narzędzia CVTRES.

Aplikacja CV_CFL_CVTPGD to zoptymalizowany pod kątem środowisko URUCHOMIENIOWE Pogo moduł wygenerowany przy użyciu narzędzia CVTPGD.

Język aplikacji CV_CFL_CSHARP to C#.

CV_CFL_VB język aplikacji jest Visual Basic.

Język aplikacji CV_CFL_ILASM jest zestawem języka pośredniego (czyli zestawem środowiska uruchomieniowego języka wspólnego (CLR)).

Język aplikacji CV_CFL_JAVA to Java.

Język aplikacji CV_CFL_JSCRIPT to JScript.

CV_CFL_MSIL język aplikacji jest nieznanego języka pośredniego firmy Microsoft (MSIL), prawdopodobnie z zastosowaniem przełącznika [/LTCG (generowanie kodu w czasie konsolidacji)](/cpp/build/reference/ltcg-link-time-code-generation) .

Język aplikacji CV_CFL_HLSL to język cieniowania wysokiego poziomu.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez wywołanie metody [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
