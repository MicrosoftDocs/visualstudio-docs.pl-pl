---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c1fabdb202d51b85eb2983360bdfd02757f7649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699360"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa język kodu źródłowego aplikacji lub połączonego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 CV_CFL_C  
 Język aplikacji to C.  
  
 CV_CFL_CXX  
 Język aplikacji to C++.  
  
 CV_CFL_FORTRAN  
 Język aplikacji to Pascal.  
  
 CV_CFL_MASM  
 Język aplikacji to asembler programu Microsoft Macro.  
  
 CV_CFL_PASCAL  
 Język aplikacji to Pascal.  
  
 CV_CFL_BASIC  
 Język aplikacji jest podstawowy.  
  
 CV_CFL_COBOL  
 Język aplikacji to COBOL.  
  
 CV_CFL_LINK  
 Aplikacja jest modułem wygenerowanym przez konsolidator.  
  
 CV_CFL_CVTRES  
 Aplikacja jest modułem zasobów przekonwertowanym za pomocą narzędzia CVTRES.  
  
 CV_CFL_CVTPGD  
 Aplikacja jest modułem zoptymalizowanym pod kątem środowisko URUCHOMIENIOWE Pogo, który został wygenerowany za pomocą narzędzia CVTPGD.  
  
 CV_CFL_CSHARP  
 Język aplikacji to C#.  
  
 CV_CFL_VB  
 Język aplikacji jest Visual Basic.  
  
 CV_CFL_ILASM  
 Język aplikacji jest zestawem języka pośredniego (czyli zestawem środowiska uruchomieniowego języka wspólnego (CLR)).  
  
 CV_CFL_JAVA  
 Język aplikacji to Java.  
  
 CV_CFL_JSCRIPT  
 Język aplikacji to JScript.  
  
 CV_CFL_MSIL  
 Język aplikacji jest nieznanego języka pośredniego firmy Microsoft (MSIL), prawdopodobnie z zastosowaniem przełącznika [/LTCG (generowanie kodu w czasie konsolidacji)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) .  
  
 CV_CFL_HLSL  
 Język aplikacji to język modułu cieniującego na wysokim poziomie.  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są zwracane przez wywołanie metody [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst. h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
