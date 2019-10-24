---
title: Lista źródeł — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c211773f20ab4643b62c8c71fc6ae6581a91987
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747904"
---
# <a name="list-source-command"></a>Lista źródeł — Polecenie
Wyświetla określone wiersze kodu źródłowego.

## <a name="syntax"></a>Składnia

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Przełączniki
/Count: `number`

Opcjonalny. Określa liczbę wierszy do wyświetlenia.

/Current

Opcjonalny. Wyświetla bieżący wiersz.

/File: `filename`

Opcjonalny. Ścieżka pliku do wyświetlenia. Jeśli nazwa pliku nie zostanie określona, polecenie pokazuje kod źródłowy wiersza bieżącej instrukcji.

/Line: `number`

Opcjonalny. Pokazuje określony numer wiersza.

/ShowLineNumbers: `yes|no`

Opcjonalny. Określa, czy mają być wyświetlane numery wierszy.

## <a name="example"></a>Przykład
W tym przykładzie przedstawiono kod źródłowy z wiersza 4 pliku Form1. vb, z widocznymi numerami wierszy.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)