---
title: Włączanie funkcji debugowania w C++ projektach (-D_DEBUG) | Microsoft Docs
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 19d341cba47e0a3d2259cc57d239c63420095347
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737954"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Włączanie funkcji debugowania w C++ projektach (/D_DEBUG)
W [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]funkcje debugowania, takie jak potwierdzenia, są włączane podczas kompilowania programu z zdefiniowanym symbolem **_DEBUG** . Można zdefiniować **_DEBUG** na jeden z dwóch sposobów:

- Określ **#define _DEBUG** w kodzie źródłowym lub

- Określ opcję kompilatora **/D_DEBUG** . (Jeśli tworzysz projekt w programie Visual Studio przy użyciu kreatorów, **/D_DEBUG** jest definiowana automatycznie w konfiguracji debugowania).

  Gdy **_DEBUG** jest zdefiniowany, kompilator kompiluje sekcje kodu otoczone **#ifdef _DEBUG** i `#endif`.

  Konfiguracja debugowania programu MFC musi łączyć się z wersją debugowania biblioteki MFC. Pliki nagłówkowe MFC określają poprawną wersję biblioteki MFC do łączenia się na podstawie zdefiniowanych symboli, takich jak **_DEBUG** i **_UNICODE**. Aby uzyskać szczegółowe informacje, zobacz [wersje biblioteki MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Zobacz także
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)