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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
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
/Adres:`yes|no`

Element opcjonalny. Określa, czy mają być wyświetlane adresy pamięci modułów. Wartością `yes`domyślną jest .

/Nazwa:`yes|no`

Element opcjonalny. Określa, czy mają być wyświetlane nazwy modułów. Wartością `yes`domyślną jest .

/Zamówienie:`yes|no`

Element opcjonalny. Określa, czy ma być pokazywany porządek modułów. Wartością `no`domyślną jest .

/Ścieżka:`yes|no`

Element opcjonalny. Określa, czy mają być wyświetlane ścieżki modułów. Wartością `yes`domyślną jest .

/Proces:`yes|no`

Element opcjonalny. Określa, czy mają być wyświetlane procesy modułów. Wartością `no`domyślną jest .

/SymbolFile:`yes|no`

Element opcjonalny. Określa, czy mają być wyświetlane pliki symboli modułów. Wartością `no`domyślną jest .

/SymbolStatus:`yes|no`

Element opcjonalny. Określa, czy mają być wyświetlane stany symboli modułów. Wartością `yes`domyślną jest .

/sygnatura czasowa:`yes|no`

Element opcjonalny. Określa, czy mają być wyświetlane sygnatury czasowe modułów. Wartością `no`domyślną jest .

/Wersja:`yes|no`

Element opcjonalny. Określa, czy mają być wyświetlane wersje modułów. Wartością `no`domyślną jest .

## <a name="example"></a>Przykład
W tym przykładzie wymieniono nazwy modułów, adresy i sygnatury czasowe dla bieżącego procesu.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Instrukcje: korzystanie z okna modułów](../../debugger/how-to-use-the-modules-window.md)
