---
title: Kontekst projektu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 175ee37628b1794377a6b4e9e94cef52466cd291
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328356"
---
# <a name="project-context"></a>Kontekst projektu
Gdy użytkownik dodaje lub współpracuje z projektów i elementów projektu, IDE używa pojęcie kontekstem projektu, aby określić, jak różne operacje, które powinny być wykonywane.

 Zazwyczaj pliki są standardowy projekt obiektów tworzonych użytkownik jawnie, wybierając **nowy projekt** polecenia lub udostępnia, wybierając **Otwórz projekt** polecenie  **Plik** menu. W takich przypadkach pliki są tworzone i otwierane w ramach projektu, a typ projektu Określa kontekst dla edytowania dokumentu.

 Niektóre projekty zawierają bardzo szeroki kontekst. Na przykład projekt zarządza o zasięgu projektu, programowe przestrzeni nazw lub zakresie projektu połączenia bazy danych dla powiązania danych. Użytkownik może często otwierać pliki lub połączenia z bazą danych bezpośrednio przy użyciu obiektu określonego projektu, takich jak element projektu wyświetlane w Eksploratorze rozwiązań.

 W pozostałym czasie kontekstem projektu elementu nie jest jawnie określona. Na przykład kontekst elementu nie jest dostępne po użytkownik otwiera plik, wybierając **Otwórz istniejący plik** polecenie **pliku** menu, gdy debuger działa z pliku lub po kliknięciu przez użytkownika **Znajdź w plikach** polecenia w pliku **Znajdź i Zamień** okno dialogowe. Do obsługi tych sytuacji wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> do zarządzania procesem odnajdywania najlepsze projekt, aby otworzyć dokument.

## <a name="see-also"></a>Zobacz też
- [Priorytet projektu](../../extensibility/internals/project-priority.md)
- [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)