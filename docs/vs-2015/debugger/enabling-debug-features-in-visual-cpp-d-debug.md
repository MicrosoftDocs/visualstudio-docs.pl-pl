---
title: Włączanie funkcji debugowania w Visual C++ (-D_DEBUG) | Microsoft Docs
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
ms.openlocfilehash: cffa8592c2048c6c6b39eee5c4ca654c41448933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686706"
---
# <a name="enabling-debug-features-in-visual-c-d_debug"></a>Włączanie funkcji debugowania w programie Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] funkcje debugowania, takie jak potwierdzenia, są włączane podczas kompilowania programu z zdefiniowanym symbolem **_DEBUG** . **_DEBUG** można definiować na jeden z dwóch sposobów:  
  
- Określ **#define _DEBUG** w kodzie źródłowym lub  
  
- Określ opcję kompilatora **/D_DEBUG** . (Jeśli tworzysz projekt w programie Visual Studio przy użyciu kreatorów, **/D_DEBUG** jest zdefiniowany automatycznie w konfiguracji debugowania).  
  
  Gdy **_DEBUG** jest zdefiniowany, kompilator kompiluje sekcje kodu otoczone **#ifdef _DEBUG** i `#endif` .  
  
  Konfiguracja debugowania programu MFC musi łączyć się z wersją debugowania biblioteki MFC. Pliki nagłówkowe MFC określają poprawną wersję biblioteki MFC do łączenia się na podstawie zdefiniowanych symboli, takich jak **_DEBUG** i **_UNICODE**. Aby uzyskać szczegółowe informacje, zobacz [wersje biblioteki MFC](https://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Ustawienia projektu dla konfiguracji debugowania w C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
