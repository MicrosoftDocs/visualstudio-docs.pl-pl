---
title: Pole wyszukiwania polecenia
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 221c5fbbd3f0f82ac97d0c2a0fcc82657e0296c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977799"
---
# <a name="findcommand-box"></a>Find/Command — Pole

Można wyszukać tekst i uruchomić polecenia programu Visual Studio z **Find/Command** pole. **Find/Command** pole jest nadal dostępne jako formant paska narzędzi, ale nie jest już domyślnie widoczne. Możesz wyświetlić **Find/Command** pola, wybierając **apletu Dodaj lub usuń przyciski** na **standardowa** narzędzi, a następnie wybierając **znaleźć**.

Aby uruchomić [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] polecenia, należy poprzedzić go o rozmiarze większym niż (**>**) logowania.

**Find/Command** pole zachowa ostatnie 20 elementów, które wprowadzono i wyświetla je na liście rozwijanej. Możesz przejść przez listę, wybierając **klawiszy strzałek**.

![Znajdź&#47;okno polecenia](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Wyszukiwanie tekstu

Domyślnie, gdy Określ tekst w **Find/Command** pole, a następnie wybierz **Enter** klucza, Visual Studio wyszukuje bieżące okno narzędzia lub dokumentu, korzystając z opcji, które są określone w **Znajdź w plikach** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Wprowadzenie poleceń

Do użycia **Find/Command** pole, aby wystawić pojedynczej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] polecenie lub alias zamiast wyszukiwania tekstu, należy poprzedzić polecenie o rozmiarze większym niż (**>**) symbol. Na przykład:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Alternatywnie, można również użyć **polecenia** okna do wprowadzania i wykonaj jedną lub kilka poleceń. Wprowadzony i wykonywane przez siebie; niektórych poleceń ani aliasów masz inne wymagane argumenty w składni. Aby uzyskać listę poleceń, które ma argumentów, zobacz [poleceń programu Visual Studio](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Znaki specjalne

Daszek (**^**) znaków za pomocą polecenia oznacza, że znak natychmiast po jego jest interpretowany dosłownie, a nie jako znak kontrolny. To może służyć do osadzania prostych znaków cudzysłowu (**"**), ukośników wiodących spacje, wartość daszków lub innych znaków literałowych w parametru lub przełącznika, z wyjątkiem nazw przełączników. Na przykład:

```
>Edit.Find ^^t /regex
```

Daszek działa tak samo, czy wewnątrz lub poza znaki cudzysłowu. Jeśli znak daszka jest ostatnim znakiem w wierszu, jest on ignorowany.

## <a name="see-also"></a>Zobacz także

- [Okno polecenia](../ide/reference/command-window.md)
- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)