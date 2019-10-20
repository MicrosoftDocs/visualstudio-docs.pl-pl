---
title: Polecenie list Source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f13689b6e3ac4db2d58c1def3a5d0dd05c219f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672318"
---
# <a name="list-source-command"></a>Lista źródeł — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla określone wiersze kodu źródłowego.

## <a name="syntax"></a>Składnia

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Przełączniki
 /Count: `number` opcjonalny. Określa liczbę wierszy do wyświetlenia.

 /Current opcjonalne. Wyświetla bieżący wiersz.

 /File: `filename` opcjonalny. Ścieżka pliku do wyświetlenia. Jeśli nazwa pliku nie zostanie określona, polecenie pokazuje kod źródłowy wiersza bieżącej instrukcji.

 /Line: `number` opcjonalny. Pokazuje określony numer wiersza.

 /ShowLineNumbers: `yes|no` opcjonalny. Określa, czy mają być wyświetlane numery wierszy.

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład
 W tym przykładzie przedstawiono kod źródłowy z wiersza 4 pliku Form1. vb, z widocznymi numerami wierszy.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Zobacz też
 [Okno poleceń](../../ide/reference/command-window.md) [poleceń programu Visual Studio](../../ide/reference/visual-studio-commands.md)
