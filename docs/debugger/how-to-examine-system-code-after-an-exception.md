---
title: Badaj kod systemu po wystąpieniu wyjątku | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fe2dcc283f84bbcd5cd0b5a04dd5d1c300d9e14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349656"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Porady: badanie kodu systemu po wystąpieniu wyjątku
Gdy wystąpi wyjątek, może być konieczne przeanalizowanie kodu wewnątrz wywołania systemowego w celu ustalenia przyczyny wyjątku. Poniższa procedura wyjaśnia, jak to zrobić, jeśli nie masz symboli ładowanych dla kodu systemowego lub jeśli Tylko mój kod jest włączona.

### <a name="to-examine-system-code-following-an-exception"></a>Aby przejrzeć kod systemowy po wyjątku

1. W oknie **stos wywołań** kliknij prawym przyciskiem myszy, a następnie kliknij polecenie **Pokaż kod zewnętrzny**.

     Jeśli Tylko mój kod nie jest włączona, ta opcja nie jest dostępna w menu skrótów, a kod systemowy jest domyślnie wyświetlany.

2. Kliknij prawym przyciskiem myszy ramki kodu zewnętrznego, które są teraz wyświetlane w oknie **stosu wywołań** .

3. Wskaż **Załaduj symbole z** , a następnie kliknij pozycję **serwery symboli firmy Microsoft**.

    1. Jeśli Tylko mój kod została włączona, zostanie wyświetlone okno dialogowe. Stany IT Tylko mój kod już wyłączone. Jest to niezbędne do przechodzenia do wywołań systemowych.

    2. Zostanie wyświetlone okno dialogowe **pobieranie symboli publicznych** . Zostanie ona usunięta po zakończeniu pobierania.

4. Teraz można przeanalizować kod systemowy w oknie **stosu wywołań** i innych oknach. Na przykład możesz dwukrotnie kliknąć ramkę stosu wywołań, aby wyświetlić kod w oknie źródłowym lub **rozasembleru** .

## <a name="see-also"></a>Zobacz też
- [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)