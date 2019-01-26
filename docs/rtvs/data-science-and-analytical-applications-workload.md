---
title: Obciążenie aplikacji analitycznych i naukowych opracowań danych
description: Obciążenie Thsi programu Visual Studio umożliwia połączenie ze sobą Python, R, F#i ich dystrybucji odpowiedniego środowiska uruchomieniowego, w tym Anaconda.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: c7ef2fb2e9d438fb4129d6835cd88663d3025e64
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004698"
---
# <a name="install-data-science-support-in-visual-studio"></a>Nainstalovat podporu do nauki o danych w programie Visual Studio

Obciążenie aplikacji analitycznych i naukowych opracowań danych, który zaznaczyć i zainstalować za pomocą Instalatora programu Visual Studio, umożliwia połączenie ze sobą w trzech językach i ich dystrybucji odpowiedniego środowiska uruchomieniowego:

- [R i Microsoft R Client](../rtvs/index.md)
- [Python i Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F#za pomocą programu .NET framework](/dotnet/fsharp/)

![Obciążenie aplikacji analitycznych i naukowych opracowań danych, w Instalatorze programu Visual Studio](media/data-science-workload.png)

Języki R i Python są dwa podstawowe języków skryptów używane do analizy danych. Oba języki są do nauczenia i są obsługiwane przez bogatego ekosystemu pakietów. Te pakiety adresów szerokiej gamy scenariuszy, takich jak pozyskiwanie danych, czyszczenie, szkolenie modelu, wdrożenie i wykreślania. F#jest również zaawansowane języka .NET skoncentrowane na funkcjonalności, które jest odpowiednie dla różnych zadań przetwarzania danych.

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu programu Visual Studio przy użyciu języka R, Python, iF#](media/data-science-workload-screens.png)](media/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Opcje obciążenia

Domyślnie obciążenie instalowane są następujące opcje, które można modyfikować w sekcji podsumowania dla obciążenia w Instalatorze programu Visual Studio:

- F#Obsługa języków
- Python:
  - Obsługa języka Python
  - [Anaconda3, wersja 64-bitowych](https://www.continuum.io) (dystrybucja języka Python, obejmującą bibliotek do nauki o danych rozbudowane i interpreter języka Python)
  - Obsługa sieci web w języku Python
  - Obsługa szablonów Cookiecutter
- R:
  - Obsługa języka R
  - Obsługa środowiska uruchomieniowego dla narzędzi programistycznych języka R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (firmy Microsoft w pełni zgodne, obsługiwane przez społeczności R interpreter z bibliotekami programu ScaleR szybciej obliczeń na pojedyncze węzły lub w klastrach. Możesz również użyć dowolnego języka R od [CRAN](https://cran.r-project.org/).)

Mimo że F# jest dołączana do wielu innych obciążeń i Python ma obciążenie własną, do nauki o danych i aplikacjom analitycznym tylko obciążenia w chwili obecnej, która obejmuje języka R. Jednakże można także zainstalować niezależnie od obciążenia języka R. Na **poszczególne składniki** w Instalatorze, a następnie wybierz następujące opcje R:

- **Działań programistycznych** > **obsługę języka R**
- **Działań programistycznych** > **Microsoft R Client**
- **Kompilatory, narzędzia do kompilacji i środowiska uruchomieniowe** > **obsługę środowiska uruchomieniowego dla narzędzi programistycznych języka R**

## <a name="sql-server-integration"></a>Integracja programu SQL Server

Obsługa programu SQL Server za pomocą języków R i Python do zaawansowanej analizy bezpośrednio w programie SQL Server. Obsługa języka R jest dołączony do programu SQL Server 2016 lub nowszy; Obsługa w języku Python jest dostępne w programie SQL Server 2017 CTP 2.0 i nowszych wersjach.

Uruchamianie kodu, w których już są przechowywane dane zapewnia następujące korzyści:

- **Eliminacja przenoszenia danych**: Zamiast przenoszenia danych z bazy danych do aplikacji lub modelu, możesz tworzyć aplikacje języków R i Python w bazie danych. Ta funkcja pozwala wyeliminować bariery zabezpieczeń, zgodności, ładu, integralności i hostem podobne problemy związane z przenoszenie ogromnych ilości danych w całym. Można również korzystać zestawów danych, który nie mieści się w pamięci komputera klienta.

- **Łatwe wdrażanie**: Gdy masz model języka R lub Python, wszystko będzie gotowe, jego wdrożeniem w środowisku produkcyjnym jest polegać na osadzenie jej w skrypcie języka T-SQL. Każda aplikacja kliencka SQL napisane w dowolnym języku mogą następnie korzystać z modeli i analizy za pośrednictwem wywołania procedury składowanej. Nie określonego integracji języka R lub Python są niezbędne.

- **Przeznaczonych dla przedsiębiorstw, wydajności i skali**: Można użyć zaawansowanych możliwości programu SQL Server, takich jak indeksy magazynu kolumn i tabel w pamięci, skalowalnych interfejsów API o wysokiej wydajności w pakietach kolekcję funkcji RevoScaleR i biblioteki. Eliminacja przenoszenie danych oznacza także uniknąć ograniczenia pamięci klienta, zgodnie z rosnącą ilością danych lub chcesz zwiększyć wydajność aplikacji.

- **Bogate opcje rozszerzalności**: Można zainstalować i uruchomić dowolne z najnowszą "open source" pakietów języka R lub Python w programie SQL Server do tworzenia uczenia głębokiego i sztucznej Inteligencji aplikacje na bardzo duże ilości danych w programie SQL Server. Instalowanie pakietu w programie SQL Server jest proste i polega na zainstalowaniu pakietu na komputerze lokalnym.

- **Powszechną dostępność bez ponoszenia dodatkowych kosztów**: Integracje z języków R i Python są dostępne we wszystkich wersjach programu SQL Server 2017 i nowszym, w tym wersja Express. (Obsługa języka R jest dostępne w programie SQL Server 2016 i nowszych wersjach).

Aby w pełni korzystać z integracji z programem SQL Server, użyj Instalatora programu Visual Studio do zainstalowania **przechowywanie i przetwarzanie danych** obciążenia za pomocą **SQL Server Data Tools** opcji. Tę druga opcję umożliwia SQL IntelliSense, wyróżnianie składni i wdrażania.

![Obciążenie przechowywania i przetwarzania danych](media/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Magazyn danych i opcje obciążenie przetwarzania](media/data-storage-workload-options.png)

Informacje dodatkowe:

- [Praca z programu SQL Server i R](integrating-sql-server-with-r.md)
- [W bazie danych Advanced Analytics przy użyciu języka R w programie SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
- [Język Python w programie SQL Server 2017: rozszerzonego uczenia maszynowego w bazie danych (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Dodatkowe usługi i zestawy SDK

Oprócz nowości w obciążeniu analizy danych i aplikacji do analizy bezpośrednio usługi platformy Azure, notesy i zestawu Azure SDK dla języka Python są również przydatne do analizy danych.

Zestaw Azure SDK dla języka Python ułatwia wykorzystanie i zarządzanie usługami Microsoft Azure z poziomu aplikacji w systemie Windows, Mac i Linux. Aby uzyskać więcej informacji, zobacz [zestawu Azure SDK dla języka Python](../python/azure-sdk-for-python.md)

Notesy platformy Azure (obecnie w wersji zapoznawczej) zawiera bezpłatny dostęp online do notesów programu Jupyter, działające w chmurze w systemie Microsoft Azure. Usługa obejmuje notesów przykładowy w języku Python, R, a F# ułatwią Ci rozpoczęcie pracy. Visit[notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu notesy platformy Azure wraz z wprowadzeniem do przykładu R](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png#lightbox)
