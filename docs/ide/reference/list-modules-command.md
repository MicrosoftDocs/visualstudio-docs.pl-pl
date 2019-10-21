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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1fef8f314f5b416edcf40c8b2f7da4eaa471a28c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610653"
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
/Address: `yes|no`

Opcjonalny. Określa, czy mają być pokazywane adresy pamięci modułów. Wartość domyślna to `yes`.

/Name: `yes|no`

Opcjonalny. Określa, czy mają być wyświetlane nazwy modułów. Wartość domyślna to `yes`.

/Order: `yes|no`

Opcjonalny. Określa, czy ma być wyświetlana kolejność modułów. Wartość domyślna to `no`.

/Path: `yes|no`

Opcjonalny. Określa, czy mają być wyświetlane ścieżki modułów. Wartość domyślna to `yes`.

/Process: `yes|no`

Opcjonalny. Określa, czy mają być wyświetlane procesy modułów. Wartość domyślna to `no`.

/SymbolFile: `yes|no`

Opcjonalny. Określa, czy mają być pokazywane pliki symboli modułów. Wartość domyślna to `no`.

/SymbolStatus: `yes|no`

Opcjonalny. Określa, czy mają być pokazywane Stany symboli modułów. Wartość domyślna to `yes`.

/Timestamp: `yes|no`

Opcjonalny. Określa, czy mają być pokazywane sygnatury czasowe modułów. Wartość domyślna to `no`.

/Version: `yes|no`

Opcjonalny. Określa, czy mają być wyświetlane wersje modułów. Wartość domyślna to `no`.

## <a name="example"></a>Przykład
W tym przykładzie wymieniono nazwy modułów, adresy i sygnatury czasowe dla bieżącego procesu.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Instrukcje: korzystanie z okna modułów](../../debugger/how-to-use-the-modules-window.md)