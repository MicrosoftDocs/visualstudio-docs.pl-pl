---
title: Włączanie funkcji debugowania w programie Visual C++ (-D_DEBUG) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2c18dfec1f6d1581f926fa24d006b3761c2f6fce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976251"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Włączanie funkcji debugowania w programie Visual C++ (/D_DEBUG)
W [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], funkcji debugowania, takie jak potwierdzenia są włączone, gdy kompilujesz program jest połączony z symbolem **_DEBUG** zdefiniowane. Można zdefiniować **_DEBUG** w jeden z dwóch sposobów:  
  
- Określ **#define _DEBUG** w kodzie źródłowym lub  
  
- Określ **/D_DEBUG** — opcja kompilatora. (Jeśli tworzysz projekt w programie Visual Studio przy użyciu kreatorów, **/D_DEBUG** jest automatycznie zdefiniowana w konfiguracji debugowania.)  
  
  Gdy **_DEBUG** jest zdefiniowany, kompilator kompiluje sekcje kodu ujęte w **#ifdef _DEBUG** i `#endif`.  
  
  Konfiguracja debugowania programu MFC musi łączyć się z wersją debugera biblioteki MFC. W plikach nagłówkowych MFC określić poprawną wersję biblioteki MFC, aby połączyć się z oparte na symbole zdefiniowane, takich jak **_DEBUG** i **_UNICODE**. Aby uzyskać więcej informacji, zobacz [wersje biblioteki MFC](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)