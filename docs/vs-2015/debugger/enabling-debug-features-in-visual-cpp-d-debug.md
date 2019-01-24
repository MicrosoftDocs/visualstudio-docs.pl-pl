---
title: Włączanie funkcji debugowania w programie Visual C++ (-D_DEBUG) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4cbaa01cfde69db639f354f3d68bd6bbee82efc9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768525"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Włączanie funkcji debugowania w programie Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], funkcji debugowania, takie jak potwierdzenia są włączone, gdy kompilujesz program jest połączony z symbolem **_DEBUG** zdefiniowane. Można zdefiniować **_DEBUG** w jeden z dwóch sposobów:  
  
- Określ **#define _DEBUG** w kodzie źródłowym lub  
  
- Określ **/D_DEBUG** — opcja kompilatora. (Jeśli tworzysz projekt w programie Visual Studio przy użyciu kreatorów, **/D_DEBUG** jest automatycznie zdefiniowana w konfiguracji debugowania.)  
  
  Gdy **_DEBUG** jest zdefiniowany, kompilator kompiluje sekcje kodu ujęte w **#ifdef _DEBUG** i `#endif`.  
  
  Konfiguracja debugowania programu MFC musi łączyć się z wersją debugera biblioteki MFC. W plikach nagłówkowych MFC określić poprawną wersję biblioteki MFC, aby połączyć się z oparte na symbole zdefiniowane, takich jak **_DEBUG** i **_UNICODE**. Aby uzyskać więcej informacji, zobacz [wersje biblioteki MFC](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
