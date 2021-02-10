---
title: Przykładowe projekty języka R
description: Indeks kolekcji próbek, aby rozpocząć pracę z językiem R i programem Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 0ed322a03d056f72ac2246e96d3aaeefa8f557c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967023"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>R Tools for Visual Studio przykładowe projekty

Ta kolekcja przykładów pozwala rozpocząć pracę w języku R, R Tools for Visual Studio (RTVS) i Microsoft Machine Learning Server:

1. Pobierz [plik zip Samples](https://github.com/Microsoft/RTVS-docs/archive/master.zip) i wyodrębnij go do wybranego folderu.
1. Otwórz, `examples/Examples.sln` Aby wyświetlić dwa foldery w projekcie:

    - *Pierwsze spojrzenie na r* daje łagodne wprowadzenie do języka r.
    - *Pani i Machine Learning* zawiera przykłady użycia języka R i Microsoft Machine Learning Server do uczenia maszynowego.

## <a name="a-first-look-at-r"></a>Pierwsze spojrzenie na R

Ten przykład zawiera szczegółowe wprowadzenie do języka R poprzez obszerne komentarze w dwóch plikach źródłowych. Aby uzyskać najlepsze doświadczenia, umieść kursor w górnej części pliku, a następnie naciśnij klawisze CTRL + ENTER, aby wysłać kod w wierszu do okna **R Interactive** . (Wiersze instalujące pakiety mogą potrwać minutę lub dwa.)

- `1-Getting Started with R.R` obejmuje wiele podstaw języka R, w tym używanie pakietów, ładowanie i analizowanie danych oraz Wykreślanie.

    ![Przykładowe dane wyjściowe z 1-Wprowadzenie z przykładem R.R](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` wprowadza pakiet graficzny ggplot2 znany dla jego wizualnie atrakcyjnych wykresów i prostej składni. Ten przykład wizualizuje dane trzęsienia ziemi od Fidżi.

    ![Przykładowe dane wyjściowe z 2-Wprowadzenie do ggplot2. Przykład R](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Microsoft Machine Learning Server i Machine Learning

W tej kolekcji przykładów pokazano, jak za pomocą języka R tworzyć modele uczenia maszynowego i korzystać z [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

Podobnie jak w przypadku wszystkich przykładów, Otwórz plik, umieść kursor u góry, a następnie przejdź do wiersza kodu linia po **naciśnięciu klawisza Ctrl** + **Enter**. Pliki promocji w poszczególnych folderach zawierają również dodatkowe szczegóły.

- `Benchmarks` uruchamia wiele intensywnych, równoległych obliczeń liniowych algebry, aby pokazać zyski wydajności, które można wykonać za pomocą programu Microsoft R Open i biblioteki jądra matematycznej Intel (MKL). W przypadku symulowanych danych testy porównawcze dokładnie porównują obliczenia macierzy w jednym wątku.

    ![Przykładowy Wykres porównawczy](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` tworzy model prognozowania popytu dla wypożyczalni roweru na podstawie historycznego zestawu danych przy użyciu ML Server Microsoft.

- `Data_Exploration` zawiera trzy skrypty:

  - `Import Data from URL.R` pokazuje, jak załadować plik danych identyfikowany przez adres URL do języka R.
  - `Import Data from URL to xdf.R` pokazuje, jak załadować plik danych identyfikowany przez adres URL do firmy Microsoft ML Server jako XDF.
  - `Using ggplot2.R` to rozszerzenie `A First Look at R/2-Introduction to ggplot2.R` przykładu, oferując bardziej obszerny przewodnik po funkcjach ggplot2's, w tym interaktywne Wykreślanie 3W.

      ![Dane wyjściowe polecenia using ggplot2. Przykład R](media/samples-3d-interactive.png)

- `Datasets` zawiera trzy pliki *CSV* używane przez inne przykłady
- `Flight_Delays_Prediction_with_R` i `Flight_Delays_Prediction_with_MRS` pokazuje, jak przewidzieć opóźnienia lotu przy użyciu języka R, uczenia maszynowego i historyczne dane o wydajności i pogodzie.
- `Machine learning` zawiera trzy przykłady do uczenia się w celu przewidywania opóźnień lotów, cen mieszkaniowych i czynszów rowerowych. We wszystkich tych przykładach przedstawiono sposób działania programów R i Microsoft ML Server na rzeczywiste problemy. Pokazano również, jak używać kilku popularnych modeli uczenia maszynowego i wdrażać je jako usługę sieci Web platformy Azure przy użyciu obszaru roboczego [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/) .

- `R_MRO_MRS_Comparison` to porównanie sześć części, które pokazuje podobieństwa i różnice w języku R, Microsoft R Open i Microsoft ML Server z poleceniami, składnią, konstrukcjami i wydajnością.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Co to jest specjalna funkcja Microsoft R Open i Microsoft ML Server?

[Microsoft r Open](https://mran.revolutionanalytics.com/download/), dystrybucja w języku r firmy Microsoft jest różna od [Cran r](https://cran.r-project.org/) na dwa ważne sposoby:

1. [Lepsza wydajność obliczeń](https://mran.revolutionanalytics.com/rro/#intelmkl1) w przypadku korzystania z [bibliotek jądra matematycznych firmy Intel](https://software.intel.com/intel-mkl). Biblioteki są dostępne bezpłatnie do pobrania od firmy Microsoft do użycia z programem Microsoft R Open.

1. [Odtwarzalny zestaw narzędzi języka r](https://mran.revolutionanalytics.com/rro/#reproducibility) zapewnia, że biblioteki użyte do skompilowania programu r są zawsze dostępne dla innych osób, które chcą odtworzyć swoją służbę.

[Microsoft ml Server (MLS)](/machine-learning-server/what-is-machine-learning-server) to rozszerzenie języka R, które pozwala na obsługę większej ilości danych i szybsze obsłudze. Zapewnia to w języku R dwie zaawansowane możliwości:

1. Większe zestawy danych bez ograniczeń pamięci RAM. ML Server może przetwarzać dane spoza pamięci z różnych źródeł, w tym klastrów Hadoop, baz danych i magazynów danych.

1. Równoległe przetwarzanie wielordzeniowe. MLS może efektywnie dystrybuować obliczenia we wszystkich dostępnych zasobach obliczeniowych. Na osobistej stacji roboczej lub zdalnym klastrze MLS szybciej otrzymuje odpowiedź.

Poniższe porównanie pokazuje, że MLS i MRO z MKL mają znacznie lepszą wydajność obliczeniową związaną z pewnymi obliczeniami macierzy niż R i MRO bez MKL. W tym obliczaniu są używane symulowane dane:

![Porównanie MLS i MRO z MKL do R i MRO bez MKL](media/samples-speed-comparison.png)

Aby poznać techniczne porównanie R z MRO i MLS, zapoznaj się z informacjami na temat [szczegółowej dyskusji](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) na temat programu Lixun Zhang w temacie.

Poniższy rysunek porównał czas w sekundach używany podczas tworzenia modeli regresji logistycznej w celu przewidywania opóźnień lotów dłuższych niż 15 minut.  Czas, który upłynął w CRAN R, rośnie znacznie podczas zwiększania niewielkiej liczby wierszy, podczas gdy MLS zwiększa się tylko o około dwa razy. Aby uzyskać szczegółowe informacje na temat tego testu porównawczego, zapoznaj się z wynikami *testów porównawczych/rxGlm_benchmark. Przykład R* .

![wzorzec rxGlm](media/samples-rxGLM-benchmark.png)
