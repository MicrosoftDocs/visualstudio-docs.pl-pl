---
title: Lista źródeł — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5348bd2533a10d98732911a6b7af5410e8ffe42
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031633"
---
# <a name="list-source-command"></a>Lista źródeł — Polecenie
Wyświetla określone linie kodu źródłowego.

## <a name="syntax"></a>Składnia

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Przełączniki
 / Liczba:`number`

 Opcjonalna. Określa liczbę wierszy do wyświetlenia.

 / Bieżąca

 Opcjonalna. Pokazuje bieżący wiersz.

 /File:`filename`

 Opcjonalna. Ścieżka pliku do wyświetlenia. Jeśli nazwa pliku nie zostanie określony, polecenie wyświetla kod źródłowy dla wiersza bieżącej instrukcji.

 / Linii:`number`

 Opcjonalna. Pokazuje określonego numeru wiersza.

 / ShowLineNumbers:`yes|no`

 Opcjonalna. Określa, czy wyświetlanie numerów wierszy.

## <a name="example"></a>Przykład
 W tym przykładzie przedstawiono kod źródłowy z wiersz 4 pliku Form1.vb, za pomocą widoczne numery wierszy.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)