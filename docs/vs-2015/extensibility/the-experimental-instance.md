---
title: Wystąpienie eksperymentalne | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 907b90f60ad2167b64e5a4ca8ff160190c625313
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760975"
---
# <a name="the-experimental-instance"></a>Wystąpienie eksperymentalne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zabezpieczenie środowiska deweloperskiego Visual Studio z nieprzetestowanych aplikacji, które może go zmienić, VSSDK miejsce eksperymentalne używanego do eksperymentowania. Twórz nowe aplikacje za pomocą programu Visual Studio w zwykły sposób, ale można je uruchamiać przy użyciu tego wystąpienie eksperymentalne.  
  
 Każda aplikacja, która zawiera pakiet VSIX uruchamia wystąpienie eksperymentalne programu Visual Studio w trybie debugowania.  
  
 Jeśli chcesz uruchomić doświadczalne wystąpienie programu Visual Studio poza konkretnego rozwiązania, uruchom następujące polecenie w oknie wiersza polecenia:  
  
 "*\<Ścieżka instalacji programu visual studio >* \Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  Wystąpienie eksperymentalne są zapisywane w kluczu rejestru `<version number>Exp` i `<version number>Exp_Config` węzłów. Na przykład jest obszar rejestru eksperymentalne programu Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` i `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Firma Microsoft zaleca uruchomienie Twojego rozszerzenia w doświadczalnym wystąpieniu podczas jej opracowywania. Podczas wdrażania rozszerzenia, jest uruchamiane w wystąpieniu rozwoju. Aby uzyskać więcej informacji na temat rejestrowania aplikacji, zobacz [rejestrowanie pakietów VSPackage](../extensibility/internals/registering-vspackages.md).
