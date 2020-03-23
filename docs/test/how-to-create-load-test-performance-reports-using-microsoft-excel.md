---
title: Tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8134d2652c1654a65ac303838bd1209a5d061bd0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589074"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Jak: Tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel

Można wygenerować raporty testów obciążenia programu Microsoft Excel, które są oparte na co najmniej dwóch wynikach testów.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Dostępne są dwa typy raportów z testów obciążenia:

- **Uruchom porównanie** Spowoduje to utworzenie zestawu raportów, który porównuje dane z dwóch wyników testu obciążenia przy użyciu tabel i wykresów słupkowych.

- **Trend** Można wygenerować analizę trendu na co najmniej dwóch wynikach testu obciążenia. Wyniki są wyświetlane przy użyciu wykresów liniowych, ale dane są dostępne w tabelach przestawnych.

> [!TIP]
> Raporty programu Microsoft Word można również tworzyć ręcznie, kopiując i wklejając dane z widoku podsumowania, widoku wykresów i tabel. Zobacz [Jak: Ręcznie utworzyć raport wydajności testu obciążenia przy użyciu programu Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

Każdy raport może służyć do udostępniania danych dotyczących wydajności zainteresowanym stronom i przekazywania, czy ogólna wydajność i kondycja systemu jest coraz lepsza, czy gorsza.

Definicje raportów są przechowywane w bazie danych testów obciążenia. Po zapisaniu raportu definicja raportu jest zapisywana w bazie danych i może być ponownie użyta później.

Ponadto skoroszyt programu Excel można udostępnić zainteresowanym stronom, aby zainteresowane strony nie musiały łączyć się z bazą danych w celu wyświetlenia raportu.

> [!NOTE]
> Skoroszytu programu Excel można udostępniać; jednak tylko użytkownicy, którzy mają visual studio zainstalowane na swoim komputerze będą mogli modyfikować dowolny z arkuszy kalkulacyjnych. Inni użytkownicy nie zobaczą opcji **Raport testu obciążenia** na wstążce pakietu **Office,** ale będą mogli wyświetlić skoroszyt.

Poniższa ilustracja jest przykładem raportu, który pokazuje korelację między spadkiem szybkości transakcji (Update Cart) a degeneracją licznika (% procesora). Wskazuje to na potencjalny problem w kodzie aplikacji, zamiast bazy danych lub sieci i jest dobrym kandydatem do zdiagnozowania przy użyciu ASP.NET Profiler.

![Potencjalny problem w kodzie aplikacji](../test/media/lt_excel.png)

Raporty programu Excel mogą być generowane w **analizatorze testów obciążenia,** za pomocą przycisku **Utwórz raport programu Excel** na pasku narzędzi lub z programu Excel za pomocą opcji **Raport testu obciążenia** na karcie **Testowanie obciążenia** na wstążce pakietu **Office.**

> [!NOTE]
> Jeśli dodasz komentarze do testu obciążenia, pojawią się one w raporcie programu Excel.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Aby wygenerować raporty porównania testów obciążenia przy użyciu programu Excel

1. Przed wygenerowaniem raportu należy najpierw uruchomić test obciążenia.

2. Raporty testów obciążenia programu Excel można tworzyć na dwa sposoby:

   - Po zakończeniu testu obciążenia na stronie **Wyniki testu obciążenia** wybierz przycisk **Utwórz raport programu Excel** na pasku narzędzi.

      > [!NOTE]
      > Jeśli przycisk **Utwórz raport programu Excel** jest wyłączony na pasku narzędzi **Podgląd wyników testów wydajności sieci Web,** może być konieczne uruchomienie programu Microsoft Excel jeden raz, zanim zostanie włączone. Po zainstalowaniu programu Visual Studio Enterprise dodatek testu obciążenia programu Visual Studio Enterprise jest kopiowany na komputer w programie Microsoft Excel; Jednak program Microsoft Excel musi być uruchomiony, aby zakończyć proces instalacji dodatku.

      Program Microsoft Excel zostanie otwarty z **Kreatorem generowania raportu testu obciążenia**.

   **Lub**

   1. Otwórz program Microsoft Excel, wybierz kartę **Testuj obciążenie** na wstążce **pakietu Office,** a następnie wybierz pozycję **Raport testu obciążenia**.

       Zostanie wyświetlony **Kreator generowania raportu testu obciążenia.**

   2. Na stronie **Wybierz bazę danych zawierającą testy obciążenia** w obszarze Nazwa **serwera**wpisz nazwę serwera zawierającego wyniki testu obciążenia.

   3. Na liście rozwijanej **Nazwa bazy danych** wybierz bazę danych zawierającą wyniki testu obciążenia.

3. Na stronie **Jak chcesz wygenerować raport,** sprawdź, czy wybrano **opcję Utwórz raport,** a następnie wybierz pozycję **Dalej**.

4. Na stronie **Jaki typ raportu chcesz wygenerować** sprawdź, czy jest **zaznaczone polecenie Uruchom porównanie,** a następnie wybierz pozycję **Dalej**.

5. Na stronie **Wprowadź szczegóły raportu testu obciążenia** wpisz nazwę raportu w polu Nazwa **raportu**.

6. Wybierz test obciążenia, dla którego chcesz wygenerować raport, i wybierz pozycję **Dalej**.

7. Na stronie **Wybierz biegi raportu** w obszarze **Wybierz jeden lub więcej przebiegów do dodania do raportu**wybierz dwa wyniki testu obciążenia, które chcesz porównać w raporcie, a następnie wybierz pozycję **Dalej**.

   > [!NOTE]
   > Raport porównawczy można wygenerować tylko na podstawie dwóch wyników testu obciążenia. Jeśli wybierzesz jeden wynik testu obciążenia lub więcej niż dwa wyniki testu obciążenia, pojawi się komunikat ostrzegawczy.

8. Na stronie **Wybierz liczniki raportu** w obszarze **Wybierz jeden lub więcej liczników do dodania do raportu** rozwijana lista liczników jest dostępna w celu dostosowania raportu. Wybierz liczniki, które chcesz porównać z dwóch wybranych przebiegów testowych w raporcie i wybierz pozycję **Zakończ**.

9. Raport skoroszytu programu Excel jest generowany przy następujących kartach arkusza kalkulacyjnego:

   - **Spis treści** — wyświetla nazwę raportu testu obciążenia i zawiera spis treści z łączami do różnych kart w raporcie.

   - **Biegi -** Zawiera szczegółowe informacje o tym, które dwa przebiegi są porównywane w raporcie.

   - **Porównanie testów -** Zawiera szczegóły wykresu słupkowego na temat regresji wydajności i ulepszeń między dwoma przebiegami, które są porównywane.

   - **Porównanie stron -** Zawiera wykres słupkowy i dane porównania wydajności procentowej między dwoma przebiegami na różnych stronach w przebiegach testowych.

   - **Porównanie maszyn -** Zawiera dane porównania między dwoma przebiegami na podstawie maszyn, które były używane.

   - **Porównanie błędów -** Porównuje typy błędów napotkanych między dwoma przebiegami i liczbę wystąpień.

     > [!TIP]
     > Dla lepszych raportów kilka właściwości są dostępne w testach obciążenia i testów wydajności sieci web, które umożliwiają bogatsze raporty. Żądanie strony ma dwie właściwości, które są prezentowane w raportach: Cel i Nazwa raportowania. Czasy odpowiedzi strony będą zgłaszane względem celu, a nazwa raportowania będzie używana zamiast adresu URL w raportach. W teście obciążenia Uruchom ustawienia w obszarze Zarządzanie zestawami liczników właściwość Znaczniki komputera jest prezentowana w nazwach komputerów raportu. Jest to bardzo przydatne do opisania roli określonej maszyny w raporcie.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Aby wygenerować raporty trendów testu obciążenia przy użyciu programu Excel

1. Przed wygenerowaniem raportu należy uruchomić test obciążenia.

2. Raporty testów obciążenia programu Excel można tworzyć na dwa sposoby:

   - Po zakończeniu testu obciążenia na stronie **Wyniki testu obciążenia** wybierz przycisk **Utwórz raport programu Excel** na pasku narzędzi.

      > [!NOTE]
      > Jeśli przycisk **Utwórz raport programu Excel** jest wyłączony na pasku narzędzi **Podgląd wyników testów wydajności sieci Web,** może być konieczne uruchomienie programu Microsoft Excel jeden raz, zanim zostanie włączone. Po zainstalowaniu programu Visual Studio Enterprise dodatek testu obciążenia programu Visual Studio Enterprise jest kopiowany na komputer w programie Microsoft Excel; Jednak program Microsoft Excel musi być uruchomiony, aby zakończyć proces instalacji dodatku.

      Program Microsoft Excel zostanie otwarty z **Kreatorem generowania raportu testu obciążenia**.

   **Lub**

   1. Otwórz program Microsoft Excel, wybierz kartę **Testuj obciążenie** na wstążce **pakietu Office,** a następnie wybierz pozycję **Raport testu obciążenia**.

       Zostanie wyświetlony **Kreator generowania raportu testu obciążenia.**

   2. Na stronie **Wybierz bazę danych zawierającą testy obciążenia** w obszarze Nazwa **serwera**wpisz nazwę serwera zawierającego wyniki testu obciążenia.

   3. Na liście rozwijanej **Nazwa bazy danych** wybierz bazę danych zawierającą wyniki testu obciążenia.

3. Na stronie **Jak chcesz wygenerować raport,** sprawdź, czy wybrano **opcję Utwórz raport,** a następnie wybierz pozycję **Dalej**.

4. Na stronie **Jaki typ raportu chcesz wygenerować,** sprawdź, czy trend jest zaznaczony, i wybierz pozycję **Dalej**. **Trend**

5. Na stronie **Wprowadź szczegóły raportu testu obciążenia** wpisz nazwę raportu w polu Nazwa **raportu**.

6. Wybierz test obciążenia, dla którego chcesz wygenerować raport, i wybierz pozycję **Dalej**.

7. Na stronie **Wybierz biegi raportu** w obszarze **Wybierz jeden lub więcej przebiegów do dodania do raportu**wybierz wyniki testu obciążenia, które chcesz porównać w raporcie, i wybierz pozycję **Dalej**.

8. Na stronie **Wybierz liczniki raportu** w obszarze **Wybierz jeden lub więcej liczników do dodania do raportu**dostępna jest rozwijana lista liczników, aby dostosować raport. Wybierz liczniki, które chcesz porównać do analizy trendów, a następnie wybierz pozycję **Zakończ**.

9. Raport jest generowany przy obliczu spisu treści zawierającego łącza do różnych kart skoroszytu programu Excel wygenerowanych w raporcie. Łącza są oparte na licznikach wybranych dla raportu trendu. Na przykład, jeśli pozostawisz liczniki domyślne wybrane w kroku 7, raport wygeneruje dane, które są prezentowane w oddzielnych kartach w programie Excel dla każdego licznika wymienionego w kroku 7. Dane generowane dla każdego licznika są prezentowane na wykresach w stylu trendu.

   > [!TIP]
   > Dla lepszych raportów kilka właściwości są dostępne w testach obciążenia i testów wydajności sieci web, które umożliwiają bogatsze raporty. Żądanie strony ma dwie właściwości, które są prezentowane w raportach: Cel i Nazwa raportowania. Czasy odpowiedzi strony będą zgłaszane względem celu, a nazwa raportowania będzie używana zamiast adresu URL w raportach. W teście obciążenia Uruchom ustawienia w obszarze Zarządzanie zestawami liczników właściwość Znaczniki komputera jest prezentowana w nazwach komputerów raportu. Jest to bardzo przydatne do opisania roli określonej maszyny w raporcie.

## <a name="net-security"></a>Zabezpieczenia platformy .NET

Wyniki testów obciążenia i raporty zawierają potencjalnie poufne informacje, które mogą być używane do tworzenia ataku na komputer lub sieć. Wyniki testów obciążenia i raporty zawierają nazwy komputerów i parametry połączenia. Należy o tym pamiętać podczas udostępniania raportów testów obciążenia innym osobom.

## <a name="see-also"></a>Zobacz też

- [Zgłoś wyniki testów obciążenia dla porównań testów lub analizy trendów](../test/compare-load-test-results.md)
