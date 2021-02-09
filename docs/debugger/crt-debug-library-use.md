---
title: Biblioteka debugowania CRT Użyj | Microsoft Docs
description: Dowiedz się, w jaki sposób biblioteka środowiska uruchomieniowego C (CRT) obsługuje Twoje działania związane z debugowaniem i co należy zrobić, aby użyć bibliotek debugowania CRT.
ms.custom: SEO-VS-2020
ms.date: 10/03/2019
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe50082f8ff62c4a19b7725facc18f43d672e353
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865712"
---
# <a name="crt-debug-library-use"></a>Korzystanie z biblioteki debugowania CRT
Biblioteka wykonawcza C zapewnia rozbudowaną obsługę debugowania. Aby użyć jednej z bibliotek debugowania CRT, należy połączyć za pomocą [/Debug](/cpp/build/reference/debug-generate-debug-info) i kompilować z **/MDD**, **/MTD** lub **/LDD**.

## <a name="remarks"></a>Uwagi
 Główne definicje i makra dotyczące debugowania CRT można znaleźć w pliku nagłówkowym CRTDBG. h.

 Funkcje w bibliotekach debugowania CRT są kompilowane z informacjami o debugowaniu ([/Z7,/ZD,/Zi,/ZI (format informacji o debugowaniu)](/cpp/build/reference/z7-zi-zi-debug-information-format)i bez optymalizacji. Niektóre funkcje zawierają potwierdzenia do sprawdzenia parametrów, które są przekazywane do nich, a kod źródłowy jest podany. Za pomocą tego kodu źródłowego można wkroczyć do funkcji CRT, aby upewnić się, że funkcje działają zgodnie z oczekiwaniami i sprawdzają, czy istnieją nieprawidłowe parametry lub Stany pamięci. (Niektóre technologie CRT są zastrzeżone i nie dostarczają kodu źródłowego dla obsługi wyjątków, liczby zmiennoprzecinkowej i kilku innych procedur).

 Aby uzyskać więcej informacji na temat różnych bibliotek w czasie wykonywania, których można użyć, zobacz [biblioteki C Run-Time](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Zobacz też

- [Techniki debugowania CRT](../debugger/crt-debugging-techniques.md)
- [/MD,/MT,/LD (Użyj biblioteki Run-Time)](/cpp/build/reference/md-mt-ld-use-run-time-library)