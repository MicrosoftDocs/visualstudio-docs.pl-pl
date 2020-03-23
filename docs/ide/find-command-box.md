---
title: Pole wyszukiwania polecenia
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b50c0503d313d4482d8370071220dbf1403d9a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591531"
---
# <a name="findcommand-box"></a>Find/Command — Pole

Można wyszukiwać tekst i uruchamiać polecenia programu Visual Studio w polu **Znajdź/Polecenie.** Pole **Znajdź/Polecenie** jest nadal dostępne jako kontrolka paska narzędzi, ale nie jest już domyślnie widoczne. Okno **Znajdź/Polecenie** można wyświetlić, wybierając pozycję **Dodaj lub usuń przyciski** na pasku narzędzi **Standardowy,** a następnie wybierając polecenie **Znajdź**.

Aby uruchomić [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] polecenie, należy go poprzedzać**>** znakiem większym niż ( ).

Pole **Znajdź/Polecenia** zachowuje ostatnie 20 wprowadzonych elementów i wyświetla je na liście rozwijanej. Możesz poruszać się po liście, wybierając **klawisze strzałek**.

![Znajdź&#47;pole polecenia](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Wyszukiwanie tekstu

Domyślnie po określeniu tekstu w polu **Znajdź/Polecenie,** a następnie wybraniu **klawisza Enter** program Visual Studio przeszukuje bieżący dokument lub okno narzędzia przy użyciu opcji określonych w oknie dialogowym **Znajdowanie w plikach.** Aby uzyskać więcej informacji, zobacz [Znajdowanie i zamienianie tekstu](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Wprowadzanie poleceń

Aby użyć pola **Znajdź/Polecenia** do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wydania pojedynczego polecenia lub aliasu zamiast wyszukiwania tekstu, przedmuchuj polecenie symbolem większym niż (**>**). Przykład:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Alternatywnie można również użyć okna **Polecenia,** aby wprowadzić i wykonać pojedyncze lub wielokrotne polecenia. Niektóre polecenia lub aliasy mogą być wprowadzane i wykonywane samodzielnie; inne mają wymagane argumenty w ich składni. Aby uzyskać listę poleceń, które mają argumenty, zobacz [Polecenia programu Visual Studio](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Znaki ucieczki

Znak przesiadki (**^**) w poleceniu oznacza, że znak bezpośrednio po nim jest interpretowany dosłownie, a nie jako znak kontrolny. Może to być używane do osadzania prostych cudzysłowów (**"**), spacji, ukośników wiodących, leżanek lub innych znaków literału w parametrze lub wartości przełącznika, z wyjątkiem nazw przełączników. Przykład:

```
>Edit.Find ^^t /regex
```

Czyn y pielęgnacyjny działa tak samo, niezależnie od tego, czy znajduje się wewnątrz, czy poza cudzysłowami. Jeśli ciesza jest ostatnim znakiem w wierszu, jest ignorowana.

## <a name="see-also"></a>Zobacz też

- [Okno polecenia](../ide/reference/command-window.md)
- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
