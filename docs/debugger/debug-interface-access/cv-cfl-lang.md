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
ms.openlocfilehash: 1f02545f1c19b57e46af302fbc0b2abaa7445612
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646346"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
Określa język kodu źródłowego aplikacji lub połączone modułu.

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

Język aplikacji CV_CFL_CXX jest w języku C++.

Język aplikacji CV_CFL_FORTRAN jest FORTRAN.

Język aplikacji CV_CFL_MASM jest Microsoft Macro Assembler.

Język aplikacji CV_CFL_PASCAL jest Pascal.

Język aplikacji CV_CFL_BASIC to podstawowa.

Język aplikacji CV_CFL_COBOL jest COBOL.

Aplikacja CV_CFL_LINK jest modułem generowanych przez konsolidator.

CV_CFL_CVTRES aplikacja jest konwertowane przy użyciu narzędzia CVTRES modułu zasobów.

Aplikacja CV_CFL_CVTPGD jest modułem POGO zoptymalizowane pod kątem wygenerowane za pomocą narzędzia CVTPGD.

Język aplikacji CV_CFL_CSHARP jest C#.

Język aplikacji CV_CFL_VB jest języka Visual Basic.

Język aplikacji CV_CFL_ILASM jest zestawem języka pośredniego (czyli zestawów środowiska uruchomieniowego języka wspólnego (CLR)).

Język aplikacji CV_CFL_JAVA czy języka Java.

Aplikacja CV_CFL_JSCRIPT języka JScript.

Język CV_CFL_MSIL aplikacji jest nieznany Microsoft Intermediate Language (MSIL), prawdopodobnie wynik za pomocą [opcję/LTCG (Generowanie kodu Link-time)](/cpp/build/reference/ltcg-link-time-code-generation) przełącznika.

Aplikacja CV_CFL_HLSL język jest wysoki poziom programu do cieniowania.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez wywołanie [idiasymbol::get_language —](../../debugger/debug-interface-access/idiasymbol-get-language.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst.h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
