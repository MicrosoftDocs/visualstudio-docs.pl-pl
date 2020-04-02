---
title: Wprowadzenie do pythona | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 97d60fe31f838c4cc497701f4560dc426ebc1cc9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543971"
---
# <a name="getting-started-with-python"></a>Wprowadzenie do języka Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia Python dla programu Visual Studio (PTVS) to bezpłatna wtyczka [typu open source](https://github.com/Microsoft/ptvs) dla programu Visual Studio, która jest zaawansowana wersja programowa Python.  
  
## <a name="python-the-language"></a>Python język
  
Python jest popularnym językiem programowania, który jest używany przez wiele uniwersytetów, naukowców, skryptów aplikacji, zwykłych programistów i profesjonalnych programistów, pracujących nad aplikacjami, witrynami internetowymi i usługami w chmurze.

Jako język programowania Python jest:
  
- Niezawodne.
- Ogólnie przydatne do tworzenia skryptów szybkich programów, skryptów aplikacji, aplikacji klasycznych, serwerów sieci web, usług internetowych i komputerów naukowych.
- Łatwy do nauczenia się i ma dobry projekt, aby zachęcić do dobrego kodowania (wiele uniwersytetów używa go do wprowadzających kursów programowania).
- Elastyczne, wspierające style programowania imperatywnego, funkcjonalnego i obiektowego.
- Darmowe i open source.
- Działa dobrze na wszystkich głównych systemach operacyjnych.  
- Obsługiwane przez wiele bezpłatnych, przydatnych i dobrze zaprojektowanych bibliotek.  
- Obsługiwane przez wiele dokumentacji, przykłady i silną społeczność deweloperów.  

Aby dowiedzieć się więcej o języku, zacznij od [Pythona dla początkujących](https://www.python.org/about/gettingstarted/) w python.org.

Aby zainstalować samego [https://www.python.org/download/](https://www.python.org/download/)Pythona, odwiedź .

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
Narzędzia Języka Python dla programu Visual Studio, które można zainstalować z [visualstudio.com,](https://www.visualstudio.com/explore/python-vs)zapewniają następujące funkcje:  
  
- Obsługa wielu tłumaczy: różne wersje CPython, IronPython i IPython  
- System projektu, który niejawnie pobiera strukturę folderów kodu Języka Python, a także umożliwia jawną kontrolę, dzięki czemu można zidentyfikować kod aplikacji, kod testowy, strony internetowe, JavaScript, skrypty kompilacji i tak dalej.  
- Szablony projektów dla konsoli, sieci Web, platformy Azure, nauki o danych i innych typów projektów.    
- Zestaw SDK platformy Azure dla języka Python (zobacz poniżej)    
- Zaawansowane funkcje edycji i rozumienia kodu, w tym kolorowanie składni, automatyczne uzupełnianie wszystkich kodu i bibliotek, pomoc dotycząca podpisu, widok klasy, Przejdź do definicji, Znajdź wszystkie odwołania, refaktoryzacja i inne.    
- Okno interaktywne (REPL)
- IPython z wizualizacjami danych.
- Obsługa ironpython i .NET/WPF.    
- Zaawansowane debugowanie bez projektu programu Visual Studio, możliwość istniejącego wykonywalnego debugowania w trybie mieszanym, zdalne debugowanie do systemu Windows/Linux/Mac i debugowanie w oknie interaktywnym.   
- Narzędzia profilowania.  
- Narzędzia testowe.  
  
Następujące zasoby pomogą Ci rozpocząć pracę:

- [Przewodnik instalacji](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Pierwsze kroki i głębokie nurkowanie krótkie filmy](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Instalacja i funkcje demonstracyjne (27 min)](https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Dokumentacja](https://github.com/Microsoft/PTVS/wiki)  

Należy zauważyć, że visual studio obecnie nie zapewnia środków do tworzenia autonomicznego pliku wykonywalnego przy użyciu języka Python, co zasadniczo oznacza program z wbudowanym interpreterem języka Python. Jednak w społeczności Pythona istnieją różne środki, aby to zrobić zgodnie z opisem w [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython obsługuje również osadzanie w aplikacji natywnej, zgodnie z opisem w blogu, [Korzystanie CPython's Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/).
  
## <a name="building-ui-with-python"></a>Tworzenie interfejsu użytkownika za pomocą języka Python  

Główną ofertą do budowy interfejsu użytkownika z Pythonem jest [Qt Project,](https://www.qt.io/qt-for-application-development/)z powiązaniami dla Pythona znanego jako [PySide (oficjalne powiązanie)](https://wiki.qt.io/PySide) (patrz również [pliki do pobrania PySide)i](https://download.qt.io/official_releases/pyside/.) [PyQt](https://wiki.python.org/moin/PyQt). Obecnie obsługa języka Python w programie Visual Studio nie zawiera żadnych określonych narzędzi do tworzenia interfejsu użytkownika.

## <a name="azure-sdk-for-python"></a>Zestaw Azure SDK dla środowiska Python
  
Zestaw Azure SDK dla języka Python, który obsługuje systemy Windows, Mac i Linux, ułatwia korzystanie z usług Microsoft Azure i zarządzanie nimi. Szczegółowe informacje można znaleźć w następujących zasobach: 

- Aby zainstalować zestaw SDK, należy użyć [indeksu pakietów języka Python](https://pypi.python.org/pypi/azure) lub postępuj zgodnie z [instrukcjami Install Python i SDK](/azure/developer/python/azure-sdk-install) w dokumentacji platformy Azure. 
- [Zestaw Azure SDK dla Python Developer Center](https://azure.microsoft.com/develop/python/) ma wiele pomocy, od instalacji do dokumentacji z samouczkami.  Niektóre z najważniejszych po:  
- Przewodniki z instrukcjami:
  - [Storage Blob](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Kolejka magazynu](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Tabela magazynowania](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Kolejki usługi Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Tematy/subskrypcje usługi Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Zarządzanie usługami](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Informatyka naukowa

Oprócz wszystkich bibliotek naukowiec języka Python, Narzędzia Python dla programu Visual Studio obsługują notesy IPython i IPython, które mogą być hostowane na platformie Azure.

Zalecamy uzyskanie IPython i naukowych bibliotek komputerowych (matplotlib, scipy, numpy, itp.) z [University of California, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Zobacz też  

[Wprowadzenie do PTVS: Konfigurowanie programu Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[Wprowadzenie do PTVS: Start Coding (Projekty)](../python/getting-started-with-ptvs-start-coding-projects.md)
[Wprowadzenie do PTVS: Wprowadzenie](../python/getting-started-with-ptvs-editing-code.md)
do edycji kodu[Wprowadzenie do PTVS: Debugowanie](../python/getting-started-with-ptvs-debugging.md)
[Wprowadzenie do PTVS: Interaktywne](../python/getting-started-with-ptvs-interactive-python.md)
wprowadzenie do[PTV: Tworzenie witryny sieci Web na platformie Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
