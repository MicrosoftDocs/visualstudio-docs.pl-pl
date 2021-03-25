---
title: Opinie do użytkownika | Microsoft Docs
description: Dowiedz się, jak zapewnić użytkownikom wizualną opinię o dostępnych funkcjach w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d40ca34ea8d579e85ee56170f621b98a10b89f2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069637"
---
# <a name="feedback-to-the-user"></a>Opinie do użytkownika
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku programistycznym (IDE), opinie wizualne dotyczące dostępnych funkcji opierają się na bieżącym wyborze użytkownika i globalnym kontekście wyboru. W poniższej tabeli wymieniono funkcje dostępne w różnych kontekstach wyboru.

|Kontekst zaznaczenia|Dostępna funkcja|
|-----------------------|-----------------------------|
|IDE|Globalnie|
|Bieżący zestaw produktów|Specyficzne dla produktu|
|Aktywna hierarchia|Specyficzne dla typu hierarchii|
|Element aktywnej hierarchii|Specyficzne dla typu elementu hierarchii|
|Aktywny dokument|Specyficzne dla typu dokumentu|
|Okno interfejsu wielu dokumentów (MDI)|Specyficzne dla typu okna|
|Bieżący kontekst zaznaczenia|Specyficzne dla kontekstu wyboru|

 Jeśli tylko chcesz, aby użytkownicy mieli potrzebną funkcjonalność i stale dostarczali spójny wybór i informacje dotyczące kontekstu środowiska, zmniejsz złożoność w IDE. Następujące reguły mają zastosowanie przy każdym otwarciu okna w środowisku IDE:

- Jeśli okno zmieni kontekst zaznaczenia, opinia o wyborze jest jasno wskazana w oknie, a **dynamiczne okno pomocy** , jeśli jest wyświetlany, zostanie zaktualizowane w celu odzwierciedlenia bieżącego kontekstu.

- Jeśli okno zmieni kontekst zaznaczenia globalnego, wszystkie menu specyficzne dla kontekstu, okno aktywnej hierarchii i pasek tytułu aplikacji są aktualizowane w celu odzwierciedlenia bieżącego kontekstu.

- Okno powinno mieć właściwości powierzchni dla bieżącego zaznaczenia w oknie **Właściwości** i opcjonalnie, jeśli jest wyświetlany, okno dialogowe **strony właściwości** .

- Jeśli okna nie są właściwościami powierzchni ani nie zmieniają globalnego kontekstu wyboru, opinia o wyborze nie powinna pozostać w oknie, gdy nie jest już aktywnym oknem w IDE.

- Wszystkie okna narzędzi specyficzne dla dokumentu powinny stale odzwierciedlać aktywny dokument.

- Menu, paski narzędzi i pasek tytułu aplikacji powinny odzwierciedlać okno klienta interfejsu wielu dokumentów (MDI).

  Na przykład gdy zostanie otwarty widok HTML **formularza sieci Web** w ramach projektu aplikacji sieci Web Visual Basic, a użytkownik wybierze `<td>` znacznik, opinia będzie dostarczana w następujący sposób:

- Zaznaczenie jest zaznaczone w aktywnym oknie i odzwierciedlone w oknie **Właściwości** .

- **Przybornik** specyficzny dla dokumentu zostanie zaktualizowany w celu odzwierciedlenia aktywnego dokumentu.

- Zostanie wyświetlony pasek narzędzi **edytora** i menu **tabela** , a pasek tytułu zostanie zaktualizowany w celu odzwierciedlenia okna formularza sieci Web.

- Aktywne okno hierarchii, które jest zwykle **Eksplorator rozwiązań**, a jego pasek tytułu jest aktualizowany w celu odzwierciedlenia bieżącego kontekstu i poleceń menu **projektu** kontekstowego, teraz stosuje się do projektu aktywnej aplikacji sieci Web.

## <a name="see-also"></a>Zobacz też
- [Wybór i waluta w IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Obiekty kontekstu wyboru](../../extensibility/internals/selection-context-objects.md)
- [Hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md)
