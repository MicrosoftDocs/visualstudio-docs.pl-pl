---
title: Czasy reakcji na testowanie obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 661a31411a561f15809a10fb15fd71a29e6a64fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672952"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Edytowanie czasów reakcji w celu symulowania opóźnień interakcji z witryną sieci Web w scenariuszach testów obciążenia

Czasy reakcji służą do symulowania zachowań ludzi, które powodują, że osoby czekają na interakcję z witryną sieci Web. Czasy reakcji występują między żądaniami w teście wydajności sieci Web i między iteracjami testu w scenariuszu testu obciążenia. Użycie czasów reakcji w teście obciążenia może być przydatne podczas tworzenia bardziej precyzyjnych symulacji obciążenia. Można zmienić, czy czasy reakcji są używane, czy ignorowane w testach obciążenia. Należy zmienić, czy czasy reakcji są używane w testach obciążenia w **Edytor testu obciążeniowego**.

*Profil myśli* jest ustawieniem, które ma zastosowanie do scenariusza w teście obciążenia. To ustawienie określa, czy czasy reakcji zapisywane w poszczególnych testach wydajności sieci Web są używane podczas testu obciążenia. Jeśli chcesz użyć czasów reakcji w niektórych testach wydajności sieci Web, ale nie w innych, należy umieścić je w różnych scenariuszach. Aby uzyskać więcej informacji na temat scenariuszy, zobacz [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md).

Początkowo należy określić, czy w testach obciążenia należy używać czasów reakcji podczas tworzenia testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego**. Aby uzyskać więcej informacji, zobacz [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md).

Opcje **profilu myśli** są opisane na poniższej liście:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Logowanie**

Czasy reakcji są ignorowane. Użyj tego ustawienia, jeśli chcesz wygenerować maksymalne obciążenie na potrzeby intensywnej obciążeniu serwera sieci Web. Nie należy używać go podczas próby utworzenia bardziej realistycznych interakcji użytkownika z serwerem sieci Web.

**Z**

Czasy reakcji są używane dokładnie tak, jak zostały zarejestrowane w teście wydajności sieci Web. Symuluje wielu użytkowników, którzy uruchamiają testy wydajności sieci Web dokładnie tak samo jak zarejestrowane. Ponieważ test obciążenia symuluje wielu użytkowników, przy użyciu tego samego czasu reakcji może stworzyć nienaturalny wzorzec obciążenia synchronizowanych użytkowników wirtualnych.

**Rozkład normalny**

Czasy reakcji są używane, ale różnią się w stosunku do normalnej krzywej. Zapewnia bardziej realistyczną symulację wirtualnych użytkowników, nieco zmieniając czas reakcji między żądaniami.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisów, zobacz [właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Zmiana profilu myśli

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Aby zmienić profil myśli w scenariuszu testu obciążenia

1. Z projektu test wydajności i obciążenia sieci Web Otwórz test obciążenia.

2. W **Edytor testu obciążeniowego**wybierz węzeł scenariusza, w którym chcesz zmienić **profil myśli**. **Profil myśli** jest wyświetlany w oknie **Właściwości** . Naciśnij klawisz **F4** , aby wyświetlić okno **Właściwości** .

3. Zmień właściwość **profil myśli** w oknie **Właściwości** .

4. Po zakończeniu zmiany właściwości wybierz pozycję **Zapisz** w menu **plik** . Następnie możesz uruchomić test obciążenia z nowym profilem myśli.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)