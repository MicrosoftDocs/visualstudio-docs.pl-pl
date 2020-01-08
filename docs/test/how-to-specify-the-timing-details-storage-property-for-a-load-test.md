---
title: Właściwości magazynowania szczegółów chronometrażu dla ustawień uruchomienia testu obciążenia
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591648"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Porady: Określanie właściwości magazynowania szczegółów chronometrażu dla ustawień przebiegu testu obciążeniowego

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** Aby zmienić ustawienia w celu spełnienia potrzeb i celów testowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Możesz edytować ustawienia przebiegu **przechowywanie informacji** wartości właściwości w **właściwości** okna. **Przechowywanie informacji** właściwość można ustawić na dowolną z następujących opcji:

- **Wszystkie szczegółowe dane:** zbiera i przechowuje dane o poszczególnych chronometrażach dla każdego testu, transakcji i strony podczas testu.

  > [!NOTE]
  > **Wszystkie szczegółowe dane** należy wybrać opcję, aby włączyć informacje o danych użytkownika wirtualnego w wyniki testu obciążenia. Aby uzyskać więcej informacji, zobacz [analizować aktywność wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

- **Brak:** nie gromadzi żadnych indywidualnych szczegółów chronometrażu. Jednakże wartości średnie są nadal dostępne.

- **Tylko statystyki:** przechowuje dane o poszczególnych chronometrażach, ale tylko jako danych percentyl. Oszczędza to zasoby miejsca.

  **Zagadnienia dotyczące właściwości magazynowania szczegółów chronometrażu**

  Jeśli **przechowywanie informacji** właściwość jest włączona, a następnie to czas na wykonanie każdego indywidualnego testu, transakcji i strony podczas testu obciążenia, które będą przechowywane w repozytorium wyników testu obciążenia. Umożliwia to 90 i 95. percentyl danych w **analizatora testu obciążenia** w **testy**, **transakcji**, i **stron** tabele.

  Jeśli **przechowywanie informacji** właściwość jest włączona, ustawiając jej wartość na wartość **StatisticsOnly** lub **AllIndividualDetails**, wszystkie poszczególne testy, strony, a transakcje są upłynął limit czasu i percentyli są obliczane na podstawie danych o poszczególnych chronometrażach. Różnica polega na tym, wraz z **StatisticsOnly** opcję po obliczono danych percentyl, o poszczególnych chronometrażach, dane są usuwane z repozytorium. Zmniejsza to ilość miejsca wymaganego w repozytorium, gdy są używane szczegółów chronometrażu. Jednakże może zaistnieć potrzeba przetwarzania danych szczegółów chronometrażu w inny sposób za pomocą narzędzia SQL, w którym to przypadku **AllIndividualDetails** tak, aby dane szczegółowe chronometrażu były dostępne dla tego przetwarzania, należy użyć opcji. Ponadto jeśli właściwość jest ustawiona **AllIndividualDetails**, następnie można analizować aktywności wirtualnego użytkownika za pomocą **wykres aktywności wirtualnych użytkowników** w **analizatora testu obciążenia** po zakończeniu testu obciążenia. Aby uzyskać więcej informacji, zobacz [analizować aktywność wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

  Ilość miejsca wymaganego w repozytorium wyników testu obciążenia do przechowywania szczegółowych danych o chronometrażu mogą być bardzo duże, szczególnie w przypadku uruchamiania dłuższych testów obciążenia. Ponadto czas przechowywania tych danych w teście obciążenia, które repozytorium wyników na koniec testu obciążenia jest dłuższy, ponieważ te dane są przechowywane w agentach testowych obciążenia do momentu zakończenia testów obciążenia wykonywania, które dane są przechowywane w repozytorium. **Przechowywanie informacji** właściwość jest domyślnie włączona. Jeśli jest to problem dla środowiska testowego, warto ustawić **przechowywanie informacji** do **Brak**.

  Szczegółowych informacji o czasie, dane są przechowywane w *loadtestitemresults.dat w czasie testu* zgłaszanych w trakcie sesji i są wysyłane do kontrolera, po zakończeniu testu obciążenia. Dla testu obciążenia uruchomione przez długi czas rozmiar pliku jest duży. Jeśli na maszynie agenta jest za mało miejsca na dysku, to będzie problem.

  Jeśli uaktualniasz projekt z poprzedniej wersji programu Visual Studio test obciążenia, należy użyć poniższej procedury w celu umożliwienia zbierania pełnych szczegółów.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Aby skonfigurować właściwości magazynowania szczegółów chronometrażu w teście obciążeniowym

1. Otwórz test obciążenia w edytorze testu obciążenia.

2. Rozwiń **parametrów uruchomieniowych** węzła w teście obciążeniowym.

3. Wybierz polecenie dotyczące wykonywania ustawień, które chcesz skonfigurować, na przykład **Uruchom ustawienia1 [aktywne]** .

4. Otwórz **właściwości** okna. Na **widoku** menu, wybierz opcję **okno właściwości**.

5. W obszarze **wyniki** kategorii, wybierz **przechowywanie informacji** właściwości i wybierz pozycję **wszystkie szczegółowe dane**.

     Po skonfigurowaniu **wszystkie szczegółowe dane** ustawienie **przechowywanie informacji** właściwości, można uruchamiać obciążenia testowania i wyświetlania **wykres aktywności wirtualnych użytkowników**. Aby uzyskać więcej informacji, zobacz [porady: analizowanie, co robią użytkownicy wirtualni podczas testu obciążeniowego](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Przewodnik: Używanie wykresu wirtualnego aktywności użytkownika umożliwiającego Wyizolowanie problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
