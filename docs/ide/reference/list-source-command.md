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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
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
/Count:`number`

Element opcjonalny. Określa liczbę wyświetlanych linii.

/Prąd

Element opcjonalny. Pokazuje bieżący wiersz.

/Plik:`filename`

Element opcjonalny. Ścieżka pliku do wyświetlenia. Jeśli nie określono nazwy pliku, polecenie pokazuje kod źródłowy wiersza bieżącej instrukcji.

/Linia:`number`

Element opcjonalny. Pokazuje określony numer wiersza.

/ShowLineNumbers:`yes|no`

Element opcjonalny. Określa, czy mają być wyświetlane numery wierszy.

## <a name="example"></a>Przykład
W tym przykładzie wyszczeli się kod źródłowy z wiersza 4 pliku Form1.vb z widocznymi numerami wierszy.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)