---
title: Właściwość przechowywania szczegółów czasu dla ustawienia przebiegu testu obciążenia
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0225ae23ed141b317d4424da573593d446766f43
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287314"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Instrukcje: Określanie właściwości przechowywania informacji o chronometrażu dla ustawienia przebiegu testu obciążenia

Po utworzeniu testu obciążenia z **nowym Kreator testu obciążeniowego**można użyć **Edytor testu obciążeniowego** , aby zmienić ustawienia w celu spełnienia wymagań dotyczących testowania i celów.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Wartość właściwości **przechowywania informacji o chronometrażu** ustawienia przebiegu można edytować w oknie **Właściwości** . Właściwość **przechowywania informacji o chronometrażu** można ustawić na dowolną z następujących opcji:

- **Wszystkie dane osobowe:** Zbiera i przechowuje poszczególne dane chronometrażu dla każdego testu, transakcji i strony wystawionych podczas testu.

  > [!NOTE]
  > Należy wybrać opcję **wszystkie szczegółowe** informacje, aby włączyć informacje o wirtualnych danych użytkownika w wynikach testu obciążenia. Aby uzyskać więcej informacji, zobacz [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

- **Brak:** Nie zbiera żadnych szczegółowych informacji o chronometrażu. Jednak wartości średnie są nadal dostępne.

- **Tylko statystyki:** Przechowuje dane poszczególnych czasów, ale tylko jako dane percentylu. Spowoduje to zapisanie zasobów miejsca.

  **Zagadnienia dotyczące właściwości przechowywania informacji o chronometrażu**

  Jeśli właściwość **przechowywanie informacji** o czasie jest włączona, czas wykonywania poszczególnych testów, transakcji i stron podczas testu obciążenia będzie przechowywany w repozytorium wyników testu obciążenia. Pozwala to na wyświetlanie 90 i używany 95. percentylu danych w **analizatorze testu obciążenia** w tabelach **testów**, **transakcji**i **stron** .

  Jeśli właściwość **przechowywanie informacji** o czasie jest włączona, ustawiając jej wartość na **StatisticsOnly** lub **AllIndividualDetails**, wszystkie indywidualne testy, strony i transakcje są czasowe, a dane percentylu są obliczane na podstawie poszczególnych danych o chronometrażu. Różnica polega na tym, że za pomocą opcji **StatisticsOnly** po obliczeniu danych percentylu dane o poszczególnych chronometrażach są usuwane z repozytorium. Zmniejsza to ilość miejsca wymaganego w repozytorium, gdy są używane szczegóły chronometrażu. Można jednak przetwarzać dane szczegółowe o chronometrażu w inny sposób przy użyciu narzędzi SQL, w tym przypadku należy użyć opcji **AllIndividualDetails** , aby dane szczegółowe chronometrażu były dostępne dla tego przetwarzania. Ponadto, jeśli właściwość zostanie ustawiona na **AllIndividualDetails**, można analizować aktywność wirtualnego użytkownika za pomocą **wykresu aktywności wirtualnego użytkownika** w **analizatorze testu obciążenia** po zakończeniu testu obciążenia. Aby uzyskać więcej informacji, zobacz [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

  Ilość miejsca wymaganego w repozytorium wyników testu obciążenia do przechowywania danych szczegółów chronometrażu może być bardzo duża, szczególnie w przypadku dłuższych testów obciążenia. Ponadto czas przechowywania tych danych w repozytorium wyników testu obciążenia na końcu testu obciążenia jest dłuższy, ponieważ te dane są przechowywane w agentach testów obciążenia do momentu zakończenia testu obciążenia, podczas gdy dane są przechowywane w repozytorium. Właściwość **przechowywania szczegółów czasu** jest domyślnie włączona. Jeśli jest to problem dla środowiska testowego, można ustawić **przechowywanie informacji o chronometrażu** na **Brak**.

  Dane dotyczące chronometrażu są przechowywane w pliku *LoadTestItemResults. dat* podczas przebiegu i są wysyłane z powrotem do kontrolera po zakończeniu testu obciążenia. W przypadku testu obciążenia działającego przez długi czas rozmiar pliku jest duży. Jeśli na komputerze agenta nie ma wystarczającej ilości miejsca, może to być problem.

  Jeśli uaktualniasz projekt z poprzedniej wersji testu obciążenia programu Visual Studio, użyj poniższej procedury, aby włączyć zbieranie pełnych informacji.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Aby skonfigurować właściwość przechowywania informacji o chronometrażu w teście obciążenia

1. Otwórz test obciążenia w edytorze testu obciążenia.

2. Rozwiń węzeł **Parametry uruchomieniowe** w teście obciążenia.

3. Wybierz Parametry uruchomieniowe, które chcesz skonfigurować, na przykład **Uruchom Settings1 [Active]**.

4. Otwórz okno **Właściwości** . W menu **Widok** wybierz polecenie **okno właściwości**.

5. W kategorii **wyniki** wybierz właściwość **przechowywanie informacji** o czasie i wybierz **wszystkie szczegóły**.

     Po skonfigurowaniu ustawienia **wszystkie szczegółowe dane** dla właściwości **przechowywanie informacji o chronometrażu** można uruchomić test obciążenia i wyświetlić **Wykres aktywności wirtualnego użytkownika**. Aby uzyskać więcej informacji, zobacz [How to: analizowanie, co robią Użytkownicy wirtualną w trakcie testu obciążenia](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Zobacz też

- [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Przewodnik: używanie wykresu aktywności wirtualnego użytkownika w celu wyizolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
