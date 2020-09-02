---
title: Wystąpienie eksperymentalne | Microsoft Docs
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
ms.openlocfilehash: ee3c1ef0aed082a0e4e0fb519c744fda376fc8e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64791278"
---
# <a name="the-experimental-instance"></a>Wystąpienie eksperymentalne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zabezpieczyć środowisko programistyczne programu Visual Studio przed nietestowanymi aplikacjami, które mogą je zmienić, VSSDK zapewnia eksperymentalne miejsce, za pomocą którego można eksperymentować. Tworzysz nowe aplikacje za pomocą programu Visual Studio w zwykły sposób, ale uruchamiasz je przy użyciu tego wystąpienia eksperymentalnego.  
  
 Każda aplikacja z pakietem VSIX uruchamia wystąpienie eksperymentalne programu Visual Studio w trybie debugowania.  
  
 Jeśli chcesz uruchomić eksperymentalne wystąpienie programu Visual Studio poza określonym rozwiązaniem, uruchom następujące polecenie w oknie polecenia:  
  
 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe" EXP/rootsuffix  
  
> [!NOTE]
> Wystąpienie eksperymentalne jest zapisywane w rejestrze w `<version number>Exp` `<version number>Exp_Config` węzłach i. Na przykład obszar rejestru eksperymentalnego programu Visual Studio 2015 to  
>   
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` i `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Zalecamy uruchomienie rozszerzenia w eksperymentalnym wystąpieniu podczas jego tworzenia. Po wdrożeniu rozszerzenia zostanie ono uruchomione w wystąpieniu deweloperskim. Aby uzyskać więcej informacji o rejestrowaniu aplikacji, zobacz [Rejestrowanie pakietów VSPackage](../extensibility/internals/registering-vspackages.md).
