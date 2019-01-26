---
title: Zapisz dziennik testu obciążenia w przypadku niepowodzenia testów
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: f35d4488add1f66ef8ee57d3a2b1125c4284ef9b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932561"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Instrukcje: Określ, czy niepowodzenia testu są zapisywane do testowania dzienników za pomocą edytora testu obciążenia

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** można zmienić właściwości testu obciążenia w celu spełnienia potrzeb i celów testowania. Zobacz [instruktażu: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md). Można określić, jeśli chcesz mieć Dziennik testu zapisany, jeśli test zakończy się niepowodzeniem w teście obciążeniowym, zmieniając **Zapisz dziennik w przypadku niepowodzenia testu** właściwości.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Aby określić, jeśli dziennik testu jest zapisywany, gdy test zakończy się niepowodzeniem w przypadku scenariusza

1.  Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawia się. Zostanie wyświetlone drzewo testu obciążenia.

2.  Obciążenia test drzew **parametrów uruchomieniowych** folderu, wybierz węzeł parametrów uruchomieniowych, który chcesz określić maksymalną liczbę iteracji testu dla.

3.  Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie ustawień i właściwości są wyświetlane w **właściwości** okna.

4.  W **Zapisz dziennik w przypadku niepowodzenia testu** właściwości, wybierz opcję **True** lub **False** do określenia, czy chcesz zapisać dziennik testu w przypadku niepowodzenia testu w scenariuszu.

     Po zakończeniu, zmiana wartości właściwości, wybierz **Zapisz** na **pliku** menu.

     Dane, które są zapisywane w dzienniku można wyświetlać przy użyciu widoku tabeli analizatora testu obciążenia. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md)