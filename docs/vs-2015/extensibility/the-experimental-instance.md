---
title: Wystąpienie eksperymentalne | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee3c1ef0aed082a0e4e0fb519c744fda376fc8e9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430143"
---
# <a name="the-experimental-instance"></a>Wystąpienie eksperymentalne
Zabezpieczenie środowiska deweloperskiego Visual Studio z nieprzetestowanych aplikacji, które może go zmienić, VSSDK miejsce eksperymentalne używanego do eksperymentowania. Twórz nowe aplikacje za pomocą programu Visual Studio w zwykły sposób, ale można je uruchamiać przy użyciu tego wystąpienie eksperymentalne.

 Każda aplikacja, która zawiera pakiet VSIX uruchamia wystąpienie eksperymentalne programu Visual Studio w trybie debugowania.

 Jeśli chcesz uruchomić doświadczalne wystąpienie programu Visual Studio poza konkretnego rozwiązania, uruchom następujące polecenie w oknie wiersza polecenia:

 "*\<Ścieżka instalacji programu visual studio >* \Common7\IDE\devenv.exe" RootSuffix Exp

> [!NOTE]
> Wystąpienie eksperymentalne są zapisywane w kluczu rejestru `<version number>Exp` i `<version number>Exp_Config` węzłów. Na przykład jest obszar rejestru eksperymentalne programu Visual Studio 2015
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` i `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Firma Microsoft zaleca uruchomienie Twojego rozszerzenia w doświadczalnym wystąpieniu podczas jej opracowywania. Podczas wdrażania rozszerzenia, jest uruchamiane w wystąpieniu rozwoju. Aby uzyskać więcej informacji na temat rejestrowania aplikacji, zobacz [rejestrowanie pakietów VSPackage](../extensibility/internals/registering-vspackages.md).