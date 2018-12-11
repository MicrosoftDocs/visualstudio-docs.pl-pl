---
title: Eksperymentalne wystąpienie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c80c071866e46528fe7edd287e082df3af166973
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138928"
---
# <a name="the-experimental-instance"></a>Eksperymentalne wystąpienie programu
Do ochrony środowiska deweloperskiego Visual Studio z zastosowaniem aplikacji, które może go zmienić, VSSDK miejsce eksperymentalne używanej do wykonywania eksperymentów. Tworzenie nowej aplikacji za pomocą programu Visual Studio w zwykły sposób, ale Uruchom za pomocą tego eksperymentalne wystąpienie.  
  
 Każda aplikacja, która zawiera pakiet VSIX uruchamia eksperymentalne wystąpienie programu Visual Studio w trybie debugowania.  
  
 Jeśli chcesz Uruchom eksperymentalne wystąpienie programu Visual Studio poza konkretnego rozwiązania, uruchom następujące polecenie w oknie wiersza polecenia:  
  
 "*\<Ścieżki instalacji programu visual studio >* \Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  Eksperymentalne wystąpienie są zapisywane w kluczu rejestru `<version number>Exp` i `<version number>Exp_Config` węzłów. Na przykład jest obszar eksperymentalne rejestru programu Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` I `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Zaleca się uruchomienie rozszerzenia w eksperymentalnym wystąpieniu podczas jego tworzenia. Podczas wdrażania rozszerzenia jest uruchamiany w przypadku rozwoju. Aby uzyskać więcej informacji na temat rejestrowania aplikacji, zobacz [rejestrowanie VSPackages](../extensibility/internals/registering-vspackages.md).