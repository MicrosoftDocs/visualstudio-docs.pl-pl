---
title: Tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a94a44d0a826cbda1d50b212f61bef86ad29f05c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287821"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Instrukcje: Tworzenie raportów wydajności testu obciążenia przy użyciu programu Microsoft Excel

Można generować raporty testów obciążenia programu Microsoft Excel, które są oparte na dwóch lub większej liczbie wyników testów.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Dostępne są dwa typy raportów testów obciążenia:

- **Wykonaj porównanie** Spowoduje to utworzenie zestawu raportów porównujących dane z dwóch wyników testów obciążenia przy użyciu tabel i wykresów słupkowych.

- **Trend** Można wygenerować analizę trendu na dwóch lub większej liczbie wyników testu obciążenia. Wyniki są wyświetlane przy użyciu wykresów liniowych, ale dane są dostępne w tabelach przestawnych.

> [!TIP]
> Możesz również ręcznie tworzyć raporty programu Microsoft Word przez kopiowanie i wklejanie danych z widoku podsumowania, widoku wykresów i widoku tabele. Zobacz [jak: ręcznie utworzyć raport wydajności testu obciążenia przy użyciu programu Microsoft Word](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

Raport może służyć do współdzielenia danych wydajności z udziałowcami i przekazywania informacji o tym, czy ogólna wydajność i kondycja systemu jest lepsza i gorsza.

Definicje raportów są przechowywane w bazie danych testu obciążenia. Gdy raport jest zapisywany, definicja raportu jest zapisywana w bazie danych i może zostać ponownie użyta później.

Skoroszyt programu Excel można również udostępnić uczestnikom projektu, tak aby uczestnicy projektu nie musieli łączyć się z bazą danych, aby wyświetlić raport.

> [!NOTE]
> Skoroszyt programu Excel można udostępnić. jednak tylko użytkownicy, którzy mają program Visual Studio zainstalowany na swojej maszynie, będą mogli modyfikować dowolne arkusze kalkulacyjne. Inni użytkownicy nie będą widzieć opcji **raport o teście obciążenia** na Wstążce **pakietu Office** , ale będą mogli wyświetlać skoroszyt.

Na poniższej ilustracji przedstawiono przykładowy raport, który zawiera korelację między szybkością odrzucania transakcji (koszyka aktualizacji) a wygenerowaniem licznika (% procesor). Wskazuje to na potencjalny problem w kodzie aplikacji, a nie w bazie danych lub sieci, a także jest dobrym kandydatem do diagnozowania przy użyciu profilera ASP.NET.

![Potencjalny problem w kodzie aplikacji](../test/media/lt_excel.png)

Raporty programu Excel można generować w **analizatorze testu obciążenia**, korzystając z przycisku **Utwórz raport programu Excel** na pasku narzędzi lub z programu Excel przy użyciu opcji Raport z **testu obciążenia** na karcie **test obciążenia** wstążki **pakietu Office** .

> [!NOTE]
> W przypadku dodania komentarzy do testu obciążenia pojawiają się one w raporcie programu Excel.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Aby wygenerować raporty porównania testów obciążenia za pomocą programu Excel

1. Przed wygenerowaniem raportu należy najpierw uruchomić test obciążenia.

2. Raporty dotyczące testów obciążenia programu Excel można tworzyć na dwa sposoby:

   - Po zakończeniu testu obciążenia na stronie **ładowanie wyniki testów** wybierz przycisk **Utwórz raport programu Excel** na pasku narzędzi.

      > [!NOTE]
      > Jeśli przycisk **Utwórz raport programu Excel** jest wyłączony na pasku narzędzi **podglądu wydajności sieci Web wyniki testów** , może być konieczne uruchomienie programu Microsoft Excel jeden raz przed jego włączeniem. Po zainstalowaniu Visual Studio Enterprise dodatek testu obciążenia Visual Studio Enterprise zostanie skopiowany na komputer dla programu Microsoft Excel; Jednak aby zakończyć proces instalacji dodatku, należy uruchomić program Microsoft Excel.

      Program Microsoft Excel zostanie otwarty z **kreatorem Generuj raport z testu obciążenia**.

   **ORAZ**

   1. Otwórz program Microsoft Excel, wybierz kartę **test obciążenia** na Wstążce **pakietu Office** , a następnie wybierz pozycję **Raport z testu obciążenia**.

       Zostanie wyświetlony **Kreator Generuj raport z testu obciążenia** .

   2. Na stronie **Wybierz bazę danych zawierającą testy obciążenia** w obszarze **Nazwa serwera**wpisz nazwę serwera zawierającego wyniki testu obciążenia.

   3. Z listy rozwijanej **Nazwa bazy danych** wybierz bazę danych zawierającą wyniki testu obciążenia.

3. Na stronie **jak chcesz wygenerować raport** upewnij się, że jest zaznaczona opcja **Utwórz raport** , a następnie wybierz przycisk **dalej**.

4. Na stronie **jaki typ raportu chcesz wygenerować** upewnij się, że wybrano opcję **Uruchom porównanie** , a następnie wybierz przycisk **dalej**.

5. Na stronie **Wprowadź szczegóły raportu testu obciążenia** wpisz nazwę raportu w polu **Nazwa raportu**.

6. Wybierz test obciążenia, dla którego chcesz wygenerować raport, a następnie wybierz przycisk **dalej**.

7. Na stronie **Wybierz przebiegi dla raportu** w obszarze **Wybierz co najmniej jeden przebieg do dodania do raportu**wybierz dwa wyniki testów obciążenia, które chcesz porównać w raporcie, i wybierz przycisk **dalej**.

   > [!NOTE]
   > Raport porównawczy można generować tylko dla dwóch wyników testu obciążenia. Jeśli wybierzesz jeden wynik testu obciążenia lub więcej niż dwa wyniki testów obciążenia, zostanie wyświetlony komunikat ostrzegawczy.

8. Na stronie **Wybierz liczniki dla raportu** w obszarze **Wybierz co najmniej jeden licznik, który ma zostać dodany do raportu można dodać** listę liczników, aby dostosować raport. Wybierz liczniki, które chcesz porównać z dwóch wybranych przebiegów testowych w raporcie, a następnie wybierz przycisk **Zakończ**.

9. Raport skoroszytu programu Excel jest generowany przy użyciu następujących kart arkusza kalkulacyjnego:

   - **Spis treści** — wyświetla nazwę raportu testu obciążenia i zawiera spis treści z linkami do różnych kart w raporcie.

   - **Uruchomienia —** Zawiera szczegółowe informacje na temat tego, które dwa przebiegi są porównywane w raporcie.

   - **Porównanie testów —** Zawiera szczegóły wykresu słupkowego dotyczące regresji wydajności i ulepszeń między dwoma różnymi przebiegami.

   - **Porównanie stron —** Zawiera wykres słupkowy i procentowe dane porównania wydajności między dwoma przebiegami na różnych stronach w przebiegach testów.

   - **Porównanie maszyn —** Zawiera dane porównania między dwoma przebiegami zależnymi od użytych maszyn.

   - **Porównanie błędów —** Porównuje typy błędów napotkane między dwoma przebiegami i liczbą wystąpień.

     > [!TIP]
     > W celu uzyskania lepszych raportów niektóre właściwości są dostępne w testach obciążenia i testach wydajności sieci Web, które umożliwiają bogatsze raporty. Żądanie strony ma dwie właściwości, które są prezentowane w raportach: cel i nazwa raportowania. Czasy odpowiedzi stron będą raportowane względem celu, a zamiast adresu URL w raportach zostanie użyta nazwa raportowania. W obszarze Ustawienia przebiegu testu obciążenia w obszarze Zarządzanie zbiorami liczników Właściwość Tagi komputera jest wyświetlana na liście nazwy maszyn raportu. Jest to bardzo przydatne w przypadku opisywania roli konkretnego komputera w raporcie.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Aby wygenerować raporty trendów testu obciążenia za pomocą programu Excel

1. Przed wygenerowaniem raportu, należy uruchomić test obciążenia.

2. Raporty dotyczące testów obciążenia programu Excel można tworzyć na dwa sposoby:

   - Po zakończeniu testu obciążenia na stronie **ładowanie wyniki testów** wybierz przycisk **Utwórz raport programu Excel** na pasku narzędzi.

      > [!NOTE]
      > Jeśli przycisk **Utwórz raport programu Excel** jest wyłączony na pasku narzędzi **podglądu wydajności sieci Web wyniki testów** , może być konieczne uruchomienie programu Microsoft Excel jeden raz przed jego włączeniem. Po zainstalowaniu Visual Studio Enterprise dodatek testu obciążenia Visual Studio Enterprise zostanie skopiowany na komputer dla programu Microsoft Excel; Jednak aby zakończyć proces instalacji dodatku, należy uruchomić program Microsoft Excel.

      Program Microsoft Excel zostanie otwarty z **kreatorem Generuj raport z testu obciążenia**.

   **ORAZ**

   1. Otwórz program Microsoft Excel, wybierz kartę **test obciążenia** na Wstążce **pakietu Office** , a następnie wybierz pozycję **Raport z testu obciążenia**.

       Zostanie wyświetlony **Kreator Generuj raport z testu obciążenia** .

   2. Na stronie **Wybierz bazę danych zawierającą testy obciążenia** w obszarze **Nazwa serwera**wpisz nazwę serwera zawierającego wyniki testu obciążenia.

   3. Z listy rozwijanej **Nazwa bazy danych** wybierz bazę danych zawierającą wyniki testu obciążenia.

3. Na stronie **jak chcesz wygenerować raport** upewnij się, że jest zaznaczona opcja **Utwórz raport** , a następnie wybierz przycisk **dalej**.

4. Na stronie **jaki typ raportu chcesz wygenerować** upewnij się, że jest zaznaczona opcja **trend** i wybierz polecenie **dalej**.

5. Na stronie **Wprowadź szczegóły raportu testu obciążenia** wpisz nazwę raportu w polu **Nazwa raportu**.

6. Wybierz test obciążenia, dla którego chcesz wygenerować raport, a następnie wybierz przycisk **dalej**.

7. Na stronie **Wybierz przebiegi dla raportu** w obszarze **Wybierz co najmniej jeden przebieg do dodania do raportu**wybierz wyniki testów obciążenia, które chcesz porównać w raporcie, i wybierz przycisk **dalej**.

8. Na stronie **Wybierz liczniki dla raportu** w obszarze **Wybierz co najmniej jeden licznik, który ma zostać dodany do raportu**, można rozwinąć listę liczników, aby dostosować raport. Wybierz liczniki, które chcesz porównać na potrzeby analizy trendów, a następnie wybierz pozycję **Zakończ**.

9. Raport jest generowany z spisem treści zawierającym linki do różnych kart skoroszytów programu Excel, które zostały wygenerowane w raporcie. Linki są oparte na licznikach wybranych dla raportu trendu. Na przykład jeśli pozostawiłeś liczniki domyślne wybrane w kroku 7, raport wygeneruje dane, które są prezentowane w oddzielnych kartach w programie Excel dla każdego licznika wymienionego w kroku 7. Dane generowane dla każdego licznika są prezentowane na wykresach w stylu trendu.

   > [!TIP]
   > W celu uzyskania lepszych raportów niektóre właściwości są dostępne w testach obciążenia i testach wydajności sieci Web, które umożliwiają bogatsze raporty. Żądanie strony ma dwie właściwości, które są prezentowane w raportach: cel i nazwa raportowania. Czasy odpowiedzi stron będą raportowane względem celu, a zamiast adresu URL w raportach zostanie użyta nazwa raportowania. W obszarze Ustawienia przebiegu testu obciążenia w obszarze Zarządzanie zbiorami liczników Właściwość Tagi komputera jest wyświetlana na liście nazwy maszyn raportu. Jest to bardzo przydatne w przypadku opisywania roli konkretnego komputera w raporcie.

## <a name="net-security"></a>Zabezpieczenia platformy .NET

Wyniki testów obciążenia i raporty zawierają potencjalnie poufne informacje, które mogą być używane do tworzenia ataku na komputer lub w sieci. Wyniki testów obciążenia i raporty zawierają nazwy komputerów i parametry połączenia. Należy pamiętać o tym, gdy udostępniasz raporty testów obciążenia innym osobom.

## <a name="see-also"></a>Zobacz też

- [Zgłoś wyniki testów obciążenia dla porównania testów lub analizy trendów](../test/compare-load-test-results.md)
