---
title: CV_CFL_LANG — | Dokumentacja firmy Microsoft
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
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6e2aa402d3f882d83525b180707653b97533e32
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724793"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa język kodu źródłowego aplikacji lub połączone modułu.  
  
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
 Język aplikacji jest w języku C++.  
  
 CV_CFL_FORTRAN  
 Język aplikacji jest FORTRAN.  
  
 CV_CFL_MASM  
 Język aplikacji jest Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 Język aplikacji jest Pascal.  
  
 CV_CFL_BASIC  
 Język aplikacji to podstawowa.  
  
 CV_CFL_COBOL  
 Język aplikacji jest COBOL.  
  
 CV_CFL_LINK  
 Aplikacja jest modułem generowanych przez konsolidator.  
  
 CV_CFL_CVTRES  
 Aplikacja jest konwertowane przy użyciu narzędzia CVTRES modułu zasobów.  
  
 CV_CFL_CVTPGD  
 Aplikacja jest generowane przy użyciu narzędzia CVTPGD modułu POGO zoptymalizowane pod kątem.  
  
 CV_CFL_CSHARP  
 Aplikacja językiem jest C#.  
  
 CV_CFL_VB  
 Język aplikacji jest języka Visual Basic.  
  
 CV_CFL_ILASM  
 Język aplikacji jest zestawem języka pośredniego (czyli zestawów środowiska uruchomieniowego języka wspólnego (CLR)).  
  
 CV_CFL_JAVA  
 Język aplikacji jest języka Java.  
  
 CV_CFL_JSCRIPT  
 Aplikacja języka JScript.  
  
 CV_CFL_MSIL  
 Język aplikacji jest nieznany Microsoft Intermediate Language (MSIL), prawdopodobnie wynik za pomocą [opcję/LTCG (Generowanie kodu Link-time)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) przełącznika.  
  
 CV_CFL_HLSL  
 Aplikacja język jest wysoki poziom programu do cieniowania.  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są zwracane przez wywołanie [idiasymbol::get_language —](../../debugger/debug-interface-access/idiasymbol-get-language.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)



