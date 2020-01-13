---
title: Wprowadzenie przy użyciu języka Python | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 960511fcfb83dfc6ac3c58a806d8a23f1ff61597
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918778"
---
# <a name="getting-started-with-python"></a>Wprowadzenie do języka Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools for Visual Studio (PTVS) to bezpłatna wtyczka typu ["Open Source](https://github.com/Microsoft/ptvs) " dla programu Visual Studio, która oferuje zaawansowane środowisko programistyczne języka Python.  
  
## <a name="python-the-language"></a>Język Python
  
Python to popularny język programowania używany przez wiele uniwersytetów, naukowców, skryptów aplikacji, dostępnych deweloperów i profesjonalnych deweloperów, pracę nad aplikacjami, witrynami sieci Web i usługami w chmurze.

Język programowania to:
  
- Miarodaj.
- Zazwyczaj przydatne w przypadku tworzenia skryptów szybkich programów, skryptów aplikacji, aplikacji klasycznych, serwerów sieci Web, usług sieci Web i obliczeń naukowych.
- Łatwa do uczenia się i ma dobry projekt, aby zachęcić do dobrego kodowania (wiele uniwersytetów używa go do wprowadzenia kursów programistycznych).
- Elastyczność, obsługa bezwzględnych, funkcjonalnych i zorientowanych na obiekty stylów programowania.
- Bezpłatna i open source.
- Działa prawidłowo we wszystkich głównych systemach operacyjnych.  
- Obsługiwane przez wiele bezpłatnych, przydatnych i dobrze zaprojektowanych bibliotek.  
- Obsługa wielu dokumentacji, przykładów i silnej społeczności deweloperów.  

Aby dowiedzieć się więcej o języku, Zacznij od języka [Python dla początkujących](https://www.python.org/about/gettingstarted/) w witrynie Python.org.

Aby zainstalować język Python, odwiedź stronę [https://www.python.org/download/](https://www.python.org/download/).

## <a name="python-tools-for-visual-studio"></a>{1&gt;{2&gt;Python Tools for Visual Studio&lt;2}&lt;1}
  
Python Tools for Visual Studio, którą można zainstalować z [VisualStudio.com](https://www.visualstudio.com/explore/python-vs), zapewniają następujące funkcje:  
  
- Obsługa wielu interpreterów: różne wersje CPython, IronPython i IPython  
- System projektu, który niejawnie pobiera strukturę folderów kodu w języku Python, a także umożliwia jawną kontrolę, aby można było identyfikować kod aplikacji, kod testowy, strony sieci Web, skrypty języka JavaScript, skryptów kompilacji i tak dalej.  
- Szablony projektów dla konsoli, sieci Web, platformy Azure, analizy danych i innych typów projektów.    
- Zestaw Azure SDK dla języka Python (patrz poniżej)    
- Zaawansowane funkcje edycji i zrozumienia kodu, w tym kolorowanie składni, Autouzupełnianie wszystkich kodów i bibliotek, pomoc w sygnaturach, Widok klas, przejdź do definicji, Znajdź wszystkie odwołania, refaktoryzacje i inne.    
- Okno interaktywne (REPL)
- IPython z wizualizacjami danych.
- Obsługa IronPython i .NET/WPF.    
- Rozbudowane debugowanie bez projektu programu Visual Studio, możliwość istniejącego pliku wykonywalnego, debugowanie w trybie mieszanym, zdalne debugowanie do systemu Windows/Linux/Mac oraz debugowanie w oknie interaktywnym.   
- Narzędzia profilowania.  
- Narzędzia do testowania.  
  
Następujące zasoby pomogą Ci rozpocząć pracę:

- [Przewodnik instalacji](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Krótkie wideo z wprowadzeniem i głębokim szczegółowe](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- (Instalacja i funkcje wersji demonstracyjnej (27 min)](https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Dokumentacja](https://github.com/Microsoft/PTVS/wiki)  

Należy pamiętać, że program Visual Studio nie udostępnia teraz metody tworzenia autonomicznego pliku wykonywalnego przy użyciu języka Python, który zasadniczo oznacza program z osadzonym interpreterem języka Python. Jednak w ramach społeczności języka Python istnieją różne metody, które zostały opisane w artykule [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython obsługuje również osadzanie w aplikacji natywnej, zgodnie z opisem w wpisie w blogu, [przy użyciu pliku zip](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)z możliwością osadzenia CPython.
  
## <a name="building-ui-with-python"></a>Tworzenie interfejsu użytkownika przy użyciu języka Python  

Główną ofertą kompilowania interfejsu użytkownika przy użyciu języka Python jest [projekt QT](https://www.qt.io/qt-for-application-development/)z powiązaniami dla języka Python znanego jako [pyside (oficjalnego powiązania)](https://wiki.qt.io/PySide) (Zobacz też [pliki do pobrania pyside](https://download.qt.io/official_releases/pyside/.)) i [PyQt](https://wiki.python.org/moin/PyQt). W chwili obecnej Obsługa w języku Python w programie Visual Studio nie ma żadnych określone narzędzia do tworzenia interfejsu użytkownika.

## <a name="azure-sdk-for-python"></a>Zestaw Azure SDK dla języka Python
  
Zestaw Azure SDK dla języka Python, który obsługuje systemy Windows, Mac i Linux, ułatwia korzystanie z usług Microsoft Azure i zarządzanie nimi. Aby uzyskać szczegółowe informacje, zobacz następujące zasoby: 

- Aby zainstalować zestaw SDK, użyj [indeksu pakietu języka Python](https://pypi.python.org/pypi/azure) lub [Zainstaluj Język Python i zestaw SDK](/azure/python/python-sdk-azure-install) w dokumentacji platformy Azure. 
- [Zestaw Azure SDK dla Centrum deweloperów języka Python](https://azure.microsoft.com/develop/python/) zawiera wiele pomocy od instalacji do dokumentacji z samouczkami.  Poniżej przedstawiono niektóre najważniejsze elementy:  
- Przewodniki z instrukcjami:
  - [Obiekt blob magazynu](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Kolejka magazynu](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Tabela magazynu](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Kolejki usługi Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Tematy Service Bus/subskrypcje](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Zarządzanie usługami](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Obliczenia naukowe

Oprócz wszystkich bibliotek danych w języku Python, Python Tools for Visual Studio obsługuje notesy IPython i IPython, które mogą być hostowane na platformie Azure.

Zalecamy uzyskanie bibliotek IPython i naukowych obliczeniowych (matplotlib, scipy, numpy itp.) z [University of Kalifornii, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Zobacz też  

[Wprowadzenie z PTVS: Konfigurowanie programu Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[wprowadzenie z PTVS: Rozpocznij kodowanie (projekty)](../python/getting-started-with-ptvs-start-coding-projects.md)
[wprowadzenie z PTVS: edytowanie kodu](../python/getting-started-with-ptvs-editing-code.md)
[wprowadzenie z PTVS: debugowanie](../python/getting-started-with-ptvs-debugging.md)
[wprowadzenie z PTVS: Interactive Python](../python/getting-started-with-ptvs-interactive-python.md)
wprowadzenie [z PTVS: Tworzenie witryny sieci Web na platformie Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
