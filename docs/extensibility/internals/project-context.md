---
title: Kontekst projektu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706587"
---
# <a name="project-context"></a>Kontekst projektu
Gdy użytkownik dodaje lub współpracuje z projektami i elementami projektu, IDE używa pojęcia kontekstu projektu, aby określić, jak różne operacje powinny być wykonywane.

 Zazwyczaj pliki są standardowymi obiektami projektu, które użytkownik jawnie tworzy, wybierając polecenie **Nowy projekt** lub udostępnia je, wybierając polecenie **Otwórz projekt** w menu **Plik.** W takich przypadkach pliki są tworzone i otwierane w kontekście projektu, a typ projektu definiuje kontekst edycji dokumentu.

 Niektóre projekty zapewniają bardzo bogaty kontekst. Na przykład projekt zarządza zakresem projektu, programowa przestrzeni nazw lub połączenia bazy danych o zakresie projektu dla powiązania danych. Użytkownik może często otwierać pliki lub połączenia bazy danych bezpośrednio przy użyciu określonego obiektu projektu, takiego jak element projektu wyświetlany w Eksploratorze rozwiązań.

 W innych przypadkach kontekst projektu elementu nie jest jawnie określony. Na przykład kontekst elementu nie jest dostępny, gdy użytkownik otworzy plik, wybierając polecenie **Otwórz istniejący plik** w menu **Plik,** gdy debuger działa w pliku lub gdy użytkownik kliknie polecenie **Znajdź w plikach** w oknie dialogowym **Znajdź i zamień.** Aby obsłużyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> te sytuacje, IDE wywołuje do zarządzania procesem znajdowania najlepszego projektu, aby otworzyć dokument.

## <a name="see-also"></a>Zobacz też
- [Priorytet projektu](../../extensibility/internals/project-priority.md)
- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
