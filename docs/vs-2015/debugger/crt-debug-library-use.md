---
title: Korzystanie z biblioteki debugowania CRT | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51534d226f3ae0f8726bb818423bf0a9b788fd8c
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834658"
---
# <a name="crt-debug-library-use"></a>Korzystanie z biblioteki debugowania CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Biblioteki wykonawczej C zapewnia rozbudowaną obsługę debugowania. Aby użyć jednego z biblioteki debugowania CRT, należy połączyć z [/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) i skompiluj z **/mdd**, **/mtd**, lub **/LDd**.  
  
## <a name="remarks"></a>Uwagi  
 Definicje głównego i makra dla debugowania CRT, można znaleźć w pliku nagłówkowym CRTDBG.h.  
  
 Funkcje z biblioteki debugowania CRT są kompilowane przy użyciu informacji o debugowaniu ([/z7, / zd, / zi, /ZI (Format informacji debugowania)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)) i bez optymalizacji. Niektóre funkcje zawierać potwierdzenia, aby sprawdzić parametry przekazywane do nich i znajduje się kod źródłowy. Przy użyciu tego kodu źródłowego możesz wejść do funkcji CRT, aby upewnić się, że funkcje działają spodziewać się i sprawdź stany złych parametrów lub pamięci. (Niektóre technologii CRT jest zastrzeżone i nie zawiera kodu źródłowego dla obsługi wyjątków, zmiennoprzecinkowych i kilka innych procedur).  
  
 Po zainstalowaniu programu Visual C++, istnieje możliwość instalowania kod źródłowy biblioteki wykonawczej języka C na dysku twardym. Jeśli kod źródłowy nie jest zainstalowany, należy dysku CD-ROM, aby wejść do funkcji CRT.  
  
 Aby uzyskać więcej informacji na temat różnych bibliotek środowiska uruchomieniowego, można użyć, zobacz [C Run-Time Libraries](http://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f).  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (Korzystaj z bibliotek wykonawczych)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)
