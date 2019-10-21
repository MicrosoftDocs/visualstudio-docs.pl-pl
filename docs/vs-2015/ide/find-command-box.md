---
title: Find — pole polecenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b7c5f9c19573a04b1d9a8d7b8c6e9450aef9bc44
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645730"
---
# <a name="findcommand-box"></a>Find/Command — Pole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wyszukiwać tekst i uruchamiać polecenia programu Visual Studio z poziomu pola **Znajdź/polecenie** . Pole **Znajdź/polecenie** jest nadal dostępne jako kontrolka paska narzędzi, ale nie jest już widoczne domyślnie. Możesz wyświetlić okno **Znajdź/polecenie** , wybierając pozycję **Dodaj lub usuń przyciski** na pasku narzędzi **Standardowy** , a następnie wybierając pozycję **Znajdź**.

 Aby uruchomić polecenie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], należy oznakować je znakiem większym niż (>).

 Okno **Znajdź/polecenie** zachowuje ostatnie 20 wprowadzonych elementów i wyświetla je na liście rozwijanej. Możesz przechodzić przez listę, wybierając klawisze strzałek.

 ![Znajdź&#47;pole polecenia](../ide/media/findcommandbox.png "FindCommandBox") Znajdź/pole polecenia

## <a name="searching-for-text"></a>Wyszukiwanie tekstu
 Domyślnie po określeniu tekstu w polu **Znajdź/polecenie** , a następnie wybraniu klawisza ENTER, program Visual Studio przeszukuje bieżący dokument lub okno narzędzia przy użyciu opcji określonych w oknie dialogowym **Znajdź w plikach** . Aby uzyskać więcej informacji, zobacz [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Wprowadzanie poleceń
 Aby użyć pola **Znajdź/polecenie** do wydawania jednego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]go polecenia lub aliasu zamiast wyszukiwania tekstu, wprowadź polecenie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], poprzedzone symbolem większym niż (>). Na przykład:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

 Alternatywnie można również użyć okno Polecenie do wprowadzania i wykonywania pojedynczych lub wielu poleceń. Niektóre polecenia lub aliasy mogą być wprowadzane i wykonywane samodzielnie; inne osoby mają wymagane argumenty w składni. Aby zapoznać się z listą poleceń, które mają argumenty, zobacz [Visual Studio Commands](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Znaki ucieczki
 Znak daszka (^) w wierszu polecenia oznacza, że znak bezpośrednio po nim jest interpretowany dosłownie, a nie jako znak kontrolny. Można go użyć do osadzenia prostych cudzysłowów ("), spacji, ukośników wiodących, karetki lub innych znaków literału w wartości parametru lub przełącznika, z wyjątkiem nazw przełączników. Na przykład

```
>Edit.Find ^^t /regex
```

 Daszek działa tak samo, niezależnie od tego, czy znajduje się wewnątrz, czy poza cudzysłowem. Jeśli karetka jest ostatnim znakiem w wierszu, zostanie zignorowana.

## <a name="see-also"></a>Zobacz też
 [Znajdowanie i zamienianie tekstu](../ide/finding-and-replacing-text.md) przez [okno poleceń](../ide/reference/command-window.md)
