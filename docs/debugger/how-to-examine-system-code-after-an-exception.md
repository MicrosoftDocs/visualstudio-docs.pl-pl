---
title: Badanie kodu systemu po zakończeniu | Microsoft Docs
description: Dowiedz się, jak przeanalizować kod w wywołaniu systemowym, aby znaleźć przyczynę wyjątku. Procedura ma zastosowanie nawet wtedy, gdy symbole dla kodu systemowego nie zostały załadowane.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f05ae1486089eaa63ef47a9953578db2a0b6662a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384658"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Porady: badanie kodu systemu po wystąpieniu wyjątku
W przypadku wystąpienia wyjątku może być konieczne przeanalizowanie kodu wewnątrz wywołania systemowego w celu określenia przyczyny wyjątku. W poniższej procedurze wyjaśniono, jak to zrobić, jeśli nie załadowano symboli dla kodu systemowego lub jeśli Tylko mój kod włączona.

### <a name="to-examine-system-code-following-an-exception"></a>Aby zbadać kod systemowy po wyjątku

1. W **oknie Stos wywołań** kliknij prawym przyciskiem myszy, a następnie kliknij polecenie **Pokaż kod zewnętrzny**.

     Jeśli Tylko mój kod nie jest włączona, ta opcja nie jest dostępna w menu skrótów, a kod systemowy jest wyświetlany domyślnie.

2. Kliknij prawym przyciskiem myszy zewnętrzne ramki kodu, które są teraz wyświetlane w **oknie Stos** wywołań.

3. Wskaż polecenie **Załaduj symbole z,** a następnie **kliknij pozycję Serwery symboli firmy Microsoft.**

    1. Jeśli Tylko mój kod została włączona, zostanie wyświetlone okno dialogowe. Stwierdza, że Tylko mój kod została wyłączona. Jest to niezbędne do przechodzenia do wywołań systemowych.

    2. Zostanie **wyświetlone okno dialogowe Pobieranie symboli** publicznych. Zniknie ona po zakończeniu pobierania.

4. Teraz możesz przeanalizować kod systemowy w **oknie stosu wywołań** i innych oknach. Na przykład możesz kliknąć dwukrotnie ramkę stosu wywołań, aby wyświetlić kod w oknie źródła lub **dezembblowania.**

## <a name="see-also"></a>Zobacz też
- [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)