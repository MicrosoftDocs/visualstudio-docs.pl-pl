---
title: Kontekst projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8afa595a264f218fcc20f18de1c261a9ead6e030
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725768"
---
# <a name="project-context"></a>Kontekst projektu
Gdy użytkownik dodaje lub współpracuje z projektami i elementami projektu, IDE używa koncepcji kontekstu projektu, aby określić, jak należy wykonać różne operacje.

 Zazwyczaj pliki są obiektami standardowych projektów, które użytkownik jawnie tworzy, wybierając polecenie **Nowy projekt** lub Udostępnij, wybierając polecenie **Otwórz projekt** w menu **plik** . W takich przypadkach pliki są tworzone i otwierane w kontekście projektu, a typ projektu definiuje kontekst do edycji dokumentu.

 Niektóre projekty oferują bardzo rozbudowany kontekst. Na przykład projekt zarządza obszarem programu programistycznego, przestrzenią nazw programu lub połączeniem z bazą danych projektu dla powiązania danych. Użytkownik może często otwierać pliki lub połączenia bazy danych bezpośrednio przy użyciu określonego obiektu projektu, takiego jak element projektu wyświetlany w Eksplorator rozwiązań.

 W innych przypadkach kontekst projektu elementu nie jest jawnie określony. Na przykład kontekst elementu nie jest dostępny, gdy użytkownik otwiera plik, wybierając polecenie **Otwórz istniejący plik** w menu **plik** , gdy debuger działa na pliku lub gdy użytkownik kliknie polecenie **Znajdź w plikach** w  **Znajdowanie i zamienianie** okna dialogowego. Aby obsłużyć te sytuacje, program IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>, aby zarządzać procesem wyszukiwania najlepszego projektu w celu otwarcia dokumentu.

## <a name="see-also"></a>Zobacz także
- [Priorytet projektu](../../extensibility/internals/project-priority.md)
- [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)