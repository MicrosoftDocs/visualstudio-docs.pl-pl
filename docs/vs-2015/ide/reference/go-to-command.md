---
title: Przejdź do polecenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 454b51b6939a78cdaab8d29f51d30910024adbe3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661200"
---
# <a name="go-to-command"></a>Przejdź do — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Przenosi kursor do określonego wiersza.

## <a name="syntax"></a>Składnia

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumenty
 `linenumber` opcjonalny. Liczba całkowita reprezentująca liczbę wierszy, które mają zostać przechodzenie.

## <a name="remarks"></a>Uwagi
 Numerowanie wierszy rozpoczyna się od jednej. Jeśli wartość `linenumber` jest mniejsza od 1, zostanie wyświetlona pierwsza linia. Jeśli wartość `linenumber` jest większa niż liczba ostatniego wiersza, zostanie wyświetlony ostatni wiersz.

 Jeśli nie określono wartości dla `linenumber`, zostanie wyświetlone okno dialogowe **Przejdź do wiersza** .

 Alias dla tego polecenia to GoToLn.

## <a name="example"></a>Przykład

```
>Edit.GoTo 125
```

## <a name="see-also"></a>Zobacz też
 Polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno](../../ide/reference/command-window.md) poleceń [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
