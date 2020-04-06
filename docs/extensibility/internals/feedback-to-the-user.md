---
title: Opinie dla użytkownika | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46b9190b16b9aa444384847bf209ccca50c7f768
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708413"
---
# <a name="feedback-to-the-user"></a>Opinie dla użytkownika
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku programistycznym (IDE) wizualne informacje zwrotne dotyczące dostępnych funkcji są oparte na bieżącym wyborze użytkownika i kontekście wyboru globalnego. W poniższej tabeli wymieniono funkcje, które są dostępne w różnych kontekstach wyboru.

|Kontekst selekcji|Dostępne funkcje|
|-----------------------|-----------------------------|
|IDE|Globalny|
|Aktualny zestaw produktów|Specyficzne dla produktu|
|Aktywna hierarchia|Specyficzne dla typu hierarchii|
|Aktywny element hierarchii|Określony typ elementu hierarchii|
|Aktywny dokument|Specyficzny typ dokumentu|
|Okno Interfejs wielokadowy (MDI) topmost|Specyficzny dla typu okna|
|Bieżący kontekst wyboru|Kontekst selekcji specyficzny dla kontekstu|

 Jeśli tylko powierzchni funkcje użytkownicy potrzebują i stale zapewniają spójne zaznaczenie i środowisko kontekstu opinii, można zmniejszyć złożoność ide. Następujące reguły mają zastosowanie za każdym razem, gdy okno jest otwierane w IDE:

- Jeśli okno zmieni kontekst wyboru, w oknie wyraźnie wskazywane są informacje zwrotne o wyborze, a okno **Pomoc dynamiczna,** jeśli jest wyświetlane, zostanie zaktualizowane w celu odzwierciedlenia bieżącego kontekstu.

- Jeśli okno zmieni kontekst zaznaczenia globalnego, wszystkie menu specyficzne dla kontekstu, aktywne okno hierarchii i pasek tytułu aplikacji zostaną zaktualizowane w celu odzwierciedlenia bieżącego kontekstu.

- Okno powinno powierzchniować właściwości bieżącego zaznaczenia w oknie **Właściwości** i opcjonalnie, jeśli jest wyświetlane, okno dialogowe **Strony właściwości.**

- Jeśli okno nie ma właściwości powierzchni lub zmienić kontekst zaznaczenia globalnego, sprzężenie zwrotne wyboru nie powinny pozostać w oknie, gdy nie jest już aktywne okno w IDE.

- Wszystkie okna narzędzi specyficznych dla dokumentu powinny stale odzwierciedlać aktywny dokument.

- Menu, paski narzędzi i pasek tytułu aplikacji powinny odzwierciedlać najwyższe okno klienta interfejsu wielu dokumentów (MDI).

  Na przykład po otwarciu widoku HTML **formularza sieci Web** wewnątrz projektu aplikacji sieci `<td>` Web języka Visual Basic i wybraniu znacznika użytkownik jest dostarczany w następujący sposób:

- Zaznaczenie jest wskazane w aktywnym oknie i odzwierciedlone w oknie **Właściwości.**

- **Zestaw narzędzi** specyficzny dla dokumentu zostanie zaktualizowany w celu odzwierciedlenia aktywnego dokumentu.

- Wyświetlany jest pasek narzędzi **Edytor** i menu **Tabela,** a pasek tytułu zostanie zaktualizowany w celu odzwierciedlenia okna formularza sieci Web.

- Aktywne okno hierarchii, które jest zazwyczaj **Eksplorator rozwiązań,** i jego aktualizacja paska tytułu, aby odzwierciedlić bieżący kontekst i kontekstowe polecenia menu **projektu** mają teraz zastosowanie do aktywnego projektu aplikacji sieci Web.

## <a name="see-also"></a>Zobacz też
- [Wybór i waluta w IDEI](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Obiekty kontekstu zaznaczenia](../../extensibility/internals/selection-context-objects.md)
- [Hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md)
