---
title: Wystąpienie eksperymentalne | Microsoft Docs
description: Dowiedz się, jak zestaw SDK programu Visual Studio zapewnia eksperymentalne miejsce do uruchamiania nietestowanych aplikacji w trybie debugowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4786f450b108c8a6c1eaefc6f86f7adf57e9269e
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715863"
---
# <a name="the-experimental-instance"></a>Wystąpienie eksperymentalne
Aby zabezpieczyć środowisko programistyczne programu Visual Studio przed nietestowanymi aplikacjami, które mogą je zmienić, VSSDK zapewnia eksperymentalne miejsce, za pomocą którego można eksperymentować. Tworzysz nowe aplikacje za pomocą programu Visual Studio w zwykły sposób, ale uruchamiasz je przy użyciu tego wystąpienia eksperymentalnego.

 Każda aplikacja z pakietem VSIX uruchamia wystąpienie eksperymentalne programu Visual Studio w trybie debugowania.

 Jeśli chcesz uruchomić eksperymentalne wystąpienie programu Visual Studio poza określonym rozwiązaniem, uruchom następujące polecenie w oknie polecenia:

 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe" EXP/rootsuffix

> [!NOTE]
> Wystąpienie eksperymentalne jest zapisywane w rejestrze w `<version number>Exp` `<version number>Exp_Config` węzłach i. Na przykład obszar rejestru eksperymentalnego programu Visual Studio 2015 to
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` i `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Zalecamy uruchomienie rozszerzenia w eksperymentalnym wystąpieniu podczas jego tworzenia. Po wdrożeniu rozszerzenia zostanie ono uruchomione w wystąpieniu deweloperskim. Aby uzyskać więcej informacji o rejestrowaniu aplikacji, zobacz [Rejestrowanie pakietów VSPackage](../extensibility/internals/registering-vspackages.md).
