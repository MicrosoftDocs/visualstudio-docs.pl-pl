---
title: Przykładowe projekty R
description: Indeks kolekcji przykładów, aby rozpocząć pracę z języka R i Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: ef3316d929b00203815918a656568f75571e954e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75843821"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Narzędzia języka R dla przykładowych projektów programu Visual Studio

Ta kolekcja przykładów rozpoczyna pracę na narzędziach R, R Tools for Visual Studio (RTVS) i microsoft machine learning Server:

1. Pobierz [przykładowy plik zip](https://github.com/Microsoft/RTVS-docs/archive/master.zip) i wyodrębnij go do wybranego folderu.
1. Otwórz, `examples/Examples.sln` aby wyświetlić dwa foldery w projekcie:

    - *Pierwsze spojrzenie na R* daje delikatne wprowadzenie dla początkujących do R.
    - *Mrs i machine learning* podaje przykłady, jak używać R i Microsoft Machine Learning Server do uczenia maszynowego.

## <a name="a-first-look-at-r"></a>Pierwsze spojrzenie na R

Ten przykład zawiera szczegółowe wprowadzenie do R poprzez obszerne komentarze w dwóch plikach źródłowych. Aby uzyskać najlepsze wrażenia, umieść kursor u góry pliku i naciśnij klawisze Ctrl+Enter, aby wysłać wiersz kodu według kłamstwa do okna **R Interactive.** (Wiersze, które instalują pakiety, mogą potrwać minutę lub dwie).

- `1-Getting Started with R.R`obejmuje wiele r podstaw, w tym przy użyciu pakietów, ładowania i analizowania danych i kreślenia.

    ![Przykładowe dane wyjściowe z przykładu 1-Wprowadzenie z R.R](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R`wprowadza pakiet graficzny ggplot2 znany z atrakcyjnych wizualnie działek i prostej składni. W tym przykładzie wizualizuje dane trzęsienie ziemi z Fidżi.

    ![Przykładowy wynik z 2-Wprowadzenie do ggplot2. Próbka R](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Serwer uczenia maszynowego firmy Microsoft i uczenie maszynowe

W tej kolekcji przykładów pokazano, jak używać języka R do tworzenia modeli uczenia maszynowego i korzystania z [programu Microsoft Machine Learning Server.](/machine-learning-server/what-is-machine-learning-server)

Podobnie jak w przypadku wszystkich przykładów, otwórz plik, umieść kursor u góry, a następnie krok po wierszu kodu za pomocą **klawisza Ctrl**+**Enter**. Pliki znaczników w każdym folderze zawierają również dodatkowe szczegóły.

- `Benchmarks`uruchamia szereg intensywnych, równoległych obliczeń algebry liniowej, aby pokazać wzrost wydajności, który jest możliwy dzięki zastosowaniu programu Microsoft R Open i biblioteki jądra matematycznego Intel (MKL). W symulowanych danych wskaźniki porównawcze porównują obliczenia macierzy w jednym wątku z dwoma.

    ![Przykładowa wykres odniesienia](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS`tworzy model przewidywania popytu dla wypożyczeń rowerów na podstawie historycznego zestawu danych przy użyciu programu Microsoft ML Server.

- `Data_Exploration`zawiera trzy skrypty:

  - `Import Data from URL.R`pokazuje, jak załadować plik danych zidentyfikowanych przez adres URL do R.
  - `Import Data from URL to xdf.R`pokazuje, jak załadować plik danych zidentyfikowanych przez adres URL do serwera Microsoft ML Server jako xdf.
  - `Using ggplot2.R`jest rozszerzeniem `A First Look at R/2-Introduction to ggplot2.R` próbki, dając szersze zwiedzanie funkcji ggplot2, w tym interaktywne kreślenie 3D.

      ![Wyjście za pomocą ggplot2. Przykład R](media/samples-3d-interactive.png)

- `Datasets`zawiera trzy pliki *csv* używane przez inne przykłady
- `Flight_Delays_Prediction_with_R`i `Flight_Delays_Prediction_with_MRS` pokazuje, jak przewidzieć opóźnienia lotów przy użyciu języka R, uczenia maszynowego oraz historycznych danych dotyczących wydajności i pogody na czas.
- `Machine learning`zawiera trzy próbki do nauki przewidywania opóźnień lotów, cen mieszkań i wypożyczalni rowerów. Razem te przykłady pokazują zastosowanie R i Microsoft ML Server do rzeczywistych problemów. Pokazują one również, jak używać kilku popularnych modeli uczenia maszynowego i wdrożyć je jako usługę azure web przy użyciu obszaru roboczego [usługi Azure Machine Learning.](https://azure.microsoft.com/services/machine-learning/)

- `R_MRO_MRS_Comparison`to sześcioczęściowe porównanie, które pokazuje podobieństwa i różnice R, Microsoft R Open i Microsoft ML Server z poleceniami, składnią, konstrukcjami i wydajnością.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Co jest wyjątkowego w programach Microsoft R Open i Microsoft ML Server?

[Microsoft R Open](https://mran.revolutionanalytics.com/download/), dystrybucja R firmy Microsoft, różni się od [CRAN R](https://cran.r-project.org/) na dwa ważne sposoby:

1. [Lepsza wydajność obliczeń](https://mran.revolutionanalytics.com/rro/#intelmkl1) w przypadku korzystania z [bibliotek jądra matematycznego Intel](https://software.intel.com/intel-mkl). Biblioteki są dostępne do bezpłatnego pobrania od firmy Microsoft do użytku z programem Microsoft R Open.

1. [Powtarzalny zestaw narzędzi R toolkit](https://mran.revolutionanalytics.com/rro/#reproducibility) zapewnia, że biblioteki używane do tworzenia programu R są zawsze dostępne dla innych, którzy chcą odtworzyć swoją pracę.

[Microsoft ML Server (MLS)](/machine-learning-server/what-is-machine-learning-server) to rozszerzenie R, które pozwala na obsługę większej ilości danych i szybsze ich obsługę. Daje to R dwie potężne możliwości:

1. Większe zestawy danych bez ograniczeń pamięci RAM. Ml Server może przetwarzać dane poza pamięcią z różnych źródeł, w tym klastrów Hadoop, baz danych i magazynów danych.

1. Przetwarzanie równoległe, wielordzeniowe. Mls może skutecznie dystrybuować obliczenia we wszystkich dostępnych zasobach obliczeniowych. Na osobistej stacji roboczej lub klastrze zdalnym mls szybciej otrzymuje odpowiedź.

Poniższe porównanie pokazuje, że MLS i MRO z MKL mają znacznie lepszą wydajność obliczeniową związaną z niektórymi obliczeniami macierzy niż R i MRO bez MKL. Symulowane dane są używane w tych obliczeniach:

![Porównanie MLS i MRO z MKL do R i MRO bez MKL](media/samples-speed-comparison.png)

Aby uzyskać techniczne porównanie R z MRO i MLS, sprawdź [szczegółową dyskusję Lixun Zhang](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) na ten temat.

Na poniższym rysunku porównuje następnie czas, jaki upłynął w sekundach używanych w tworzeniu modeli regresji logistycznej w celu przewidywania opóźnień lotu większych niż 15 minut.  Czas, jaki upłynął w CRAN R, znacznie wzrasta, gdy zwiększa się niewielka liczba rzędów, podczas gdy MLS zwiększa się tylko około dwa razy. Aby uzyskać szczegółowe informacje na temat tego wskaźnika, zapoznaj się z *benchmarkami/rxGlm_benchmark. Przykład R.*

![Benchmark rxGlm](media/samples-rxGLM-benchmark.png)
