---
title: Narzędzie CreateExpInstance | Microsoft Docs
description: Dowiedz się więcej o narzędziu CreateExpInstance, które umożliwia tworzenie, resetowanie lub usuwanie eksperymentalnego wystąpienia Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cce9bc25cb2ed820d3291ab65d94a868bb401ec9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898139"
---
# <a name="createexpinstance-utility"></a>Narzędzie CreateExpInstance
Użyj narzędzia **CreateExpInstance,** aby utworzyć, zresetować lub usunąć eksperymentalne wystąpienie Visual Studio. Wystąpienia eksperymentalnego można użyć do debugowania i testowania Visual Studio bez zmiany produktu bazowego.

## <a name="syntax"></a>Składnia

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametry
 **/Create** Tworzy wystąpienie eksperymentalne.

 **/Reset** Usuwa wystąpienie eksperymentalne, a następnie tworzy nowe.

 **/Clean** Usuwa wystąpienie eksperymentalne.

 **/VSInstance** Nazwa katalogu, który zawiera bazę Visual Studio do skopiowania.

 **/RootSuffix** Sufiks dołączany do nazwy katalogu wystąpienia eksperymentalnego.

## <a name="remarks"></a>Uwagi
 Podczas pracy z rozszerzeniem Visual Studio naciśnij klawisz F5, aby otworzyć domyślne wystąpienie eksperymentalne i zainstalować bieżące rozszerzenie. Jeśli wystąpienie eksperymentalne nie jest dostępne, Visual Studio je, które ma ustawienia domyślne.

 Domyślna lokalizacja wystąpienia eksperymentalnego zależy od Visual Studio wersji. Na przykład w Visual Studio 2015 r. lokalizacja to *%localappdata%\Microsoft\VisualStudio\14.0Exp. \\* Wszystkie pliki w lokalizacji katalogu są traktowane jako część tego wystąpienia. Żadne dodatkowe wystąpienia eksperymentalne nie zostaną załadowane przez Visual Studio chyba że nazwa katalogu zostanie zmieniona na lokalizację domyślną.

 Visual Studio nie uzyskuje dostępu do rejestru systemowego, gdy otwiera wystąpienie eksperymentalne. Różni się to od wcześniejszych wersji Visual Studio, które używały eksperymentalnej wersji gałęzi rejestru.

 Narzędzie **CreateExpInstance** zastępuje narzędzie **VsRegEx.**

 Poniższy przykład resetuje domyślne eksperymentalne wystąpienie Visual Studio:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
