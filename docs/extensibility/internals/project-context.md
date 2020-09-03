---
title: Kontekst projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e411f0bca361f96cdffcfd89498908fd21d441
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706587"
---
# <a name="project-context"></a>Kontekst projektu
Gdy użytkownik dodaje lub współpracuje z projektami i elementami projektu, IDE używa koncepcji kontekstu projektu, aby określić, jak należy wykonać różne operacje.

 Zazwyczaj pliki są obiektami standardowych projektów, które użytkownik jawnie tworzy, wybierając polecenie **Nowy projekt** lub Udostępnij, wybierając polecenie **Otwórz projekt** w menu **plik** . W takich przypadkach pliki są tworzone i otwierane w kontekście projektu, a typ projektu definiuje kontekst do edycji dokumentu.

 Niektóre projekty oferują bardzo rozbudowany kontekst. Na przykład projekt zarządza obszarem programu programistycznego, przestrzenią nazw programu lub połączeniem z bazą danych projektu dla powiązania danych. Użytkownik może często otwierać pliki lub połączenia bazy danych bezpośrednio przy użyciu określonego obiektu projektu, takiego jak element projektu wyświetlany w Eksplorator rozwiązań.

 W innych przypadkach kontekst projektu elementu nie jest jawnie określony. Na przykład kontekst elementu nie jest dostępny, gdy użytkownik otwiera plik, wybierając polecenie **Otwórz istniejący plik** w menu **plik** , gdy debuger działa na pliku lub gdy użytkownik kliknie polecenie **Znajdź w plikach** w oknie dialogowym **Znajdowanie i zamienianie** . Aby obsłużyć te sytuacje, środowisko IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> do zarządzania procesem wyszukiwania najlepszego projektu w celu otwarcia dokumentu.

## <a name="see-also"></a>Zobacz też
- [Priorytet projektu](../../extensibility/internals/project-priority.md)
- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
