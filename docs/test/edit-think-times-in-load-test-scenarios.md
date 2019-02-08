---
title: Czasy reakcji do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bb5227c4b5f771747a43a7f0f12e0125b125604e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55943379"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Edytowanie czasów reakcji w celu symulowania opóźnienia interakcja z witryny sieci Web w scenariuszach testów obciążenia

Czasy reakcji służą do symulowania zachowań ludzkich, który powoduje, że osoby do interakcji z witryny sieci Web. Czasy reakcji występują między żądaniami w teście wydajności sieci web i między poszczególnymi iteracjami testu w scenariuszu testu obciążenia. Użycie czasów reakcji w teście obciążeniowym może być przydatne przy tworzeniu bardziej dokładnych symulacji obciążenia. Można zmienić, czy testy reakcji, czasy są używane, lub zignorować obciążenia. Możesz określić, czy reakcji, czasy są używane w obciążenia testy w **edytorze testu obciążeniowego**.

*Profil reakcji* to ustawienie ma zastosowanie do scenariusza w teście obciążeniowym. Ustawienie określa, czy reakcji, czasy, które są zapisywane w testach wydajności sieci web w poszczególnych są używane podczas testu obciążeniowego. Jeśli chcesz używać traktować razy w niektórych testów wydajności sieci web, ale nie w innych, należy umieścić je w różnych scenariuszach. Aby uzyskać więcej informacji na temat scenariuszy, zobacz [scenariusze testów obciążenia edycji](../test/edit-load-test-scenarios.md).

Początkowo ustawić czy używać czasów reakcji w testach obciążenia, podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**. Aby uzyskać więcej informacji, zobacz [scenariusze testów obciążenia edycji](../test/edit-load-test-scenarios.md).

**Profil reakcji** opcje są opisane na poniższej liście:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Off**

Czasy reakcji są ignorowane. Użyj tego ustawienia, jeśli chcesz wygenerować maksymalnego obciążenia intensywnie podkreślanie serwera sieci web. Nie jest używana podczas próby tworzenia bardziej realistycznego interakcji użytkownika z serwerem sieci web.

**On**

Czasy reakcji służą dokładnie tak, jak są one rejestrowane w teście wydajności sieci web. Symuluje wielu użytkownikom uruchamianie testów wydajności sieci web, dokładnie tak, jak zarejestrowany. Ponieważ zasymulowano obciążenie wielu użytkowników, korzystając z tych samych zdaniem czasu można utworzyć wzorzec obciążenia nienaturalnym synchronizowanych użytkowników wirtualnych.

**Rozkład normalny**

Czasy reakcji są używane, ale zróżnicowane na typową krzywą. Zapewnia bardziej realistyczna symulacja użytkowników wirtualnych przez zróżnicowanie nieco czas namysłu między żądaniami.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Zmień profil reakcji

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Aby zmienić profil reakcji w scenariuszu testu obciążenia

1.  Od wydajności sieci web i obciążenia projektu testowego, otwórz test obciążenia.

2.  W **edytora testu obciążenia**, wybierz węzeł scenariusz, w której chcesz zmienić **profil reakcji**. **Profil reakcji** jest wyświetlany w **właściwości** okna. Naciśnij klawisz **F4** do wyświetlenia **właściwości** okna.

3.  Zmiana **profil reakcji** właściwość **właściwości** okna.

4.  Po zmianie właściwości, wybierz **Zapisz** na **pliku** menu. Następnie można uruchomić test obciążenia przy użyciu nowego profilu reakcji.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)