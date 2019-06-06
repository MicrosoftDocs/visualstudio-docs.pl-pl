---
title: Tworzenie raportów wydajności testu obciążenia za pomocą programu Microsoft Excel
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6bd73c643cdc01be07d56857f65d3fb34c6346e0
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747581"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Instrukcje: Tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel

Można generować raporty testu obciążenia programu Microsoft Excel, które opierają się na dwóch lub więcej wynikach badań.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Dostępne są dwa typy raportów testów obciążenia:

- **Uruchom porównanie** tworzy zestaw raportów, który porównuje dane z dwóch wyniki testu obciążenia za pomocą tabel i wykresów słupkowych.

- **Trend** możesz wygenerować analizy trendu na podstawie dwóch lub więcej wyników testu obciążenia. Wyniki są wyświetlane przy użyciu wykresów liniowych, ale dane są dostępne w raportach tabeli przestawnej.

> [!TIP]
> Można również ręcznie utworzyć raporty w programie Microsoft Word przez kopiowanie i wklejanie danych z widoku podsumowania, widoku wykresów i widoku tabel. Zobacz [jak: Ręczne tworzenie raportu wydajności testu obciążenia przy użyciu programu Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

Raport może służyć do udostępniania danych dotyczących wydajności zainteresowanym osobom i przekazywania, czy ogólna wydajność i kondycja systemu jest coraz lepsza czy gorsza.

Definicje raportów są przechowywane w bazie danych testu obciążenia. Po zapisaniu raportu definicja raportu jest zapisywany w bazie danych i może być ponownie wykorzystana później.

Ponadto skoroszytu programu Excel mogą być udostępniane zainteresowane strony, aby nie trzeba połączyć z bazą danych, aby wyświetlić raport zainteresowanych stron.

> [!NOTE]
> Możesz udostępnić skoroszyt programu Excel; jednak tylko w przypadku użytkowników, którzy mają zainstalowany na swoim komputerze program Visual Studio będą mogli modyfikować arkusze kalkulacyjne. Inni użytkownicy nie zobaczą **raport z testu obciążenia** opcji **Office** wstążki, ale będą mogli przeglądać skoroszyt.

Na poniższej ilustracji przedstawiono przykładowy raport, który pokazuje związek między spadkiem szybkości transakcji (Aktualizuj koszyk) a zwyrodnieniem licznika (% procesora). To wskazuje na potencjalny problem w kodzie aplikacji, a nie bazy danych lub w sieci i jest dobrym kandydatem do diagnozowania przy użyciu Profiler platformy ASP.NET.

![Potencjalny problem w kodzie aplikacji](../test/media/lt_excel.png)

Raporty programu Excel można albo wygenerować w **analizatora testu obciążenia**, za pomocą **Utwórz raport programu Excel** przycisk na pasku narzędzi lub z programu Excel przy użyciu **raport z testu obciążenia** opcji **testu obciążeniowego** karcie **Office** wstążki.

> [!NOTE]
> Po dodaniu komentarzy do testu obciążenia są wyświetlane w raporcie programu Excel.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Aby wygenerować raporty porównania testów obciążenia za pomocą programu Excel

1. Przed wygenerowaniem raportu, należy najpierw uruchomić test obciążenia.

2. Można utworzyć raporty testu obciążenia programu Excel na dwa sposoby:

   - Po zakończeniu testu obciążenia w **wyników testu obciążeniowego** wybierz **Utwórz raport programu Excel** przycisku na pasku narzędzi.

      > [!NOTE]
      > Jeśli **Utwórz raport programu Excel** przycisk jest niedostępny w **podglądu wyników testu wydajności sieci Web** narzędzi może być konieczne uruchomienie programu Microsoft Excel jeden raz przed jego włączeniem. Po zainstalowaniu programu Visual Studio Enterprise programu Visual Studio Enterprise load test dodatek programu jest kopiowany do komputera dla programu Microsoft Excel; jednak należy uruchomić programu Microsoft Excel, aby ukończyć proces instalacji dodatku.

      Microsoft Excel otwiera się przy użyciu **Generowanie kreatora raportu testu obciążenia**.

   **OR**

   1. Otwórz program Microsoft Excel, zaznacz **testu obciążeniowego** karcie **Office** wstążki, a następnie wybierz **raport z testu obciążenia**.

       **Generowanie kreatora raportu testu obciążenia** pojawia się.

   2. W **wybierz bazę danych zawierającą testy obciążeniowe** w obszarze **nazwy serwera**, wpisz nazwę serwera zawierającego wyniki testu obciążenia.

   3. W **Nazwa bazy danych** listę rozwijaną, wybierz bazę danych zawierającą wyniki testu obciążenia na liście.

3. W **jak chcesz wygenerować raport** Sprawdź, czy **utworzyć raport** jest zaznaczone, a następnie wybierz **dalej**.

4. W **jaki typ raportu chcesz wygenerować** Sprawdź, czy **Uruchom porównanie** jest zaznaczone, a następnie wybierz **dalej**.

5. W **szczegóły raportu testu obciążeniowego Enter** strony, wpisz nazwę dla raportu w **Nazwa raportu**.

6. Zaznacz test obciążeniowy, aby wygenerować raport i wybierz polecenie **dalej**.

7. W **wybierz przebiegi do raportu** w obszarze **wybierz co najmniej jeden przebieg do dodania do raportu**wybierz dwa wyniki testów, które chcesz porównać w raporcie, a następnie wybierz obciążenia **dalej**.

   > [!NOTE]
   > Możesz tylko wygenerować raport porównawczy dla wyników dwóch testów obciążenia. Jeśli wybierzesz albo jeden wynik testu obciążenia lub więcej niż dwa wyniki testów obciążenia, pojawi się komunikat ostrzegawczy.

8. W **Wybierz liczniki do raportu** w obszarze **wybierz co najmniej jeden licznik do dodania do raportu** rozwijana lista liczników jest dostępna w celu dostosowywania raportu. Wybierz liczniki, które chcesz porównać dwie wybrane uruchomienia testu w raporcie, a następnie wybierz **Zakończ**.

9. Z następującymi kartami arkusza kalkulacyjnego jest generowany raport skoroszytu programu Excel:

   - **Spis treści** — Wyświetla nazwę raportu testu obciążenia oraz spis treści z łączami do różnych kart w raporcie.

   - **Uruchamia -** zawiera szczegółowe informacje, na które dwa przebiegi są porównywane w raporcie.

   - **Porównanie testów -** zawiera wykresu słupkowego szczegóły dotyczące regresji wydajności i ulepszeń między dwoma porównywanymi przebiegami.

   - **Porównanie stron —** zawiera wykres słupkowy i wydajności procent dane porównania między dwoma przebiegami na różnych stronach w przebiegu testowym.

   - **Porównanie - komputerów** zawiera dane porównawcze między dwoma przebiegami na podstawie maszyn, które były używane.

   - **Porównanie błędów —** porównuje typy błędów napotkanych między dwoma uruchomieniami i liczbę wystąpień.

     > [!TIP]
     > Aby uzyskać lepsze raporty kilka właściwości są dostępne w testach obciążenia i testy wydajności sieci web, które umożliwiają bardziej rozbudowane raporty. Żądanie strony ma dwie właściwości, które są wyświetlane w raportach: Cel i nazwa raportowania. Czasy reakcji stron będą raportowane względem celu, a nazwa raportowania będzie używana zamiast adresu URL w raportach. W teście obciążeniowym parametrów uruchomieniowych, w obszarze Zarządzaj zbiorem liczników właściwość znaczniki komputerów jest przedstawiona w nazwach komputerów raportów. Jest to bardzo przydatne do opisywania roli danej maszyny w raporcie.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Aby wygenerować raporty trendów testów obciążenia za pomocą programu Excel

1. Przed wygenerowaniem raportu, należy uruchomić test obciążenia.

2. Można utworzyć raporty testu obciążenia programu Excel na dwa sposoby:

   - Po zakończeniu testu obciążenia w **wyników testu obciążeniowego** wybierz **Utwórz raport programu Excel** przycisku na pasku narzędzi.

      > [!NOTE]
      > Jeśli **Utwórz raport programu Excel** przycisk jest niedostępny w **podglądu wyników testu wydajności sieci Web** narzędzi może być konieczne uruchomienie programu Microsoft Excel jeden raz przed jego włączeniem. Po zainstalowaniu programu Visual Studio Enterprise programu Visual Studio Enterprise load test dodatek programu jest kopiowany do komputera dla programu Microsoft Excel; jednak należy uruchomić programu Microsoft Excel, aby ukończyć proces instalacji dodatku.

      Microsoft Excel otwiera się przy użyciu **Generowanie kreatora raportu testu obciążenia**.

   **OR**

   1. Otwórz program Microsoft Excel, zaznacz **testu obciążeniowego** karcie **Office** wstążki, a następnie wybierz **raport z testu obciążenia**.

       **Generowanie kreatora raportu testu obciążenia** pojawia się.

   2. W **wybierz bazę danych zawierającą testy obciążeniowe** w obszarze **nazwy serwera**, wpisz nazwę serwera zawierającego wyniki testu obciążenia.

   3. W **Nazwa bazy danych** listę rozwijaną, wybierz bazę danych zawierającą wyniki testu obciążenia na liście.

3. W **jak chcesz wygenerować raport** Sprawdź, czy **utworzyć raport** jest zaznaczone, a następnie wybierz **dalej**.

4. W **jaki typ raportu chcesz wygenerować** Sprawdź, czy **Trend** jest zaznaczone, a następnie wybierz **dalej**.

5. W **szczegóły raportu testu obciążeniowego Enter** strony, wpisz nazwę dla raportu w **Nazwa raportu**.

6. Zaznacz test obciążeniowy, aby wygenerować raport i wybierz polecenie **dalej**.

7. W **wybierz przebiegi do raportu** w obszarze **wybierz co najmniej jeden przebieg do dodania do raportu**, zaznacz wyniki testów obciążenia, które chcesz porównać w raporcie, a następnie wybierz **dalej**.

8. W **Wybierz liczniki do raportu** w obszarze **wybierz co najmniej jeden licznik do dodania do raportu**, rozwijana lista liczników jest dostępna w celu dostosowywania raportu. Wybierz liczniki, które chcesz porównać dla analizy trendu i wybierz przycisk **Zakończ**.

9. Raport jest generowany ze spisem treści, zawierającym łącza do różnych kart skoroszytu programu Excel generowanych w raporcie. Łącza są oparte na licznikach wybranych dla raportu trendu. Na przykład jeśli domyślne liczniki wybrane w kroku 7, następnie raport wygeneruje dane, które są przedstawiane na osobnych kartach w programie Excel dla każdego licznika wymienionego w kroku 7. Dane, który jest generowany dla każdego licznika są przedstawione w wykresów trend styl.

   > [!TIP]
   > Aby uzyskać lepsze raporty kilka właściwości są dostępne w testach obciążenia i testy wydajności sieci web, które umożliwiają bardziej rozbudowane raporty. Żądanie strony ma dwie właściwości, które są wyświetlane w raportach: Cel i nazwa raportowania. Czasy reakcji stron będą raportowane względem celu, a nazwa raportowania będzie używana zamiast adresu URL w raportach. W teście obciążeniowym parametrów uruchomieniowych, w obszarze Zarządzaj zbiorem liczników właściwość znaczniki komputerów jest przedstawiona w nazwach komputerów raportów. Jest to bardzo przydatne do opisywania roli danej maszyny w raporcie.

## <a name="net-security"></a>Zabezpieczenia platformy .net

Wyniki testu obciążenia i raporty zawierają potencjalnie poufne informacje, które mogą być używane do zorganizowania ataku na komputer użytkownika lub sieci. Wyniki testu obciążenia i raporty zawierają nazwy komputerów i parametry połączenia. Należy pamiętać o tym kiedy raportów testów obciążenia są udostępniane innym osobom.

## <a name="see-also"></a>Zobacz także

- [Testy obciążenia raport wyników dla potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md)