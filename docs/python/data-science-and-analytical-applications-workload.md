---
title: Obciążenie aplikacji do analizy i przetwarzania danych
description: To obciążenie programu Visual Studio łączy środowisko Python F#oraz odpowiednie dystrybucje środowiska uruchomieniowego, w tym Anaconda. (R jest również uwzględniony tylko w programie Visual Studio 2017).
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 44906d70be05891fe52096adec2f61f2261b5db5
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154880"
---
# <a name="install-data-science-support-in-visual-studio"></a>Instalowanie pomocy technicznej dotyczącej analizy danych w programie Visual Studio

Obciążenie aplikacji analizy i przetwarzania danych, które można wybrać i zainstalować za pomocą Instalatora programu Visual Studio, zawiera kilka języków i ich dystrybucje w czasie wykonywania:

::: moniker range="vs-2017"
- [Python i Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F#z .NET Framework](/dotnet/fsharp/)
- [R i Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [F#z .NET Framework](/dotnet/fsharp/)
::: moniker-end

![Obciążenie aplikacji do analizy i przetwarzania danych w Instalatorze programu Visual Studio](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Języki Python i R są dwoma podstawowymi językami skryptów używanymi do analizy danych. Oba języki są łatwe w nauce i są obsługiwane przez bogaty ekosystem pakietów. Pakiety te obejmują szeroką gamę scenariuszy, takich jak pozyskiwanie danych, czyszczenie, uczenie modeli, wdrażanie i Kreślenie. F#jest również zaawansowanym i funkcjonalnym językiem .NET, który jest przeznaczony do różnorodnych zadań przetwarzania danych.
::: moniker-end

::: moniker range="vs-2019"
Python to podstawowy język skryptów używany do nauki danych. Język Python jest łatwy do uczenia i jest obsługiwany przez bogaty ekosystem pakietów. Pakiety te obejmują szeroką gamę scenariuszy, takich jak pozyskiwanie danych, czyszczenie, uczenie modeli, wdrażanie i Kreślenie. F#jest również zaawansowanym i funkcjonalnym językiem .NET, który jest przeznaczony do różnorodnych zadań przetwarzania danych. (Dla języka R zalecamy [Azure Notebooks](https://notebooks.azure.com).)
::: moniker-end

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu programu Visual Studio z językiem R, Python iF#](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Opcje obciążenia

Domyślnie obciążenie instaluje następujące opcje, które można zmodyfikować w sekcji podsumowania obciążenia w Instalatorze programu Visual Studio:

::: moniker range="vs-2019"
- F#Obsługa pulpitu języka
- Python:
  - Obsługa języka Python
  - Obsługa sieci web w języku Python
::: moniker-end

::: moniker range="vs-2017"
- F#Obsługa języków
- Python:
  - Obsługa języka Python
  - [Anaconda3 64-bit](https://www.continuum.io), dystrybucji języka Python, który zawiera rozbudowane biblioteki analizy danych i interpreter języka Python.
  - Obsługa sieci web w języku Python
  - Obsługa szablonów Cookiecutter
- ®
  - Obsługa języka R
  - Obsługa środowiska uruchomieniowego dla narzędzi programistycznych języka R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (W pełni zgodne, obsługiwane przez społeczność interpreter R z bibliotekami skalowania umożliwiającą szybsze Obliczanie na pojedynczych węzłach lub w klastrach. Możesz również użyć dowolnego języka R z [Cran](https://cran.r-project.org/).)
::: moniker-end

## <a name="sql-server-integration"></a>Integracja programu SQL Server

::: moniker range="vs-2017"
SQL Server obsługuje używanie języków Python i R do zaawansowanej analizy bezpośrednio w programie SQL Server. Obsługa języka R jest dołączona do SQL Server 2016 i nowszych. Obsługa języka Python jest dostępna w SQL Server 2017 CTP 2,0 i nowszych.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server obsługuje używanie języka Python do zaawansowanej analizy bezpośrednio w programie SQL Server. Obsługa języka Python jest dostępna w SQL Server 2017 CTP 2,0 i nowszych.
::: moniker-end

Korzystając z kodu, na którym już przebywa Twoje dane, możesz korzystać z następujących korzyści:

- **Eliminowanie przenoszenia danych**: Zamiast przenosić dane z bazy danych do aplikacji lub modelu, można tworzyć aplikacje w bazie danych programu. Ta funkcja eliminuje bariery związane z zabezpieczeniami, zgodnością, nadzorem, integralnością i hostem podobnych problemów związanych z przenoszeniem ogromnych ilości danych. Można również korzystać z zestawów danych, które nie mieszczą się w pamięci komputera klienckiego.

- **Łatwe wdrażanie**: Gdy model jest gotowy, wdrożenie go w środowisku produkcyjnym jest prostą kwestią osadzania go w skrypcie T-SQL. Wszystkie aplikacje klienckie SQL zapisane w dowolnym języku mogą następnie skorzystać z modeli i analizy za pomocą wywołania procedury przechowywanej. Nie są wymagane żadne konkretne integracje języka.

- **Wydajność i skala klasy korporacyjnej**: Można korzystać z zaawansowanych funkcji SQL Server, takich jak tabele w pamięci i indeksy magazynu kolumn z skalowalnymi interfejsami API o wysokiej wydajności w pakietach RevoScale. Eliminacja przenoszenia danych oznacza również, że można uniknąć ograniczeń pamięci klienta w miarę zwiększania się danych lub zwiększenia wydajności aplikacji.

- Rozbudowana rozszerzalność: Możesz zainstalować i uruchomić dowolne z najnowszych pakietów typu open source w SQL Server, aby tworzyć aplikacje do uczenia głębokiego i AI w przypadku ogromnych ilości danych w SQL Server. Instalowanie pakietu w SQL Server jest tak proste jak zainstalowanie pakietu na komputerze lokalnym.

- **Szeroka dostępność bez dodatkowych kosztów**: Integracje językowe są dostępne we wszystkich wersjach SQL Server 2017 i nowszych, w tym wersji Express.

Aby w pełni wykorzystać możliwości integracji z usługą SQL Server, użyj Instalatora programu Visual Studio w celu zainstalowania obciążenia **magazynu i przetwarzania danych** za pomocą opcji **SQL Server Data Tools** . Ta ostatnia opcja włącza funkcję SQL IntelliSense, wyróżnianie składni i wdrażanie.

![Obciążenie magazynowanie i przetwarzanie danych](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Opcje obciążenia magazynu i przetwarzania danych](media/workload/data-storage-workload-options.png)

Informacje dodatkowe:

::: moniker range="vs-2017"
- [Współpraca z SQL Server i R](../rtvs/integrating-sql-server-with-r.md)
- [Zaawansowana analiza w bazie danych przy użyciu języka R w SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [Python w SQL Server 2017: ulepszono Uczenie maszynowe w bazie danych (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Dodatkowe usługi i zestawy SDK

Oprócz tego, co znajduje się w obciążeniu aplikacji analizy i przetwarzania danych, usługa Azure Notebooks i zestaw Azure SDK dla języka Python również ułatwiają naukę danych.

Zestaw Azure SDK dla języka Python ułatwia korzystanie z usług Microsoft Azure i zarządzanie nimi z poziomu aplikacji działających w systemach Windows, Mac i Linux. Aby uzyskać więcej informacji, zobacz [zestaw Azure SDK dla języka Python](/azure/python/).

Azure Notebooks (obecnie w wersji zapoznawczej) oferuje bezpłatny dostęp online do notesów Jupyter działających w chmurze w Microsoft Azure. Usługa obejmuje przykładowe notesy w języku Python, R i F# , aby rozpocząć pracę. Odwiedź stronę [Notebooks.Azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu Azure Notebooks z wprowadzeniem do przykładu R](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
