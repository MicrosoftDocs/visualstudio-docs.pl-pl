---
title: Listing — polecenie demontażu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ff5e620d4c53889afe17274364d6f92936025d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672739"
---
# <a name="list-disassembly-command"></a>Lista dezasemblacji — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rozpoczyna proces debugowania i pozwala określić, jak błędy są obsługiwane.

## <a name="syntax"></a>Składnia

```
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Przełączniki
 Każdy przełącznik może być wywoływany przy użyciu kompletnego formularza lub krótkiej formy.

 /Count: `number` [lub]/c: `number` [lub]/length: `number` [lub]/l: `number` opcjonalne. Liczba instrukcji do wyświetlenia. Wartość domyślna to 8.

 /endaddress: `expression` [lub]/e: `expression` opcjonalny. Adres, pod który ma zostać zatrzymany demontaż.

 /codebytes: `yes`&#124;`no` [lub]/bytes: `yes`&#124;`no` [lub]/b: `yes`&#124;`no` opcjonalny. Wskazuje, czy mają być wyświetlane bajty kodu. Wartość domyślna to `no` .

 /source: `yes`&#124;`no` [lub]/s: `yes`&#124;`no` opcjonalny. Wskazuje, czy ma być wyświetlany kod źródłowy. Wartość domyślna to `no` .

 /symbolnames: `yes`&#124;`no` [lub]/names: `yes`&#124;`no` [lub]/n: `yes`&#124;`no` opcjonalny. Wskazuje, czy mają być wyświetlane nazwy symboli. Wartość domyślna to `yes` .

 [/linenumbers: `yes`&#124;`no` ] opcjonalne. Włącza wyświetlanie numerów wierszy skojarzonych z kodem źródłowym. Przełącznik/Source musi mieć wartość, `yes` Aby można było użyć przełącznika/linenumbers.

## <a name="example"></a>Przykład

```
>Debug.ListDisassembly
```

## <a name="see-also"></a>Zobacz też
 [Lista poleceń stosu wywołań](../../ide/reference/list-call-stack-command.md) [List Threads Command](../../ide/reference/list-threads-command.md) poleceń polecenie [Visual Studio](../../ide/reference/visual-studio-commands.md) Commands [okno](../../ide/reference/command-window.md) [Find/Command Box](../../ide/find-command-box.md) [Visual Studio Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
