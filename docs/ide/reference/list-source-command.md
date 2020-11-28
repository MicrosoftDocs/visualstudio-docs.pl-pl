---
title: Lista źródeł — Polecenie
description: Dowiedz się więcej o poleceniu list Source i sposobie wyświetlania określonych wierszy kodu źródłowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae2463a3d8dd295fcba9bf264e1ad3fa250169d4
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305289"
---
# <a name="list-source-command"></a>Lista źródeł — Polecenie
Wyświetla określone wiersze kodu źródłowego.

## <a name="syntax"></a>Składnia

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Przełączniki
Liczbą`number`

Opcjonalny. Określa liczbę wierszy do wyświetlenia.

/Current

Opcjonalny. Wyświetla bieżący wiersz.

Rozszerzeniem`filename`

Opcjonalny. Ścieżka pliku do wyświetlenia. Jeśli nazwa pliku nie zostanie określona, polecenie pokazuje kod źródłowy wiersza bieżącej instrukcji.

Liniow`number`

Opcjonalny. Pokazuje określony numer wiersza.

ShowLineNumbers`yes|no`

Opcjonalny. Określa, czy mają być wyświetlane numery wierszy.

## <a name="example"></a>Przykład
W tym przykładzie przedstawiono kod źródłowy z wiersza 4 pliku Form1. vb, z widocznymi numerami wierszy.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)