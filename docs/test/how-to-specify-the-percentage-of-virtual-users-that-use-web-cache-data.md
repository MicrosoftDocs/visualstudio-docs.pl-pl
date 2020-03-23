---
title: 'Test ładowania: ustawianie procentu użytkownika wirtualnego przy użyciu danych pamięci podręcznej sieci Web'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cac3368d0f03c268e086cc8636f1175a15effdd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113358"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Jak: Określ procent użytkowników wirtualnych korzystających z danych pamięci podręcznej sieci Web

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążenia**można zmienić właściwości scenariuszy, aby spełnić twoje potrzeby i cele testowania za pomocą **Edytora testów obciążenia**. Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisy, zobacz [Właściwości scenariusza testu obciążenia.](../test/load-test-scenario-properties.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Właściwość **Procent nowych użytkowników** jest ustawiona w oknie **Właściwości.** Można edytować właściwości scenariusza testu obciążenia w **Edytorze testów obciążenia**.

Właściwość **Procent nowych użytkowników** wpływa na sposób, w jaki test obciążenia symuluje buforowanie, które byłoby wykonywane przez przeglądarkę sieci web. Domyślnie **właściwość Procent nowych użytkowników** jest ustawiona na 0%. Jeśli wartość dla **procentu nowych użytkowników** właściwości jest ustawiona na 100%, każdy test wydajności sieci web uruchomić w teście obciążenia jest traktowany jak po raz pierwszy użytkownika do witryny sieci Web, który nie ma żadnej zawartości z witryny sieci Web w pamięci podręcznej przeglądarki z poprzednich wizyt. W związku z tym wszystkie żądania w teście sieci web, w tym wszystkie żądania zależne, takie jak obrazy, są pobierane.

> [!NOTE]
> Gdy ten sam zasób buforowa jest wymagany więcej niż jeden raz w teście sieci web, żądania nie są pobierane.

Jeśli testujesz obciążenie witryny sieci Web, która ma znaczną liczbę powracających użytkowników, którzy mogą mieć obrazy i inną zawartość buforowaną w pamięci podręcznej lokalnie, ustawienie 100% dla **procentu nowych użytkowników** właściwości wygeneruje więcej żądań pobierania niż miałoby to miejsce w rzeczywistych użyciach. W takim przypadku należy oszacować procent odwiedzin w witrynie, które pochodzą od pierwszych użytkowników witryny, i odpowiednio ustawić **udział procentowy nowych użytkowników.**

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>Aby określić procent nowych użytkowników dla scenariusza

1. Otwórz test obciążenia.

     Pojawi się **Edytor testów obciążenia.** Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze Drzewa testów obciążenia **wybierz** węzeł scenariusza, dla którego chcesz zmienić wartość procentową nowego użytkownika.

3. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości.**

4. Ustaw wartość dla **procentu nowych użytkowników** właściwości, wprowadzając liczbę dla procentu nowych użytkowników.

5. Po zakończeniu zmiany właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia przy użyciu nowej wartości **Procent nowych użytkowników.**

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
- [Edytowanie wzorców obciążenia w celu modelowania działań użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md)
