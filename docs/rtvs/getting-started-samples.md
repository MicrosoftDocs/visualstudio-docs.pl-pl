---
title: R przykładowych projektów
description: Indeks kolekcji przykładów, aby rozpocząć pracę z języków R i programu Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: adcc5ce422cdd06e641408b3506fb751a4c730d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62950476"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Narzędzia języka R dla programu Visual Studio przykładowych projektów

Ta kolekcja przykładów ułatwia rozpoczęcie pracy na R, R Tools for Visual Studio (RTVS), a serwer Microsoft Machine Learning:

1. Pobierz [plik zip przykłady](https://github.com/Microsoft/RTVS-docs/archive/master.zip) i Wyodrębnij zawartość do wybranego folderu.
1. Otwórz `examples/Examples.sln` się dwa foldery w projekcie:

    - *Pierwsze spojrzenie na R* zawiera wprowadzenie delikatnie nowym do języka R.
    - *PANI i usługi Machine Learning* zawiera przykłady dotyczące używania języka R i serwer Microsoft Machine Learning do uczenia maszynowego.

## <a name="a-first-look-at-r"></a>Pierwsze spojrzenie na R

W tym przykładzie zapewnia szczegółowe wprowadzenie do języka R za pośrednictwem liczne komentarze w dwóch plikach źródłowych. Najlepsze środowisko, umieść kursor na początku pliku i naciśnij klawisze Ctrl + Enter, aby wysłać kod wiersza przez-znajdują się na **interaktywne R** okna. (Wiersze, które instalowanie pakietów może zająć minutę lub dwie do ukończenia).

- `1-Getting Started with R.R` obejmuje wiele podstawy języka R, w tym za pomocą pakietów, ładowania i analizowania danych i wykreślania.

    ![Przykładowe dane wyjściowe z uruchomiono wprowadzenie 1 R.R próbki](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` wprowadza pakietu grafiki ggplot2 znana jej atrakcyjność powierzchni i prostą składnię. W tym przykładzie wizualizuje dane Fidżi trzęsienie ziemi.

    ![Przykład danych wyjściowych z 2 — wprowadzenie do ggplot2. Przykładowy języka R](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Serwer Microsoft Machine Learning i usługi Machine Learning

Ta kolekcja przykładów przedstawia sposób użycia języka R, do tworzenia modeli uczenia maszynowego i korzystać z zalet [serwer Microsoft Machine Learning](/machine-learning-server/what-is-machine-learning-server).

Zgodnie z przykładami dla wszystkich, otwórz plik, umieść kursor na początku, a następnie przejść przez kod wiersz po wierszu za pomocą **Ctrl**+**Enter**. Pliki markdown w każdy folder zawierają również dodatkowe szczegóły.

- `Benchmarks` Uruchamia szereg mocy obliczeniowej, równoległe algebry liniowej obliczeń, aby wyświetlić wydajność uzyska, które są możliwe przy użyciu programu Microsoft R Open wraz z Intel matematyczne jądra biblioteki (MKL). Z symulowanymi danymi wzorców specjalnie Porównaj macierzach w jednym wątku, a dwa.

    ![Przykład testu porównawczego wykres](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` Tworzy model prognozowania popytu wypożyczenia rowerów, na podstawie zestawu danych historycznych, przy użyciu Microsoft ML Server.

- `Data_Exploration` zawiera trzy skrypty:

  - `Import Data from URL.R` Pokazuje, jak załadować plik danych identyfikowane przez adres URL do języka R.
  - `Import Data from URL to xdf.R` Pokazuje, jak załadować plik danych identyfikowane przez adres URL do Microsoft ML Server jako xdf.
  - `Using ggplot2.R` to rozszerzenie `A First Look at R/2-Introduction to ggplot2.R` próbki, zapewniając bardziej rozległe Przewodnik po przykładzie funkcje ggplot2 firmy, w tym interaktywne wykreślania 3D.

      ![Dane wyjściowe przy użyciu ggplot2. Przykład języka R](media/samples-3d-interactive.png)

- `Datasets` zawiera trzy *CSV* pliki używane przez inne przykłady
- `Flight_Delays_Prediction_with_R` i `Flight_Delays_Prediction_with_MRS` pokazuje, jak do prognozowania opóźnień lotów przy użyciu języka R, usługi machine learning i historycznych punktualności lotów oraz danych o pogodzie.
- `Machine learning` zawiera trzy próbki do nauki do prognozowania opóźnień lotów, ceny obudowy i wypożyczenia rowerów. Razem te przykłady pokazują zastosowanie języków R i Microsoft ML Server do rzeczywistych problemów. Mogą również pokazują, jak używać modele uczenia maszynowego popularne w kilku i wdrażanie ich jako usługi sieci Web platformy Azure przy użyciu [usługi Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/) obszaru roboczego.

- `R_MRO_MRS_Comparison` to porównanie sześcioczęściowej, który pokazuje podobieństw i różnic języka R, Microsoft R Open i Microsoft ML Server za pomocą poleceń, składni, konstrukcje i wydajności.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Co to jest specjalne dotyczące programu Microsoft R Open wraz z Microsoft ML Server?

[Microsoft R Open](https://aka.ms/rtvs-r-open), dystrybucja firmy Microsoft języka r, różni się od [CRAN języka R](https://cran.r-project.org/) na dwa istotne sposoby:

1. [Lepsza wydajność obliczeń](https://mran.revolutionanalytics.com/rro/#intelmkl1) gdy jest używane z [biblioteki jądra matematyczne Intel](https://software.intel.com/intel-mkl). Biblioteki są dostępne bezpłatnie do pobrania firmy Microsoft do użytku z programem Microsoft R Open.

1. [Zestaw narzędzi do odtworzenia R](https://mran.revolutionanalytics.com/rro/#reproducibility) gwarantuje, że bibliotek używanych do tworzenia programu R są zawsze dostępne dla innych użytkowników, których chcesz odtworzyć swoją pracę.

[Microsoft ML Server (MLS)](/machine-learning-server/what-is-machine-learning-server) jest rozszerzeniem języka R, umożliwiające obsługę większej ilości danych i szybciej go obsłużyć. Przekazuje R dwa zaawansowane możliwości:

1. Większe zestawy danych bez ograniczeń pamięci RAM. ML Server może przetwarzać dane braku pamięci z różnych źródeł, w tym klastrów Hadoop, baz danych i magazyny danych.

1. Przetwarzanie równoległe, wielordzeniowych. MLS mogą efektywnie rozproszenia obliczeń wszystkich zasobów obliczeniowych jest dostępna. Na osobistych stacji roboczej lub w klastrze zdalnym MLS pobiera odpowiedź szybciej.

Poniższe porównanie pokazuje, że MLS oraz MRO z MKL ma znacznie lepszą wydajność obliczeń związanych z niektórych obliczeń macierzy niż języków R i MRO bez MKL. W tych obliczeniach są używane symulowane dane:

![Porównanie MLS i MRO z MKL r i MRO bez MKL](media/samples-speed-comparison.png)

Techniczne porównanie R MRO i MLS, zapoznaj się z [Lixun Zhang szczegółowe omówienie](http://htmlpreview.github.io/? https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) tematu.

Poniższa ilustracja następnie porównuje czas w sekundach stosowanego w budynku, modele regresji logistycznej do prognozowania opóźnień lotów więcej niż 15 minut.  Upłynęło czasu używany w języku R z sieci CRAN gwałtowny wzrost podczas zwiększenie niewielką liczbę wierszy, podczas gdy MLS zwiększa tylko przez około dwa razy. Aby uzyskać szczegółowe informacje o tym testów porównawczych, zapoznaj się *testy porównawcze/rxGlm_benchmark. R* przykład.

![Test porównawczy rxGlm](media/samples-rxGLM-benchmark.png)
