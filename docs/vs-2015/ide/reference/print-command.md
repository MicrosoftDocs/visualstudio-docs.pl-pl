---
title: Polecenie Print | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136edf7fa91e4caeb9303edfd4441ee178fa6038
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662159"
---
# <a name="print-command"></a>Print — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Oblicza wyrażenie lub Wyświetla określony tekst.

## <a name="syntax"></a>Składnia

```
Debug.Print text
```

## <a name="arguments"></a>Argumenty
 `text` Wymagane. Wyrażenie, które ma zostać obliczone lub tekst do wyświetlenia.

## <a name="remarks"></a>Uwagi
 Możesz użyć znaku zapytania (?) jako aliasu dla tego polecenia. Tak więc, na przykład, polecenie

```
>Debug.Print expA
```

 można również napisać

```
>? expA
```

 Obie wersje tego polecenia zwróci bieżącą wartość wyrażenia `expA` .

## <a name="example"></a>Przykład

```
>Debug.Print varA
```

## <a name="see-also"></a>Zobacz też
 [Polecenie oszacowania](../../ide/reference/evaluate-statement-command.md) [poleceń programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno](../../ide/reference/command-window.md) poleceń [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
