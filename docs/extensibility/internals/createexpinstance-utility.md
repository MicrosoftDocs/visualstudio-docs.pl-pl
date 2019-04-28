---
title: Narzędzie CreateExpInstance | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c4f77d0eba4ca974522534c69d554af9d807a9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861922"
---
# <a name="createexpinstance-utility"></a>Narzędzie CreateExpInstance
Użyj **CreateExpInstance** narzędzie do tworzenia, zresetuj lub Usuń wystąpienie doświadczalne programu Visual Studio. Wystąpienie eksperymentalne umożliwia debugowanie i testowanie rozszerzenia programu Visual Studio bez zmiany podstawowego produktu.

## <a name="syntax"></a>Składnia

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametry
 **/ Tworzenie** tworzy wystąpienie eksperymentalne.

 **/ Resetowanie** usuwa wystąpienie eksperymentalne programu, a następnie tworzy nową.

 **/ Czyszczenie** usuwa wystąpienie eksperymentalne.

 **/ VSInstance** nazwę katalogu, który zawiera wystąpienie programu Visual Studio w podstawowej, aby skopiować.

 **/ RootSuffix** sufiks, który można dołączyć do nazwy katalogu, w eksperymentalnym wystąpieniu.

## <a name="remarks"></a>Uwagi
 Podczas pracy w rozszerzeniu Visual Studio, można nacisnąć F5, aby otworzyć domyślne wystąpienie doświadczalne i zainstaluj rozszerzenie bieżącego. Jeśli żadne wystąpienie doświadczalne jest dostępny, program Visual Studio tworzy jeden, który zawiera ustawienia domyślne.

 Domyślna lokalizacja wystąpienie doświadczalne zależy od numeru wersji programu Visual Studio. Na przykład dla programu Visual Studio 2015, lokalizacja jest *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*. Wszystkie pliki w lokalizacji katalogu są traktowane jako część tego wystąpienia. Wszelkie dodatkowe wystąpienia doświadczalnego nie zostanie załadowany przez program Visual Studio, chyba, że nazwa katalogu jest zmieniana na lokalizację domyślną.

 Program Visual Studio nie uzyskać dostępu do rejestru systemowego, po otwarciu wystąpienie eksperymentalne. Różni się to z wcześniejszych wersji programu Visual Studio, które są używane w wersji doświadczalnej gałęzi rejestru.

 **CreateExpInstance** zastępuje narzędzie **VsRegEx** narzędzia.

 Poniższy przykład Resetuje domyślne doświadczalnym wystąpieniu programu Visual Studio:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Zobacz także
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)