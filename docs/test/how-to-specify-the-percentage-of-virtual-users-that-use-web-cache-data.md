---
title: 'Test obciążenia: Ustawianie wartości procentowej wirtualnego użytkownika przy użyciu danych w pamięci podręcznej sieci Web'
description: Dowiedz się, jak określić wartość procentową właściwości New Users w okno Właściwości. Edytujesz właściwości scenariusza testu obciążenia w Edytor testu obciążeniowego.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: bd7c23218fca3a501aa0c56684a4fea98d304252
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943773"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Instrukcje: Określanie procentu użytkowników wirtualnych korzystających z danych w pamięci podręcznej sieci Web

Po utworzeniu testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego** można zmienić właściwości scenariuszy, aby spełniały potrzeby testowania i cele przy użyciu **Edytor testu obciążeniowego**. Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisów, zobacz [właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Wartość procentowa właściwości New Users** jest ustawiana w oknie **Właściwości** . Edytujesz właściwości scenariusza testu obciążenia w **Edytor testu obciążeniowego**.

**Wartość procentowa właściwości New Users** ma wpływ na sposób, w jaki test obciążenia symuluje buforowanie wykonywane przez przeglądarkę sieci Web. Domyślnie **wartość procentowa właściwości New Users** jest równa 0%. Jeśli wartość dla wartości **procentowej właściwości nowy użytkownik** jest równa 100%, każdy przebieg testu wydajności sieci Web w teście obciążenia jest traktowany jak użytkownik po raz pierwszy do witryny sieci Web, która nie ma żadnej zawartości z witryny sieci Web w swojej pamięci podręcznej przeglądarki od wcześniejszych odwiedzin. W związku z tym wszystkie żądania w teście sieci Web, w tym wszystkie żądania zależne, takie jak obrazy, są pobierane.

> [!NOTE]
> Gdy ten sam zasób pamięci podręcznej jest żądany więcej niż raz w teście sieci Web, żądania nie są pobierane.

Jeśli testujesz witrynę sieci Web, która ma znaczną liczbę użytkowników zwracających, którzy prawdopodobnie mają obrazy i inne buforowane elementy pamięci podręcznej, to ustawienie 100% dla **wartości procentowej nowych użytkowników** spowoduje wygenerowanie większej liczby żądań pobierania niż w świecie rzeczywistym. W takim przypadku należy oszacować procent wizyt w witrynie sieci Web, które są od użytkowników po raz pierwszy, i ustawić odpowiednio **wartość procentową dla nowych użytkowników** .

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>Aby określić procent nowych użytkowników dla scenariusza

1. Otwórz test obciążenia.

     Zostanie wyświetlona **Edytor testu obciążeniowego** . Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **scenariuszy** drzew testów obciążenia wybierz węzeł scenariusza, dla którego chcesz zmienić nową wartość procentową użytkownika.

3. W menu **Widok** wybierz polecenie **okno właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości** .

4. Ustaw wartość **procentu właściwości nowy użytkownik** , wprowadzając liczbę dla wartości procentowej nowych użytkowników.

5. Po zakończeniu zmiany właściwości wybierz pozycję **Zapisz** w menu **plik** . Następnie możesz uruchomić test obciążenia, korzystając z nowego **procentu wartości nowych użytkowników** .

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
- [Edytuj wzorce obciążenia, aby modelować działania użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md)
