---
title: Narzędzie CreateExpInstance | Microsoft Docs
description: Dowiedz się więcej na temat narzędzia CreateExpInstance, które umożliwia tworzenie, Resetowanie lub usuwanie eksperymentalnego wystąpienia programu Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c02e85a96d59645787d3018100949369d52c8980
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305371"
---
# <a name="createexpinstance-utility"></a>Narzędzie CreateExpInstance
Użyj narzędzia **CreateExpInstance** , aby utworzyć, zresetować lub usunąć eksperymentalne wystąpienie programu Visual Studio. Możesz użyć eksperymentalnego wystąpienia do debugowania i testowania rozszerzeń programu Visual Studio bez zmiany bazowego produktu.

## <a name="syntax"></a>Składnia

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametry
 **/Create** Tworzy wystąpienie eksperymentalne.

 **/Reset** Usuwa wystąpienie eksperymentalne, a następnie tworzy nowe.

 **/Clean** Usuwa wystąpienie eksperymentalne.

 **/VSInstance** Nazwa katalogu zawierającego podstawowe wystąpienie programu Visual Studio do skopiowania.

 **/Rootsuffix** Sufiks do dołączenia do nazwy eksperymentalnego katalogu wystąpień.

## <a name="remarks"></a>Uwagi
 Podczas pracy nad rozszerzeniem programu Visual Studio można nacisnąć klawisz F5, aby otworzyć domyślne wystąpienie eksperymentalne i zainstalować bieżące rozszerzenie. Jeśli żadne wystąpienie eksperymentalne nie jest dostępne, program Visual Studio tworzy taki, który ma ustawienia domyślne.

 Domyślna lokalizacja wystąpienia doświadczalnego zależy od numeru wersji programu Visual Studio. Na przykład w przypadku programu Visual Studio 2015 lokalizacją jest *%LocalAppData%\Microsoft\VisualStudio\14.0Exp \\*. Wszystkie pliki w lokalizacji w katalogu są uważane za część tego wystąpienia. Wszystkie dodatkowe eksperymentalne wystąpienia nie zostaną załadowane przez program Visual Studio, chyba że nazwa katalogu zostanie zmieniona na lokalizację domyślną.

 Program Visual Studio nie uzyskuje dostępu do rejestru systemowego, gdy otwiera wystąpienie eksperymentalne. Różni się to od wcześniejszych wersji programu Visual Studio, które używały eksperymentalnej wersji gałęzi rejestru.

 Narzędzie **CreateExpInstance** zastępuje narzędzie **VsRegEx** .

 Poniższy przykład resetuje domyślne wystąpienie eksperymentalne programu Visual Studio:

 **CreateExpInstance.exe/Reset/VSInstance = 14.0/RootSuffix = EXP**

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
