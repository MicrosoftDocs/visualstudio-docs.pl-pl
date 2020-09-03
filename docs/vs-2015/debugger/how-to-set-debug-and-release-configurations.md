---
title: 'Instrukcje: Ustawianie konfiguracji debugowania i wydania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4984355c12a92529a943fe6778740ac2d7f522f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703636"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Porady: ustawienia konfiguracji Debug i Release
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty programu Visual Studio mają osobne konfiguracje wersji i debugowania dla Twojego programu. Jak nazywają się nazwami, można skompilować wersję debugowania do debugowania i wersję wydania dla ostatecznej dystrybucji wersji.  
  
 Konfiguracja debugowania programu jest skompilowana z pełnymi symbolicznymi informacjami o debugowaniu i bez optymalizacji. Optymalizacja komplikuje debugowanie, ponieważ relacja między kodem źródłowym i wygenerowanymi instrukcjami jest bardziej skomplikowana.  
  
 Konfiguracja wydania programu nie zawiera żadnych symbolicznych informacji o debugowaniu i jest w pełni zoptymalizowana. Informacje debugowania można generować w plikach PDB, w zależności od używanych opcji kompilatora. Tworzenie plików PDB może być bardzo przydatne w przypadku późniejszej debugowania wersji wydania.  
  
 Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).  
  
 Konfigurację kompilacji można zmienić z menu **kompilacja** , na pasku narzędzi lub na stronach właściwości projektu. Strony właściwości projektu są specyficzne dla języka. W poniższej procedurze pokazano, jak zmienić konfigurację kompilacji z menu i paska narzędzi. Aby uzyskać więcej informacji na temat zmiany konfiguracji kompilacji w projektach w różnych językach, zobacz sekcję Tematy pokrewne poniżej.  
  
### <a name="to-change-the-build-configuration"></a>Aby zmienić konfigurację kompilacji  
  
1. W menu Kompilacja kliknij pozycję **kompilacja/Configuration Manager**, a następnie wybierz pozycję **Debuguj** lub **Zwolnij**.  
  
2. Na pasku narzędzi wybierz opcję **Debuguj** lub **Zwolnij** w polu listy **konfiguracje rozwiązań** .  
  
     ![Konfiguracja kompilacji paska narzędzi](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Ten pasek narzędzi nie jest dostępny w wersjach Express. Można użyć elementów menu **Kompiluj rozwiązanie F6** i **Rozpocznij debugowanie F5** , aby wybrać konfigurację.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)   
 [Debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)
