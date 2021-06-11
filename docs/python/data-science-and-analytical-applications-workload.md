---
title: Obciążenie Dla aplikacji analizy i przetwarzania danych
description: To Visual Studio łączy język Python, język F# i odpowiednie dystrybucje środowiska uruchomieniowego, w tym środowisko Anaconda. (R jest również dołączony Visual Studio 2017 r.)
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: 2c12c8a0979ab081ea2f09faeeccdb5a8a9d2175
ms.sourcegitcommit: 398b4d4e5ce0f978720f11990db05b209766aedc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2021
ms.locfileid: "112016310"
---
# <a name="install-data-science-support-in-visual-studio"></a>Instalowanie obsługi nauki o danych w programie Visual Studio

Obciążenie Aplikacje do analizy i przetwarzania danych, które można wybrać i zainstalować za pomocą instalatora Visual Studio, łączy w sobie kilka języków i ich odpowiednich dystrybucji środowiska uruchomieniowego:

::: moniker range="vs-2017"
- [Python i Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# z platformą .NET Framework](/dotnet/fsharp/)
- [R i Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [F# z platformą .NET Framework](/dotnet/fsharp/)
::: moniker-end

![Obciążenie Aplikacje do analizy i przetwarzania danych w instalatorze Visual Studio danych](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python i R to dwa podstawowe języki skryptowe używane do nauki o danych. Oba języki są łatwe do nauczenia się i są obsługiwane przez bogaty ekosystem pakietów. Te pakiety rozsyłają szeroką gamę scenariuszy, takich jak pozyskiwanie danych, czyszczenie, trenowanie modelu, wdrażanie i kreślenie. F# to również zaawansowany język .NET o pierwszym funkcjonalności, który jest odpowiedni dla szerokiej gamy zadań przetwarzania danych.
::: moniker-end

::: moniker range=">=vs-2019"
Python to podstawowy język skryptowy używany do nauki o danych. Język Python jest łatwy do nauczenia się i jest obsługiwany przez bogaty ekosystem pakietów. Te pakiety rozsyłają szeroką gamę scenariuszy, takich jak pozyskiwanie danych, czyszczenie, trenowanie modelu, wdrażanie i kreślenie. F# to również zaawansowany język .NET typu "najpierw funkcjonalne", który jest odpowiedni dla szerokiej gamy zadań przetwarzania danych).
::: moniker-end

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu przedstawiający Visual Studio językach R, Python i F #](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Opcje obciążenia

Domyślnie obciążenie instaluje następujące opcje, które można zmodyfikować w sekcji podsumowania obciążenia w Visual Studio instalatora:

::: moniker range=">=vs-2019"
- Obsługa języka F# desktop
- Python:
  - Obsługa języka Python
  - Obsługa sieci Web w języku Python
::: moniker-end

::: moniker range="vs-2017"
- Obsługa języka F#
- Python:
  - Obsługa języka Python
  - [64-bitowa biblioteka Anaconda3](https://www.continuum.io), dystrybucji języka Python, która zawiera rozbudowane biblioteki nauki o danych i interpreter języka Python.
  - Obsługa sieci Web w języku Python
  - Obsługa szablonów Cookiecutter
- R:
  - Obsługa języka R
  - Obsługa środowiska uruchomieniowego dla narzędzi deweloperskie języka R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (w pełni zgodny, obsługiwany przez społeczność interpreter języka R firmy Microsoft z bibliotekami programu ScaleR w celu szybszego wykonywania obliczeń w pojedynczych węzłach lub klastrach. Można również użyć dowolnego języka R z [CRAN).](https://cran.r-project.org/)
::: moniker-end

## <a name="sql-server-integration"></a>Integracja programu SQL Server

::: moniker range="vs-2017"
SQL Server języka Python i R do zaawansowanej analizy bezpośrednio w środowisku SQL Server. Obsługa R jest dołączona do SQL Server 2016 i nowszych; Obsługa języka Python jest dostępna w wersji SQL Server 2017 CTP 2.0 i nowszych.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server języka Python do zaawansowanej analizy bezpośrednio w SQL Server. Obsługa języka Python jest dostępna w wersji SQL Server 2017 CTP 2.0 i nowszych.
::: moniker-end

Uruchamiając kod, w którym już są dane, możesz korzystać z następujących zalet:

- **Eliminacja przenoszenia** danych: zamiast przenoszenia danych z bazy danych do aplikacji lub modelu można tworzyć aplikacje w bazie danych. Ta funkcja eliminuje bariery zabezpieczeń, zgodności, ładu, integralności i wielu podobnych problemów związanych z przenoszeniem ogromnych ilości danych. Możesz również korzystać z zestawów danych, które nie mieściły się w pamięci maszyny klienckiej.

- **Łatwe wdrażanie:** gdy model będzie gotowy, wdrożenie go w środowisku produkcyjnym to prosta kwestia osadzenia go w skrypcie języka T-SQL. Każda aplikacja klienska SQL napisana w dowolnym języku może następnie korzystać z modeli i inteligencji za pośrednictwem wywołania procedury składowanej. Nie są wymagane żadne integracje z określonym językiem.

- **Wydajność i** skala klasy korporacyjnej: za pomocą zaawansowanych możliwości usługi SQL Server, takich jak indeksy tabel w pamięci i magazynu kolumn, można używać skalowalnych interfejsów API o wysokiej wydajności w pakietach RevoScale. Eliminacja ruchu danych oznacza również, że unika się ograniczeń pamięci klienta w miarę zwiększania się ilości danych lub zwiększania wydajności aplikacji.

- **Rozbudowane możliwości** rozszerzania: możesz instalować i uruchamiać dowolne najnowsze pakiety open source w programie SQL Server, aby tworzyć aplikacje uczenia głębokiego i AI na ogromnych ilościach danych na platformie SQL Server. Instalowanie pakietu w SQL Server jest tak proste jak zainstalowanie pakietu na komputerze lokalnym.

- **Szeroka dostępność bez dodatkowych kosztów:** integracje języków są dostępne we wszystkich wersjach programu SQL Server 2017 i nowszych, w tym w wersji Express.

Aby w pełni wykorzystać możliwości SQL Server, użyj instalatora usługi Visual Studio, aby zainstalować obciążenie Magazyn danych i przetwarzanie **z** opcją narzędzia SQL Server **Data Tools.** Druga opcja umożliwia korzystanie z funkcji Sql IntelliSense, wyróżnianie składni i wdrażanie.

![Obciążenie magazynu i przetwarzania danych](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Opcje obciążenia magazynu i przetwarzania danych](media/workload/data-storage-workload-options.png)

Więcej informacji:

::: moniker range="vs-2017"
- [Praca z SQL Server i R](../rtvs/integrating-sql-server-with-r.md)
- [Advanced Analytics with R in-database in-database in SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [Python in SQL Server 2017: enhanced in-database machine learning (Python w wersji 2017: ulepszone uczenie maszynowe w bazie danych) (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Dodatkowe usługi i zestawy SDK

Oprócz tego, co znajduje się bezpośrednio w obciążeniu Aplikacje do analizy i przetwarzania danych, usługa Azure Notebooks i zestaw Azure SDK dla języka Python są również pomocne w nauce o danych.

Zestaw Azure SDK dla języka Python ułatwia korzystanie z usług Microsoft Azure z aplikacji działających w systemach Windows, Mac i Linux oraz zarządzanie nimi. Aby uzyskać więcej informacji, zobacz [Zestaw Azure SDK dla języka Python.](/azure/python/)

Azure Notebooks (obecnie w wersji zapoznawczej) zapewnia bezpłatny dostęp online do notesów Jupyter uruchomionych w chmurze na platformie Microsoft Azure. Usługa zawiera przykładowe notesy w językach Python, R i F#, aby rozpocząć pracę. Odwiedź [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Zrzuty ekranu Azure Notebooks z przykładowym wprowadzeniem do R](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
