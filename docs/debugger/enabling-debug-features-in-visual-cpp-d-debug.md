---
title: Włączanie funkcji debugowania w projektach C++ (-D_DEBUG) | Microsoft Docs
description: W Visual C++ włączeniu funkcji debugowania przez zdefiniowanie _DEBUG. Dowiedz się, jak to zrobić, i Dowiedz się, jak połączyć program MFC w celu jego debugowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: c0a8941fbda263ce3a2345a135594d2f9eec87e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871900"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Włączanie funkcji debugowania w projektach C++ (/D_DEBUG)
W programie [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] funkcje debugowania, takie jak potwierdzenia, są włączane podczas kompilowania programu z zdefiniowanym symbolem **_DEBUG** . **_DEBUG** można definiować na jeden z dwóch sposobów:

- Określ **#define _DEBUG** w kodzie źródłowym lub

- Określ opcję kompilatora **/D_DEBUG** . (Jeśli tworzysz projekt w programie Visual Studio przy użyciu kreatorów, **/D_DEBUG** jest zdefiniowany automatycznie w konfiguracji debugowania).

  Gdy **_DEBUG** jest zdefiniowany, kompilator kompiluje sekcje kodu otoczone **#ifdef _DEBUG** i `#endif` .

  Konfiguracja debugowania programu MFC musi łączyć się z wersją debugowania biblioteki MFC. Pliki nagłówkowe MFC określają poprawną wersję biblioteki MFC do łączenia się na podstawie zdefiniowanych symboli, takich jak **_DEBUG** i **_UNICODE**. Aby uzyskać szczegółowe informacje, zobacz [wersje biblioteki MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)