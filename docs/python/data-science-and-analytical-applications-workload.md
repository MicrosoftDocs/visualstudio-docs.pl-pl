---
title: Obciążenie aplikacji analitycznych i naukowych opracowań danych
description: To obciążenie programu Visual Studio umożliwia połączenie ze sobą Python, F#i ich dystrybucji odpowiedniego środowiska uruchomieniowego, w tym Anaconda. (Języka R znajduje się również w programie Visual Studio 2017 jedynie.)
ms.date: 02/28/2019
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 44dfa13059e16338111bbeb2eb2f0bc6d6b44408
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57325331"
---
# <a name="install-data-science-support-in-visual-studio"></a>Nainstalovat podporu do nauki o danych w programie Visual Studio

Obciążenie aplikacji analitycznych i naukowych opracowań danych, który zaznaczyć i zainstalować za pomocą Instalatora programu Visual Studio, umożliwia połączenie ze sobą kilku języków i ich dystrybucji odpowiedniego środowiska uruchomieniowego:

::: moniker range="vs-2017"
- [Python i Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F#za pomocą programu .NET framework](/dotnet/fsharp/)
- [R i Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [F#za pomocą programu .NET framework](/dotnet/fsharp/)
::: moniker-end

![Obciążenie aplikacji analitycznych i naukowych opracowań danych, w Instalatorze programu Visual Studio](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python i R są dwa podstawowe języków skryptów używane do analizy danych. Oba języki są do nauczenia i są obsługiwane przez bogatego ekosystemu pakietów. Te pakiety adresów szerokiej gamy scenariuszy, takich jak pozyskiwanie danych, czyszczenie, szkolenie modelu, wdrożenie i wykreślania. F#jest również zaawansowane języka .NET skoncentrowane na funkcjonalności, które jest odpowiednie dla różnych zadań przetwarzania danych.
::: moniker-end

::: moniker range="vs-2019"
Język Python jest podstawowy język skryptowy służący do analizy danych. Python łatwo nauczyć się i jest obsługiwany przez bogatego ekosystemu pakietów. Te pakiety adresów szerokiej gamy scenariuszy, takich jak pozyskiwanie danych, czyszczenie, szkolenie modelu, wdrożenie i wykreślania. F#jest również zaawansowane języka .NET skoncentrowane na funkcjonalności, które jest odpowiednie dla różnych zadań przetwarzania danych. (W języku R, firma Microsoft zaleca [notesów usługi Azure](https://notebooks.azure.com).)
::: moniker-end

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu programu Visual Studio przy użyciu języka R, Python, iF#](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Opcje obciążenia

Domyślnie obciążenie instalowane są następujące opcje, które można modyfikować w sekcji podsumowania dla obciążenia w Instalatorze programu Visual Studio:

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
  - [Anaconda3, wersja 64-bitowych](https://www.continuum.io), dystrybucja języka Python, obejmującą bibliotek do nauki o danych rozbudowane i interpreter języka Python.
  - Obsługa sieci web w języku Python
  - Obsługa szablonów Cookiecutter
- R:
  - Obsługa języka R
  - Obsługa środowiska uruchomieniowego dla narzędzi programistycznych języka R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (firmy Microsoft w pełni zgodne, obsługiwane przez społeczności R interpreter z bibliotekami programu ScaleR szybciej obliczeń na pojedyncze węzły lub w klastrach. Możesz również użyć dowolnego języka R od [CRAN](https://cran.r-project.org/).)
::: moniker-end

## <a name="sql-server-integration"></a>Integracja programu SQL Server

::: moniker range="vs-2017"
Obsługa programu SQL Server przy użyciu języka R i Python do zaawansowanej analizy bezpośrednio w programie SQL Server. Obsługa języka R jest dołączony do programu SQL Server 2016 lub nowszy; Obsługa w języku Python jest dostępne w programie SQL Server 2017 CTP 2.0 i nowszych wersjach.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server obsługuje przy użyciu języka Python do zaawansowanej analizy bezpośrednio w programie SQL Server. Obsługa w języku Python jest dostępne w programie SQL Server 2017 CTP 2.0 i nowszych wersjach.
::: moniker-end

Uruchamianie kodu, w których już są przechowywane dane zapewnia następujące korzyści:

- **Eliminacja przenoszenia danych**: Zamiast przenoszenia danych z bazy danych do aplikacji lub modelu, możesz tworzyć aplikacje w bazie danych. Ta funkcja pozwala wyeliminować bariery zabezpieczeń, zgodności, ładu, integralności i hostem podobne problemy związane z przenoszenie ogromnych ilości danych w całym. Można również korzystać zestawów danych, który nie mieści się w pamięci komputera klienta.

- **Łatwe wdrażanie**: Przygotować modelu wdrażania do środowiska produkcyjnego po polegać na osadzenie jej w skrypcie języka T-SQL. Każda aplikacja kliencka SQL napisane w dowolnym języku mogą następnie korzystać z modeli i analizy za pośrednictwem wywołania procedury składowanej. Nie integracji języka są niezbędne.

- **Przeznaczonych dla przedsiębiorstw, wydajności i skali**: Można użyć zaawansowanych możliwości programu SQL Server, takich jak kolumn i tabel w pamięci indeksów, skalowalnych interfejsów API o wysokiej wydajności przechowywania w pakietach RevoScale. Eliminacja przenoszenie danych oznacza także uniknąć ograniczenia pamięci klienta, zgodnie z rosnącą ilością danych lub chcesz zwiększyć wydajność aplikacji.

- **Bogate opcje rozszerzalności**: Można zainstalować i uruchomić dowolne z najnowszych pakietów "open source" w programie SQL Server do tworzenia uczenia głębokiego i sztucznej Inteligencji aplikacje na bardzo duże ilości danych w programie SQL Server. Instalowanie pakietu w programie SQL Server jest proste i polega na zainstalowaniu pakietu na komputerze lokalnym.

- **Powszechną dostępność bez ponoszenia dodatkowych kosztów**: Integracji języków są dostępne we wszystkich wersjach programu SQL Server 2017 i nowszym, w tym wersja Express.

Aby w pełni korzystać z integracji z programem SQL Server, użyj Instalatora programu Visual Studio do zainstalowania **przechowywanie i przetwarzanie danych** obciążenia za pomocą **SQL Server Data Tools** opcji. Tę druga opcję umożliwia SQL IntelliSense, wyróżnianie składni i wdrażania.

![Obciążenie przechowywania i przetwarzania danych](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Magazyn danych i opcje obciążenie przetwarzania](media/workload/data-storage-workload-options.png)

Informacje dodatkowe:

::: moniker range="vs-2017"
- [Praca z programu SQL Server i R](../rtvs/integrating-sql-server-with-r.md)
- [W bazie danych Advanced Analytics przy użyciu języka R w programie SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [Język Python w programie SQL Server 2017: rozszerzonego uczenia maszynowego w bazie danych (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Dodatkowe usługi i zestawy SDK

Oprócz nowości w obciążeniu analizy danych i aplikacji do analizy bezpośrednio usługi platformy Azure, notesy i zestawu Azure SDK dla języka Python są również przydatne do analizy danych.

Zestaw Azure SDK dla języka Python ułatwia wykorzystanie i zarządzanie usługami Microsoft Azure z poziomu aplikacji w systemie Windows, Mac i Linux. Aby uzyskać więcej informacji, zobacz [zestawu Azure SDK dla języka Python](../python/azure-sdk-for-python.md)

Notesy platformy Azure (obecnie w wersji zapoznawczej) zawiera bezpłatny dostęp online do notesów programu Jupyter, działające w chmurze w systemie Microsoft Azure. Usługa obejmuje notesów przykładowy w języku Python, R, a F# ułatwią Ci rozpoczęcie pracy. Odwiedź stronę [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu notesy platformy Azure wraz z wprowadzeniem do przykładu R](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
