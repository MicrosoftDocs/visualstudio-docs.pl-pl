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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f162590fafaa263e9cc4233744e5f2ba39c8ce6f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926182"
---
# <a name="list-source-command"></a>Lista źródeł — Polecenie
Wyświetla określone linie kodu źródłowego.

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

Opcjonalna. Ścieżka pliku do wyświetlenia. Jeśli nazwa pliku nie zostanie określona, polecenie pokazuje kod źródłowy wiersza bieżącej instrukcji.

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
- [Okno Polecenie](../../ide/reference/command-window.md)