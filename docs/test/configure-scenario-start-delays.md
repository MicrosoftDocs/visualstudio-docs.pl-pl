---
title: Konfigurowanie opóźnień uruchamiania scenariusza do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f962306462538717df694d3bc47719fe31b1e1fe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76111480"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Konfigurowanie opóźnień uruchamiania scenariusza w testach obciążenia

Określ opóźnienie przed rozpoczęciem scenariusza w teście obciążenia przy użyciu edytora testów obciążenia i okna **Właściwości.**

Na przykład można użyć **opóźnienie czas rozpoczęcia** właściwości, jeśli potrzebujesz jednego scenariusza, aby rozpocząć produkcję elementów, które zużywa inny scenariusz. Można opóźnić scenariusz zużywania, aby włączyć scenariusz produkcji do wypełniania niektórych danych.

Innym przykładem jest, że może mieć jeden scenariusz, który jest uruchamiany tylko w określonej porze dnia. Tak, chcesz opóźnić początek scenariusza, aby symulować to.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Określanie czasu rozpoczęcia opóźnienia scenariusza

Można określić opóźnienie przed rozpoczęciem scenariusza w teście obciążenia za pomocą Edytora testów obciążenia, aby zmienić **właściwość Opóźnienie czasu rozpoczęcia** w oknie **Właściwości.**

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisy, zobacz [Właściwości scenariusza testu obciążenia.](../test/load-test-scenario-properties.md)

Przykład wystąpienia, gdy można użyć **delay start time** właściwość jest, gdy potrzebujesz jednego scenariusza, aby rozpocząć produkcję elementów, które zużywa inny scenariusz. Można opóźnić scenariusz zużywania, aby włączyć scenariusz produkcji do wypełniania niektórych danych.

Innym przykładem jest, że może mieć jeden scenariusz, który jest uruchamiany tylko o określonej porze dnia. W związku z tym chcesz opóźnić rozpoczęcie scenariusza, aby symulować to.

> [!NOTE]
> Aby uzyskać pełną listę właściwości ustawień uruchamiania i ich opisy, zobacz [Ładowanie właściwości scenariusza testu](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Aby określić czas rozpoczęcia opóźnienia dla scenariusza

1. Otwórz test obciążenia.

     Pojawi się Edytor testów obciążenia. Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **Scenariusze** drzew testów obciążenia wybierz węzeł scenariusza, dla którego chcesz określić czas rozpoczęcia opóźnienia.

3. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości.**

4. W polu tekstowym właściwości **Opóźnienie czasu rozpoczęcia** wpisz wartość czasu, która wskazuje czas oczekiwania po uruchomieniu testu obciążenia przed rozpoczęciem scenariusza po uruchomieniu testu obciążenia.

    > [!NOTE]
    > Jeśli wartość właściwości **Disable During Warmup** dla scenariusza jest ustawiona na **True,** po okresie rozgrzewania zostanie zastosowana wartość czasu właściwości **Opóźnienie w czasie.** Można kontrolować, które scenariusze są uwzględniane w rozgrzewce przy użyciu **Disable During Warmup** scenario właściwości.

5. Po zmianie właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia przy użyciu nowej wartości **Czas rozpoczęcia opóźnienia.**

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Włączanie i wyłączanie, czy scenariusz jest uruchamiany w okresie rozgrzewania

Właściwość **Disable During Warmup** jest ustawiana przy użyciu okna **Właściwości.** Edytowanie właściwości scenariusza testu obciążenia jest ustawiana przez Edytor testów obciążenia.

**Właściwość Disable During Warmup** służy do wskazania, czy scenariusz powinien być uruchamiany, czy nie w okresie rozgrzewania określonym we właściwości **Opóźnienie czasu rozpoczęcia.** Aby uzyskać więcej informacji, zapoznaj się z poprzednią [procedurą Określ czas rozpoczęcia opóźnienia scenariusza](#specify-the-delay-start-time-of-a-scenario).

> [!NOTE]
> Aby uzyskać pełną listę właściwości ustawień uruchamiania i ich opisy, zobacz [Ładowanie właściwości scenariusza testu](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Aby włączyć lub wyłączyć okres rozgrzewania dla scenariusza

1. Otwórz test obciążenia.

     Pojawi się **Edytor testów obciążenia.** Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **Scenariusze** drzew testów obciążenia wybierz węzeł scenariusza, dla którego chcesz zmienić zachowanie rozgrzewania.

3. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości.**

     We właściwości **Wyłącz podczas rozgrzewania** wybierz true **lub** **false.**

4. Po zakończeniu zmiany właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia przy użyciu nowej wartości **Wyłącz podczas rozgrzewania.**

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
- [Konfigurowanie agentów testowych i kontrolerów testów do testów obciążenia](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
