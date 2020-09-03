---
title: List modułów — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4600f27f62d6e840041a65b4128df128e4d36873
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659530"
---
# <a name="list-modules-command"></a>Lista modułów — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla listę modułów dla bieżącego procesu.

## <a name="syntax"></a>Składnia

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametry
 /Address: `yes|no` opcjonalne. Określa, czy mają być pokazywane adresy pamięci modułów. Wartość domyślna to `yes` .

 /Name: `yes|no` opcjonalny. Określa, czy mają być wyświetlane nazwy modułów. Wartość domyślna to `yes` .

 /Order: `yes|no` opcjonalne. Określa, czy ma być wyświetlana kolejność modułów. Wartość domyślna to `no` .

 /Path: `yes|no` opcjonalne. Określa, czy mają być wyświetlane ścieżki modułów. Wartość domyślna to `yes` .

 /Process: `yes|no` opcjonalne. Określa, czy mają być wyświetlane procesy modułów. Wartość domyślna to `no` .

 /SymbolFile: `yes|no` opcjonalne. Określa, czy mają być pokazywane pliki symboli modułów. Wartość domyślna to `no` .

 /SymbolStatus: `yes|no` opcjonalne. Określa, czy mają być pokazywane Stany symboli modułów. Wartość domyślna to `yes` .

 /Timestamp: `yes|no` opcjonalne. Określa, czy mają być pokazywane sygnatury czasowe modułów. Wartość domyślna to `no` .

 /Version: `yes|no` opcjonalny. Określa, czy mają być wyświetlane wersje modułów. Wartość domyślna to `no` .

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład
 W tym przykładzie wymieniono nazwy modułów, adresy i sygnatury czasowe dla bieżącego procesu.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Zobacz też
 Okno poleceń [poleceń programu Visual Studio](../../ide/reference/visual-studio-commands.md) [Command Window](../../ide/reference/command-window.md) [instrukcje: korzystanie z okna moduły](../../debugger/how-to-use-the-modules-window.md)
