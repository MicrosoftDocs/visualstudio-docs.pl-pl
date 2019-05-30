---
title: Opinia dla użytkownika | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2255a972dd7a889713e77fa686b348500c03ea7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328978"
---
# <a name="feedback-to-the-user"></a>Opinia dla użytkownika
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE), wizualną opinię dotyczący możliwości opiera się na bieżące zaznaczenie i kontekst zaznaczenia globalnego użytkownika. W poniższej tabeli wymieniono funkcje, które są dostępne w kontekstach inną opcję.

|Kontekst zaznaczenia|Dostępne funkcje|
|-----------------------|-----------------------------|
|IDE|Global|
|Bieżący zestaw produktów|Specyficzne dla produktu|
|Aktywnej hierarchii|Określonego typu hierarchii|
|Element aktywnej hierarchii|Określonego typu elementu w hierarchii|
|Aktywnego dokumentu|Określonego typu dokumentu|
|Okno najwyższego poziomu interfejsu wielu dokumentów (MDI)|Określonego typu okno|
|Bieżący kontekst zaznaczenia|Określone kontekst zaznaczenia|

 Jeśli tylko urządzenia surface funkcjonalność, użytkownicy muszą i zapewnić spójne wybór i opinie kontekst środowiska można zmniejszyć złożoność w środowisku IDE. Przy każdym otwarciu okna w IDE, stosowane są następujące reguły:

- Jeśli okno zmienia kontekst zaznaczenia, informacje zwrotne dotyczące wyboru jest wyraźnie wskazane w oknie i **dynamiczna Pomoc** okna, jeśli wyświetlony, jest zaktualizowana w celu odzwierciedlenia bieżącego kontekstu.

- Jeśli okno zmienia kontekst zaznaczenia globalnego, wszystkich menu kontekstowych, okna aktywnej hierarchii i na pasku tytułu aplikacji są aktualizowane, tak aby odzwierciedlić bieżący kontekst.

- Okno powinno powierzchni właściwości dla bieżącego zaznaczenia w **właściwości** okna i, opcjonalnie, jeśli wyświetlony, **strony właściwości** okno dialogowe.

- Jeśli okno nie powierzchni właściwości lub zmienić kontekst zaznaczenia globalnego, informacje zwrotne dotyczące wyboru nie powinna pozostać w oknie, gdy nie jest już aktywnego okna w IDE.

- Wszystkie okna narzędzi specyficznych dla dokumentu stale powinny odzwierciedlać aktywnego dokumentu.

- Menu, paski narzędzi i paska tytułu aplikacji powinny odzwierciedlać okna klienta znajdujące się najwyżej interfejsu wielu dokumentów (MDI).

  Na przykład, gdy kod HTML widoku **formularz sieci Web** wewnątrz aplikacji sieci Web w języku Visual Basic jest otwarty projekt, a użytkownik wybierze `<td>` tagu, informacje są przekazywane w następujący sposób:

- Wybór jest wskazane w aktywnym oknie i zostaną uwzględnione w **właściwości** okna.

- Specyficzne dla dokumentu **przybornika** zostanie zaktualizowany w celu odzwierciedlenia aktywnego dokumentu.

- **Edytora** narzędzi i **tabeli** są wyświetlane w menu i na pasku tytułu aktualizowany w celu odzwierciedlenia okna formularza sieci Web.

- Okno aktywnej hierarchii, które jest zazwyczaj **Eksploratora rozwiązań**i jej aktualizacji paska tytułu, aby odzwierciedlić bieżący kontekst i kontekstowej **projektu** poleceń menu teraz je zastosować do aktywnego internetowego Projekt aplikacji.

## <a name="see-also"></a>Zobacz także
- [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md)
- [Hierarchie i zaznaczenia](../../extensibility/internals/hierarchies-and-selection.md)