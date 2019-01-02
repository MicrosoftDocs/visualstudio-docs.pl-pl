---
title: Korzystanie z biblioteki debugowania CRT | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 79f75cf227826ec0f9d35d9a7564bbdc25a3cd0f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890907"
---
# <a name="crt-debug-library-use"></a>Korzystanie z biblioteki debugowania CRT
Biblioteki wykonawczej C zapewnia rozbudowaną obsługę debugowania. Aby użyć jednego z biblioteki debugowania CRT, należy połączyć z [/DEBUG](/cpp/build/reference/debug-generate-debug-info) i skompiluj z **/mdd**, **/mtd**, lub **/LDd**.  
  
## <a name="remarks"></a>Uwagi  
 Definicje głównego i makra dla debugowania CRT, można znaleźć w pliku nagłówkowym CRTDBG.h.  
  
 Funkcje z biblioteki debugowania CRT są kompilowane przy użyciu informacji o debugowaniu ([/z7, / zd, / zi, /ZI (Format informacji debugowania)](/cpp/build/reference/z7-zi-zi-debug-information-format)) i bez optymalizacji. Niektóre funkcje zawierać potwierdzenia, aby sprawdzić parametry przekazywane do nich i znajduje się kod źródłowy. Przy użyciu tego kodu źródłowego możesz wejść do funkcji CRT, aby upewnić się, że funkcje działają spodziewać się i sprawdź stany złych parametrów lub pamięci. (Niektóre technologii CRT jest zastrzeżone i nie zawiera kodu źródłowego dla obsługi wyjątków, zmiennoprzecinkowych i kilka innych procedur).  
  
 Po zainstalowaniu programu Visual C++, istnieje możliwość instalowania kod źródłowy biblioteki wykonawczej języka C na dysku twardym. Jeśli kod źródłowy nie jest zainstalowany, należy dysku CD-ROM, aby wejść do funkcji CRT.  
  
 Aby uzyskać więcej informacji na temat różnych bibliotek środowiska uruchomieniowego, można użyć, zobacz [C Run-Time Libraries](/cpp/c-runtime-library/crt-library-features).  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (Korzystaj z bibliotek wykonawczych)](/cpp/build/reference/md-mt-ld-use-run-time-library)