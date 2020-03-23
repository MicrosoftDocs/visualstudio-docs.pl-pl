---
title: Obciążenie do nauki o danych i aplikacji analitycznych
description: To obciążenie programu Visual Studio łączy Python, F#, i ich odpowiednich dystrybucji środowiska uruchomieniowego, w tym Anaconda. (Język R jest również uwzględniony tylko w programie Visual Studio 2017).
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 44906d70be05891fe52096adec2f61f2261b5db5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "70154880"
---
# <a name="install-data-science-support-in-visual-studio"></a>Instalowanie obsługi nauki o danych w programie Visual Studio

Obciążenie data science i aplikacje analityczne, które można wybrać i zainstalować za pośrednictwem instalatora programu Visual Studio, łączy w siebie kilka języków i ich odpowiednich dystrybucji środowiska uruchomieniowego:

::: moniker range="vs-2017"
- [Python i Anakonda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# z platformą .NET](/dotnet/fsharp/)
- [R i Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [F# z platformą .NET](/dotnet/fsharp/)
::: moniker-end

![Obciążenie aplikacji do nauki i analizy danych w instalatorze programu Visual Studio](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python i R to dwa podstawowe języki skryptów używane do nauki o danych. Oba języki są łatwe do nauczenia i są obsługiwane przez bogaty ekosystem pakietów. Pakiety te dotyczą szerokiego zakresu scenariuszy, takich jak pozyskiwanie danych, czyszczenie, szkolenie modelu, wdrażanie i drukowanie. F# jest również zaawansowanym językiem .NET, który nadaje się do różnych zadań przetwarzania danych.
::: moniker-end

::: moniker range="vs-2019"
Python jest podstawowym językiem skryptów używanym do nauki o danych. Python jest łatwy do nauczenia się i jest obsługiwany przez bogaty ekosystem pakietów. Pakiety te dotyczą szerokiego zakresu scenariuszy, takich jak pozyskiwanie danych, czyszczenie, szkolenie modelu, wdrażanie i drukowanie. F# jest również zaawansowanym językiem .NET, który nadaje się do różnych zadań przetwarzania danych. (For the R language we recommend [Azure Notebooks](https://notebooks.azure.com).)
::: moniker-end

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu programu Visual Studio z języka R, Python i F #](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Opcje obciążenia

Domyślnie obciążenie instaluje następujące opcje, które można zmodyfikować w sekcji podsumowania dla obciążenia w instalatorze programu Visual Studio:

::: moniker range="vs-2019"
- Obsługa języka pulpitu F#
- Python:
  - Obsługa języka Języka Python
  - Pomoc techniczna języka Python
::: moniker-end

::: moniker range="vs-2017"
- Obsługa języka Języka F#
- Python:
  - Obsługa języka Języka Python
  - [Anaconda3 64-bitowy](https://www.continuum.io), dystrybucja Pythona, która zawiera obszerne biblioteki do nauki o danych i interpretera Języka Python.
  - Pomoc techniczna języka Python
  - Obsługa szablonów cookiecutter
- R:
  - Obsługa języka R
  - Obsługa środowiska uruchomieniowego dla narzędzi programistycznych R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (w pełni kompatybilny, obsługiwany przez społeczność interpreter R firmy Microsoft z bibliotekami ScaleR w celu szybszego obliczania w pojedynczych węzłach lub klastrach. Można również użyć dowolnego R z [CRAN](https://cran.r-project.org/).)
::: moniker-end

## <a name="sql-server-integration"></a>Integracja programu SQL Server

::: moniker range="vs-2017"
SQL Server obsługuje przy użyciu python i R do zaawansowanej analizy bezpośrednio wewnątrz programu SQL Server. Obsługa języka R jest dołączona do programu SQL Server 2016 i nowszych; Obsługa języka Python jest dostępna w programie SQL Server 2017 CTP 2.0 lub nowszym.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server obsługuje przy użyciu języka Python do zaawansowanej analizy bezpośrednio wewnątrz programu SQL Server. Obsługa języka Python jest dostępna w programie SQL Server 2017 CTP 2.0 lub nowszym.
::: moniker-end

Możesz korzystać z następujących korzyści, uruchamiając kod, w którym twoje dane już żyją:

- **Eliminacja przenoszenia danych:** Zamiast przenosić dane z bazy danych do aplikacji lub modelu, można tworzyć aplikacje w bazie danych. Ta funkcja eliminuje bariery bezpieczeństwa, zgodności, zarządzania, integralności i wiele podobnych problemów związanych z przenoszeniem ogromnej ilości danych. Można również używać zestawów danych, które nie mogą zmieścić się w pamięci komputera klienckiego.

- **Łatwe wdrożenie:** Po przygotowaniu modelu wdrożenie go w trybie produkcyjnym jest prostą kwestią osadzania go w skrypcie T-SQL. Każda aplikacja klienta SQL napisane w dowolnym języku można następnie skorzystać z modeli i analizy za pośrednictwem wywołania procedury składowanej. Nie są konieczne żadne specyficzne integracje językowe.

- **Wydajność i skala klasy korporacyjnej:** Można użyć zaawansowanych funkcji programu SQL Server, takich jak indeksy magazynu tabeli i kolumn w pamięci z skalowalnymi interfejsami API o wysokiej wydajności w pakietach RevoScale. Eliminacja przenoszenia danych oznacza również, że można uniknąć ograniczeń pamięci klienta w miarę wzrostu danych lub chcesz zwiększyć wydajność aplikacji.

- **Rozbudowa:** Możesz zainstalować i uruchomić dowolny z najnowszych pakietów open source w programie SQL Server, aby tworzyć aplikacje głębokiego uczenia i ai na ogromnych ilościach danych w programie SQL Server. Instalowanie pakietu w programie SQL Server jest tak proste, jak zainstalowanie pakietu na komputerze lokalnym.

- **Szeroka dostępność bez dodatkowych kosztów:** Integracje językowe są dostępne we wszystkich wersjach programu SQL Server 2017 i nowszych, w tym w wersji Express.

Aby w pełni korzystać z integracji programu SQL Server, użyj instalatora programu Visual Studio, aby zainstalować obciążenie **magazynowania i przetwarzania danych** za pomocą opcji **Narzędzia danych programu SQL Server.** Ta ostatnia opcja umożliwia SQL IntelliSense, wyróżnianie składni i wdrażania.

![Obciążenie związane z przechowywaniem i przetwarzaniem danych](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Opcje przechowywania i przetwarzania danych](media/workload/data-storage-workload-options.png)

Więcej informacji:

::: moniker range="vs-2017"
- [Praca z programami SQL Server i R](../rtvs/integrating-sql-server-with-r.md)
- [Zaawansowane analizy w bazie danych z funkcją R w programie SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [Python w programie SQL Server 2017: ulepszone uczenie maszynowe w bazie danych (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Dodatkowe usługi i SDK

Oprócz tego, co znajduje się bezpośrednio w obciążeniu aplikacji do nauki o danych i analizy, usługa Azure Notebooks i zestaw SDK platformy Azure dla języka Python są również przydatne w naukach o danych.

Zestaw Azure SDK dla języka Python ułatwia korzystanie z usług platformy Microsoft Azure i zarządzanie nimi z aplikacji z systemem Windows, Mac i Linux. Aby uzyskać więcej informacji, zobacz [Zestaw SDK platformy Azure dla języka Python](/azure/python/).

Notesy platformy Azure (obecnie w wersji zapoznawczej) zapewniają bezpłatny dostęp online do notesów Jupyter działających w chmurze na platformie Microsoft Azure. Usługa zawiera przykładowe notesy w pythonie, języku R i F#, aby rozpocząć pracę. Odwiedź [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu notesów platformy Azure z przykładem Wprowadzenie do r](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
