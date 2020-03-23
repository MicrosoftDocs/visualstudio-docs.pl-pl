---
title: Właściwość magazynu szczegółów chronometrażu dla ustawienia przebiegu testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbd3b2a7d7e56870a994af288f5887f1d86256af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591648"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Jak: Określ właściwość magazynu szczegółów chronometrażu dla ustawienia przebiegu testu obciążenia

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążenia**można użyć **Edytora testów obciążenia,** aby zmienić ustawienia, aby spełnić twoje potrzeby i cele testowe.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Można edytować wartość właściwości **Chronometracie szczegóły chronometrażu** w oknie **Właściwości.** Właściwość **Magazyn szczegółów chronometrażu** można ustawić na dowolną z następujących opcji:

- **Wszystkie szczegółowe informacje:** Zbiera i przechowuje indywidualne dane chronometrażu dla każdego testu, transakcji i strony wystawionej podczas testu.

  > [!NOTE]
  > Aby włączyć informacje o danych użytkownika wirtualnego w wynikach testu obciążenia, należy wybrać opcję **Wszystkie szczegóły szczegółowe.** Aby uzyskać więcej informacji, zobacz [Analizowanie aktywności użytkownika wirtualnego w widoku Szczegóły](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

- **Brak:** Nie zbiera żadnych indywidualnych szczegółów chronometrażu. Jednak średnie wartości są nadal dostępne.

- **Tylko statystyki:** Przechowuje poszczególne dane chronometrażu, ale tylko jako dane percentyla. Pozwala to zaoszczędzić zasoby miejsca.

  **Zagadnienia dotyczące właściwości magazynu szczegółów chronometrażu**

  Jeśli właściwość **magazyn szczegółów chronometrażu** jest włączona, czas wykonania każdego testu, transakcji i strony podczas testu obciążenia będzie przechowywany w repozytorium wyników testu obciążenia. Dzięki temu dane 90 i 95 percentyl są wyświetlane w **analizatorze testów obciążenia** w **tabelach** **Testy,** Transakcje i **Strony.**

  Jeśli właściwość **Magazyn szczegółów chronometrażu** jest włączona, ustawiając jej wartość na **StatisticsOnly** lub **AllIndividualDetails**, wszystkie poszczególne testy, strony i transakcje są zdążone, a dane percentyla są obliczane na podstawie poszczególnych danych chronometrażu. Różnica polega na tym, że z **StatisticsOnly** opcji, po obliczeniu danych percentyla, poszczególne dane chronometrażu są usuwane z repozytorium. Zmniejsza to ilość miejsca, która jest wymagana w repozytorium, gdy używane są szczegóły chronometrażu. Jednak można przetworzyć dane szczegółów chronometrażu w inny sposób przy użyciu narzędzi SQL, w którym to przypadku **AllIndividualDetails** opcja powinna być używana tak, aby dane szczegółów chronometrażu jest dostępny dla tego przetwarzania. Ponadto jeśli ustawisz właściwość na **AllIndividualDetails**, następnie można analizować działanie użytkownika wirtualnego przy użyciu **wykresu aktywności użytkownika wirtualnego** w **analizatorze testu obciążenia** po zakończeniu testu obciążenia. Aby uzyskać więcej informacji, zobacz [Analizowanie aktywności użytkownika wirtualnego w widoku Szczegóły](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

  Ilość miejsca wymaganego w repozytorium wyników testu obciążenia do przechowywania danych szczegółów chronometrażu może być bardzo duża, szczególnie w przypadku dłuższych testów obciążenia. Ponadto czas przechowywania tych danych w repozytorium wyników testu obciążenia na końcu testu obciążenia jest dłuższy, ponieważ te dane są przechowywane na agentach testu obciążenia, dopóki test obciążenia nie zakończy wykonywania, w którym czasie dane są przechowywane w repozytorium. Właściwość **Magazyn szczegółów chronometrażu** jest domyślnie włączona. Jeśli jest to problem dla środowiska testowego, można ustawić **magazyn szczegółów chronometrażu** na **Brak**.

  Dane szczegółów chronometrażu są przechowywane w pliku *LoadTestItemResults.dat* podczas uruchamiania i są wysyłane z powrotem do kontrolera po zakończeniu testu obciążenia. W przypadku testu obciążenia uruchomionego przez długi czas rozmiar pliku jest duży. Jeśli na komputerze agenta nie ma wystarczającej ilości miejsca na dysku, będzie to problem.

  Jeśli uaktualniasz projekt z poprzedniej wersji testu obciążenia programu Visual Studio, użyj poniższej procedury, aby włączyć pełną kolekcję szczegółów.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Aby skonfigurować właściwość magazynu szczegółów chronometrażu w teście obciążenia

1. Otwórz test obciążenia w edytorze testów obciążenia.

2. Rozwiń węzeł **Uruchom ustawienia** w teście obciążenia.

3. Wybierz ustawienia uruchamiania, które chcesz skonfigurować, na przykład **Uruchom ustawienia1[Aktywny]**.

4. Otwórz okno **Właściwości.** W menu **Widok** wybierz polecenie **Okno Właściwości**.

5. W kategorii **Wyniki** wybierz właściwość **Magazyn szczegółów chronometrażu** i wybierz pozycję **Wszystkie szczegółowe informacje**.

     Po skonfigurowaniu ustawienia **Wszystkie szczegóły indywidualne** dla właściwości Magazyn szczegółów **chronometrażu** można uruchomić test obciążenia i wyświetlić **wykres aktywności użytkownika wirtualnego**. Aby uzyskać więcej informacji, zobacz [Jak: Analizowanie, co użytkownicy wirtualni robią podczas testu obciążenia](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Zobacz też

- [Analizowanie aktywności użytkownika wirtualnego w widoku Szczegóły](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Przewodnik: Używanie wykresu aktywności użytkownika wirtualnego do izolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
