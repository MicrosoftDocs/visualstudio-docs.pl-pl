---
title: Zastosuj rozkład do opóźnienia tempem na potrzeby testowania obciążenia
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa5d3239e3b096a2018d6ef9c9b3c6666dcd31c3
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288276"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Instrukcje: stosowanie dystrybucji do opóźnienia tempem dla modelu testu tempa użytkownika

Po utworzeniu testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego**można użyć Edytor testu obciążeniowego, aby zmienić właściwości scenariusza, aby spełniały potrzeby testowania i cele.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Właściwość **Zastosuj dystrybucję do tempem opóźnienie** jest ustawiana za pomocą okna **Właściwości** . Właściwości scenariusza testu obciążenia są modyfikowane przy użyciu Edytor testu obciążeniowego.

> [!NOTE]
> Właściwość **apply Distribution to tempem** ma zastosowanie tylko wtedy, gdy *mieszany test obciążenia* jest skonfigurowany na podstawie tempa użytkownika. Aby uzyskać więcej informacji, zobacz [Edit Text mix models, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Wartość dla **opóźnienia Apply tempem** można ustawić na wartość true lub false:

- **Prawda**: scenariusz stosuje normalne opóźnienia dystrybucji statystycznej, które są określone przez wartość w kolumnie **testy na użytkownika na godzinę** w oknie dialogowym **Edytowanie testu mieszanego** . Aby uzyskać więcej informacji, zobacz [Edit Text mix models, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Załóżmy na przykład, że masz **testy na użytkownika na godzinę** w oknie dialogowym **Edytowanie testu mieszanego** dla testu dla zestawu testów dwóch użytkowników na godzinę. Jeśli właściwość **Zastosuj dystrybucję do tempem** jest ustawiona na **wartość true**, normalna dystrybucja statystyczna jest stosowana do czasu oczekiwania między testami. Testy będą nadal uruchamiać dwa testy na godzinę, ale nie musi to być opóźnienie 30 minut między nimi. Pierwszy test można uruchomić po upływie czterech minut, a drugi test po 45 minutach.

- **Fałsz**: testy są uruchamiane w tempie określonym dla wartości w kolumnie **testy na użytkownika na godzinę** w oknie dialogowym **Edytowanie testu mieszanego** . Aby uzyskać więcej informacji, zobacz [Edit Text mix models, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Załóżmy na przykład, że masz **testy na użytkownika na godzinę** w oknie dialogowym **Edytowanie testu mieszanego** dla testu dla zestawu testów dwóch użytkowników na godzinę. Jeśli właściwość **Zastosuj dystrybucję do tempem** jest ustawiona na **wartość FAŁSZ**, nastąpi brak Leeway, gdy testy są uruchamiane. Test będzie uruchamiany co 30 minut. Daje to pewność, że wykonujesz dwa testy na godzinę.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Aby określić ustawienie właściwości Zastosuj dystrybucję do tempem dla scenariusza

1. Otwórz test obciążenia.

   Zostanie wyświetlona **Edytor testu obciążeniowego** . Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **scenariusze** drzewa testu obciążenia wybierz węzeł scenariusza, do którego ma zostać zastosowana dystrybucja tempem.

3. W menu **Widok** wybierz polecenie **okno właściwości**.

   Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości** .

4. W polu wartość właściwości dla opcji **Zastosuj dystrybucję do tempem**wybierz wartość **prawda** lub **Fałsz**.

5. Wybierz pozycję **plik**  >  **Zapisz**. Teraz można uruchomić test obciążenia z nową wartością **opóźnienia Zastosuj dystrybucję do tempem** .

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
