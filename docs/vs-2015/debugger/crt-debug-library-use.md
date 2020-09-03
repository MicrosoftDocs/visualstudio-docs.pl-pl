---
title: Biblioteka debugowania CRT Użyj | Microsoft Docs
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
ms.openlocfilehash: 7e14a181b432dede3f00a4465d40154fdb393bb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697855"
---
# <a name="crt-debug-library-use"></a>Korzystanie z biblioteki debugowania CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Biblioteka wykonawcza C zapewnia rozbudowaną obsługę debugowania. Aby użyć jednej z bibliotek debugowania CRT, należy połączyć za pomocą [/Debug](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) i kompilować z **/MDD**, **/MTD**lub **/LDD**.  
  
## <a name="remarks"></a>Uwagi  
 Główne definicje i makra dotyczące debugowania CRT można znaleźć w pliku nagłówkowym CRTDBG. h.  
  
 Funkcje w bibliotekach debugowania CRT są kompilowane z informacjami o debugowaniu ([/Z7,/ZD,/Zi,/ZI (format informacji o debugowaniu)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)i bez optymalizacji. Niektóre funkcje zawierają potwierdzenia do sprawdzenia parametrów, które są przekazywane do nich, a kod źródłowy jest podany. Za pomocą tego kodu źródłowego można wkroczyć do funkcji CRT, aby upewnić się, że funkcje działają zgodnie z oczekiwaniami i sprawdzają, czy istnieją nieprawidłowe parametry lub Stany pamięci. (Niektóre technologie CRT są zastrzeżone i nie dostarczają kodu źródłowego dla obsługi wyjątków, liczby zmiennoprzecinkowej i kilku innych procedur).  
  
 Podczas instalowania Visual C++ można zainstalować kod źródłowy biblioteki wykonawczej C na dysku twardym. Jeśli nie zainstalujesz kodu źródłowego, będziesz potrzebować dysku CD-ROM, aby przejść do funkcji CRT.  
  
 Aby uzyskać więcej informacji na temat różnych bibliotek czasu wykonywania, których można użyć, zobacz [biblioteki uruchomieniowe języka C](https://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f).  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki debugowania CRT](../debugger/crt-debugging-techniques.md)   
 [/MD,/MT,/LD (Korzystaj z bibliotek Run-Time)](https://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)
