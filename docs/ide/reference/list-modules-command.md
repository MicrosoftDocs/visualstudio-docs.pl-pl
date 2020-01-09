---
title: Lista modułów — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e083a0e1baeefc6807dccb2199cd0e5a9bd883d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595504"
---
# <a name="list-modules-command"></a>Lista modułów — Polecenie
Wyświetla listę modułów dla bieżącego procesu.

## <a name="syntax"></a>Składnia

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametry
/Address:`yes|no`

Opcjonalny. Określa, czy mają być pokazywane adresy pamięci modułów. Wartość domyślna to `yes`.

/Name:`yes|no`

Opcjonalny. Określa, czy mają być wyświetlane nazwy modułów. Wartość domyślna to `yes`.

/Order:`yes|no`

Opcjonalny. Określa, czy ma być wyświetlana kolejność modułów. Wartość domyślna to `no`.

/Path:`yes|no`

Opcjonalny. Określa, czy mają być wyświetlane ścieżki modułów. Wartość domyślna to `yes`.

/Process:`yes|no`

Opcjonalny. Określa, czy mają być wyświetlane procesy modułów. Wartość domyślna to `no`.

/SymbolFile:`yes|no`

Opcjonalny. Określa, czy mają być pokazywane pliki symboli modułów. Wartość domyślna to `no`.

/SymbolStatus:`yes|no`

Opcjonalny. Określa, czy mają być pokazywane Stany symboli modułów. Wartość domyślna to `yes`.

/Timestamp:`yes|no`

Opcjonalny. Określa, czy mają być pokazywane sygnatury czasowe modułów. Wartość domyślna to `no`.

/Version:`yes|no`

Opcjonalny. Określa, czy mają być wyświetlane wersje modułów. Wartość domyślna to `no`.

## <a name="example"></a>Przykład
W tym przykładzie wymieniono nazwy modułów, adresy i sygnatury czasowe dla bieżącego procesu.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Instrukcje: korzystanie z okna modułów](../../debugger/how-to-use-the-modules-window.md)
