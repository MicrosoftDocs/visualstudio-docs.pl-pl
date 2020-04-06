---
title: Eksperymentalne wystąpienie | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 8e2284767a0aa6be58c0f7e38c912783728914cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699039"
---
# <a name="the-experimental-instance"></a>Wystąpienie eksperymentalne
Aby chronić środowisko programistyczne Visual Studio przed nieprzetestowanymi aplikacjami, które mogą go zmienić, zestaw VSSDK udostępnia przestrzeń eksperymentalną, której można użyć do eksperymentowania. Tworzenie nowych aplikacji przy użyciu programu Visual Studio jak zwykle, ale można je uruchomić przy użyciu tego wystąpienia eksperymentalnego.

 Każda aplikacja, która ma pakiet VSIX uruchamia wystąpienie eksperymentalne programu Visual Studio w trybie debugowania.

 Jeśli chcesz uruchomić eksperymentalne wystąpienie programu Visual Studio poza określonym rozwiązaniem, uruchom następujące polecenie w oknie polecenia:

 "*\<Ścieżka instalacji programu Visual Studio>* \Common7\IDE\devenv.exe" /RootSuffix Exp

> [!NOTE]
> Eksperymentalne wystąpienie jest zapisywane `<version number>Exp` w `<version number>Exp_Config` rejestrze w i węzłów. Na przykład eksperymentalny obszar rejestru programu Visual Studio 2015 jest
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` i `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Zaleca się uruchomienie rozszerzenia w wystąpieniu eksperymentalnym podczas jego opracowywania. Po wdrożeniu rozszerzenia, działa w wystąpieniu dewelopera. Aby uzyskać więcej informacji na temat rejestrowania aplikacji, zobacz [Rejestrowanie pakietów VSPackages](../extensibility/internals/registering-vspackages.md).
