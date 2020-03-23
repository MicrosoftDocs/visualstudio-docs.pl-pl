---
title: Zapisz dziennik testu obciążenia dla błędów testów
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b47010a68520379afd8e0d969fa99169cb1ff0b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588957"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Jak: Określ, czy błędy testu są zapisywane w dziennikach testowych za pomocą Edytora testów obciążenia

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążenia**można użyć **Edytora testów obciążenia,** aby zmienić właściwości testu obciążenia, aby spełnić twoje potrzeby i cele testowania. Zobacz [Przewodnik: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md). Można określić, czy dziennik testu ma być zapisany, jeśli test zakończy się niepowodzeniem w teście obciążenia, zmieniając **save log on test failure** właściwości.

> [!NOTE]
> Aby uzyskać pełną listę właściwości ustawień uruchamiania i ich opisy, zobacz [Właściwości ustawień przebiegu testu ładowania](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Aby określić, czy dziennik testu jest zapisywany, gdy test zakończy się niepowodzeniem w scenariuszu

1. Otwórz test obciążenia.

     Pojawi się **Edytor testów obciążenia.** Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **Uruchom ustawienia** drzew testu obciążenia wybierz węzeł ustawień uruchamiania, dla którego chcesz określić maksymalną liczbę iteracji testowych.

3. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Kategorie i właściwości ustawień uruchamiania są wyświetlane w oknie **Właściwości.**

4. We właściwości **Zapisz błąd testu dzienniku** wybierz wartość **Prawda** lub **Fałsz,** aby określić, czy dziennik testu ma zostać zapisane w przypadku niepowodzenia testu w scenariuszu.

     Po zakończeniu zmiany właściwości wybierz polecenie **Zapisz** w menu **Plik.**

     Dane zapisane w dzienniku można przeglądać za pomocą widoku Tabele analizatora testów obciążenia. Aby uzyskać więcej informacji, zobacz [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
