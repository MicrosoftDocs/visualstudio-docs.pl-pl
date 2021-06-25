---
title: Kontekst | Microsoft Docs
description: Dowiedz się, Visual Studio IDE używa kontekstu projektu, aby określić sposób wykonywania operacji, gdy użytkownik dodaje projekty i elementy projektu lub pracuje z nim.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73e3c8a94607e7e0b31bacddac8e7f19b6139328
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899826"
---
# <a name="project-context"></a>Kontekst projektu
Gdy użytkownik dodaje projekty i elementy projektu lub pracuje z nim, w idee używane jest określenie kontekstu projektu w celu określenia sposobu wykonania różnych operacji.

 Zazwyczaj pliki są standardowymi obiektami projektu, które użytkownik jawnie tworzy, wybierając polecenie **Nowy** projekt lub udostępniając je, wybierając polecenie **Otwórz** projekt w menu **Plik.** W takich przypadkach pliki są tworzone i otwierane w kontekście projektu, a typ projektu definiuje kontekst edycji dokumentu.

 Niektóre projekty zapewniają bardzo rozbudowane konteksty. Na przykład projekt zarządza połączeniem bazy danych o zakresie projektu, programową przestrzenią nazw lub bazą danych w zakresie projektu w celu powiązania danych. Użytkownik może często otwierać pliki lub połączenia z bazą danych bezpośrednio przy użyciu określonego obiektu projektu, takiego jak element projektu wyświetlany w Eksplorator rozwiązań.

 W innych momentach kontekst projektu elementu nie jest jawnie określony. Na przykład **kontekst** elementu nie jest dostępny, gdy użytkownik otwiera  plik, wybierając polecenie Otwórz istniejący plik w menu Plik, gdy debuger  działa na pliku, lub gdy użytkownik kliknie polecenie Znajdź w plikach w oknie dialogowym Znajdź i zamień.  Aby obsłużyć takie sytuacje, środowiska IDE wywołuje w celu zarządzania procesem znajdowania najlepszego <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> projektu w celu otwarcia dokumentu.

## <a name="see-also"></a>Zobacz też
- [Priorytet projektu](../../extensibility/internals/project-priority.md)
- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
