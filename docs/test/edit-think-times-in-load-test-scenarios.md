---
title: Czasy przemyślenia na potrzeby testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 887d2af9e60be914bd74141041ecc375cfea4f00
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590036"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Edytuj czasy zajmów się, aby symulować opóźnienia interakcji z człowiekiem w scenariuszach testów obciążenia

Czasy myśleń są używane do symulowania ludzkich zachowań, które powodują, że ludzie czekają między interakcjami z witryną sieci Web. Czasy myślenia występują między żądaniami w teście wydajności sieci web i między iteracjami testów w scenariuszu testu obciążenia. Korzystanie z czasów myślenia w teście obciążenia może być przydatne w tworzeniu dokładniejszych symulacji obciążenia. Można zmienić, czy czasy myślenia są używane lub ignorowane w testach obciążenia. Można zmienić, czy czasy myślenia są używane w testach obciążenia w **Edytorze testów obciążenia**.

*Profil think* jest ustawieniem, które ma zastosowanie do scenariusza w teście obciążenia. Ustawienie określa, czy czasy zajdą, które są zapisywane w poszczególnych testów wydajności sieci web są używane podczas testu obciążenia. Jeśli chcesz użyć czasu myślenia w niektórych testach wydajności sieci web, ale nie w innych, należy umieścić je w różnych scenariuszach. Aby uzyskać więcej informacji o scenariuszach, zobacz [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md).

Początkowo można określić, czy podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążenia**używane są czasy myślów. Aby uzyskać więcej informacji, zobacz [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md).

Opcje **Profilu myśli** są opisane na następującej liście:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Wyłączone**

Czasy myślenia są ignorowane. To ustawienie należy używać, jeśli chcesz wygenerować maksymalne obciążenie, aby mocno podkreślić serwer www. Nie należy go używać, gdy próbujesz utworzyć bardziej realistyczne interakcje użytkownika z serwerem sieci web.

**Włączone**

Czasy myślów są używane dokładnie tak, jak zostały zarejestrowane w teście wydajności sieci. Symuluje wielu użytkowników z uruchomionymi testami wydajności sieci Web dokładnie tak, jak zostało to zarejestrowane. Ponieważ test obciążenia symuluje wielu użytkowników, przy użyciu tego samego czasu myślenia może utworzyć nienaturalny wzorzec obciążenia zsynchronizowanych użytkowników wirtualnych.

**Rozkład normalny**

Czasy myślenia są używane, ale zróżnicowane na normalnej krzywej. Zapewnia bardziej realistyczną symulację wirtualnych użytkowników, nieznacznie zmieniając czas na myślenie między żądaniami.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisy, zobacz [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Zmienianie profilu myślenia

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Aby zmienić profil myślenia w scenariuszu testu obciążenia

1. Z projektu testu wydajności sieci web i obciążenia otwórz test obciążenia.

2. W **Edytorze testów obciążenia**wybierz węzeł scenariusz, w którym chcesz zmienić **profil think**. Profil **think** jest wyświetlany w oknie **Właściwości.** Naciśnij **klawisz F4,** aby wyświetlić okno **Właściwości.**

3. Zmień właściwość **Think Profile** w oknie **Właściwości.**

4. Po zakończeniu zmiany właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia z nowym profilem myślenia.

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
