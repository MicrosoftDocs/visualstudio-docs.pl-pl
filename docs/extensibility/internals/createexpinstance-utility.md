---
title: Narzędzie CreateExpInstance | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6b302976495e6067fad14317856cda4ac4625f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709240"
---
# <a name="createexpinstance-utility"></a>Narzędzie CreateExpInstance
Narzędzie **CreateExpInstance** służy do tworzenia, resetowania lub usuwania eksperymentalnego wystąpienia programu Visual Studio. Eksperymentalne wystąpienie służy do debugowania i testowania rozszerzeń programu Visual Studio bez zmiany produktu źródłowego.

## <a name="syntax"></a>Składnia

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametry
 **/Utwórz** Tworzy eksperymentalne wystąpienie.

 **/Reset** Usuwa eksperymentalne wystąpienie, a następnie tworzy nowe.

 **/Czyste** Usuwa eksperymentalne wystąpienie.

 **/VSInstance** Nazwa katalogu, który zawiera podstawowe wystąpienie programu Visual Studio do skopiowania.

 **/RootSuffix** Sufiks do dołączania do nazwy katalogu wystąpienia eksperymentalnego.

## <a name="remarks"></a>Uwagi
 Podczas pracy nad rozszerzeniem programu Visual Studio, można nacisnąć klawisz F5, aby otworzyć domyślne wystąpienie eksperymentalne i zainstalować bieżące rozszerzenie. Jeśli nie jest dostępne wystąpienie eksperymentalne, program Visual Studio tworzy taki, który ma ustawienia domyślne.

 Domyślna lokalizacja wystąpienia eksperymentalnego zależy od numeru wersji programu Visual Studio. Na przykład w programie Visual Studio 2015 lokalizacja to *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*. Wszystkie pliki w lokalizacji katalogu są uważane za część tego wystąpienia. Wszelkie dodatkowe wystąpienia eksperymentalne nie zostaną załadowane przez program Visual Studio, chyba że nazwa katalogu zostanie zmieniona na lokalizację domyślną.

 Visual Studio nie uzyskuje dostępu do rejestru systemu po otwarciu wystąpienia eksperymentalnego. Różni się to od wcześniejszych wersji programu Visual Studio, który używał eksperymentalnej wersji gałęzi rejestru.

 Narzędzie **CreateExpInstance** zastępuje narzędzie **VsRegEx.**

 Poniższy przykład resetuje domyślne eksperymentalne wystąpienie programu Visual Studio:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
