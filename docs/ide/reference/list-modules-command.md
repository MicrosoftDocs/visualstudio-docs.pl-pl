---
title: Lista modułów — Polecenie
description: Informacje na temat poleceń list modułów i sposobu wyświetlania listy modułów dla bieżącego procesu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a38a5423568528d267fd92894b8b06b4e5667c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852066"
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
Ulica`yes|no`

Opcjonalny. Określa, czy mają być pokazywane adresy pamięci modułów. Wartość domyślna to `yes`.

Nazwij`yes|no`

Opcjonalny. Określa, czy mają być wyświetlane nazwy modułów. Wartość domyślna to `yes`.

Porządek`yes|no`

Opcjonalny. Określa, czy ma być wyświetlana kolejność modułów. Wartość domyślna to `no`.

Ścieżka`yes|no`

Opcjonalny. Określa, czy mają być wyświetlane ścieżki modułów. Wartość domyślna to `yes`.

Podstawowych`yes|no`

Opcjonalny. Określa, czy mają być wyświetlane procesy modułów. Wartość domyślna to `no`.

SymbolFile`yes|no`

Opcjonalny. Określa, czy mają być pokazywane pliki symboli modułów. Wartość domyślna to `no`.

Stansymboli`yes|no`

Opcjonalny. Określa, czy mają być pokazywane Stany symboli modułów. Wartość domyślna to `yes`.

Znacznik czasu`yes|no`

Opcjonalny. Określa, czy mają być pokazywane sygnatury czasowe modułów. Wartość domyślna to `no`.

Nowszym`yes|no`

Opcjonalny. Określa, czy mają być wyświetlane wersje modułów. Wartość domyślna to `no`.

## <a name="example"></a>Przykład
W tym przykładzie wymieniono nazwy modułów, adresy i sygnatury czasowe dla bieżącego procesu.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Instrukcje: korzystanie z okna modułów](../../debugger/how-to-use-the-modules-window.md)
