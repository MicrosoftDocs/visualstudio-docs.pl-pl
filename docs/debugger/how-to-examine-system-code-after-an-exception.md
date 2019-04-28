---
title: Badanie kodu systemu po wystąpieniu wyjątku | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b9467ce7001f0061c20a5097220bd93b24937db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894037"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Instrukcje: Badanie kodu systemu po wystąpieniu wyjątku
Gdy wystąpi wyjątek, Niewykluczone, że sprawdzić kod wewnątrz wywołania systemu, aby ustalić przyczynę wyjątku. Poniższa procedura wyjaśnia, jak to zrobić, jeśli nie masz symbole załadowane dla kodu systemowego lub jeśli włączono opcję tylko mój kod.

### <a name="to-examine-system-code-following-an-exception"></a>Aby sprawdzić kod systemu w następstwie wyjątku

1. W **stos wywołań** okna, kliknij prawym przyciskiem myszy, następnie kliknij przycisk **Pokaż kod zewnętrzny**.

     Jeśli nie włączono opcję tylko mój kod, ta opcja nie jest dostępne w menu skrótów, a kod systemowy jest wyświetlany domyślnie.

2. Kliknij prawym przyciskiem myszy ramki kodu zewnętrznego, które pojawiają się w **stos wywołań** okna.

3. Wskaż **Załaduj symbole z** a następnie kliknij przycisk **serwery symboli firmy Microsoft**.

    1. Jeśli włączono opcję tylko mój kod, pojawi się okno dialogowe. Stwierdza, że tylko mój kod teraz został wyłączony. Jest to konieczne do przechodzenia do wywołań systemowych.

    2. **Pobieranie symboli publicznych** pojawi się okno dialogowe. Znikną po zakończeniu pobierania.

4. Można teraz sprawdzić kod systemu w **stos wywołań** okna i innych oknach. Na przykład, możesz kliknąć dwukrotnie ramki stosu wywołań, aby wyświetlić kod w źródle lub **dezasemblacji** okna.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)