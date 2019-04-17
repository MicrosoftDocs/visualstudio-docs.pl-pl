---
title: Wprowadzenie do języka Python | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 9c18ae2731d92e6d128d13e7687bac77ae76dc8a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648458"
---
# <a name="getting-started-with-python"></a>Wprowadzenie do języka Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia Python Tools for Visual Studio (narzędzi PTVS), to bezpłatny, [typu open-source](https://github.com/Microsoft/ptvs) dodatek dla programu Visual Studio środowisko zaawansowane Programowanie w języku Python.  
  
## <a name="python-the-language"></a>Język Python
  
Język Python jest popularnych języków programowania, który jest używany przez wiele uniwersytety, analitykom, twórcom aplikacji skryptów, deweloperzy zwykłych i profesjonalnych deweloperów, pracy w aplikacji, witryn sieci web i usług w chmurze.

Język programowania Python jest jako:
  
- Niezawodne.
- Zazwyczaj przydatne w przypadku skryptów szybkiego programów, skryptów aplikacji, aplikacje klasyczne, serwery sieci web, usług sieci web i obliczeń naukowych.
- Do nauczenia i ma dobry projekt, aby zachęcać do dobrego kodowania (wiele uniwersytety użyć go wprowadzające kursy programowania).
- Elastyczna Obsługa stylów programowania imperatywnego, funkcjonalności i zorientowane obiektowo.
- Bezpłatne, a oprogramowanie typu open source.
- Działa dobrze we wszystkich najważniejszych systemach operacyjnych.  
- Obsługiwane przez wiele bezpłatnych, przydatne i dobrze zaprojektowane biblioteki.  
- Obsługiwane przez mnóstwo dokumentacji, przykładów i społeczności deweloperów silne.  

Aby dowiedzieć się więcej o języku, zacznij od [języka Python dla początkujących](https://www.python.org/about/gettingstarted/) w witrynie python.org.

Do zainstalowania języka Python, samego, odwiedź stronę [ https://www.python.org/download/ ](https://www.python.org/download/).

## <a name="python-tools-for-visual-studio"></a>Narzędzia języka Python dla programu Visual Studio
  
Python Tools for Visual Studio, które można zainstalować z [visualstudio.com](https://www.visualstudio.com/explore/python-vs), zapewniają następujące funkcje:  
  
- Obsługa wielu interpreterów: różne wersje CPython, IronPython i IPython  
- System projektu, niejawnie przejmuje strukturę folderów w kodzie języka Python, a także umożliwia jawną kontrolę, dzięki czemu można zidentyfikować kodu aplikacji, kodu testu, stron sieci web, JavaScript, skrypty kompilacji i tak dalej.  
- Szablony projektu dla konsoli sieci web, Azure, nauki o danych i innych rodzajów projektów.    
- Zestaw Azure SDK dla języka Python (patrz poniżej)    
- Zaawansowane edytowanie i kod zrozumienie funkcje w tym kolorowania, automatycznego uzupełniania dla całego kodu i bibliotek, pomocy dotyczącej sygnatur, widoku klas, przejdź do definicji i Znajdź wszystkie odwołania, refaktoryzacji i więcej.    
- Okno interaktywne (REPL)
- Program IPython za pomocą wizualizacji danych.
- Wsparcie dla języków IronPython i platformy .NET/WPF.    
- Zaawansowane funkcje debugowania bez projektu programu Visual Studio, możliwość istniejącego pliku wykonywalnego, mieszany tryb debugowania zdalnego debugowania w systemie Linux/Windows/Mac i debugowanie w oknie interaktywnym.   
- Narzędzia profilowania.  
- Narzędzia do testowania.  
  
Następujące zasoby pomogą Ci rozpocząć pracę:

- [Przewodnik instalacji](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Wprowadzenie rozpoczęcie pracy i deep dive krótkie filmy wideo](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- (Instalacja i funkcje wersji demonstracyjnej (27 min)]https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Dokumentacja](https://github.com/Microsoft/PTVS/wiki)  

Należy pamiętać, że program Visual Studio nie obecnie zapewnia oznacza, że do utworzenia autonomicznego pliku wykonywalnego przy użyciu języka Python, co oznacza programu przy użyciu osadzonych interpreter języka Python. Istnieją różne środki w ramach społeczności języka Python w tym celu zgodnie z opisem na [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython obsługuje również osadzona w aplikacji macierzystej, zgodnie z opisem na wpis w blogu [możliwego do osadzenia pliku Zip przy użyciu CPython](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/).
  
## <a name="building-ui-with-python"></a>Tworzenie interfejsu użytkownika za pomocą języka Python  

Główne oferty tworzenia interfejsu użytkownika za pomocą języka Python jest [projektu Qt](https://www.qt.io/qt-for-application-development/), powiązań dla języka Python, znane jako [PySide (oficjalna powiązania)](http://wiki.qt.io/PySide) (Zobacz też [PySide pliki do pobrania](https://download.qt.io/official_releases/pyside/.)) i [PyQt](https://wiki.python.org/moin/PyQt). W chwili obecnej Obsługa w języku Python w programie Visual Studio nie ma żadnych określone narzędzia do tworzenia interfejsu użytkownika.

## <a name="azure-sdk-for-python"></a>Zestaw Azure SDK dla języka Python
  
Zestaw Azure SDK dla języka Python, który obsługuje Windows, Mac i Linux, ułatwia korzystanie i zarządzanie nimi usług platformy Microsoft Azure. Zapoznaj się z poniższymi zasobami, aby uzyskać szczegółowe informacje: 

- Aby zainstalować zestaw SDK, użyj [indeksu pakietów języka Python](https://pypi.python.org/pypi/azure) lub wykonaj [zainstalowania języka Python i zestawu SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) w dokumentacji platformy Azure. 
- [Zestaw Azure SDK dla Centrum deweloperów języka Python](https://azure.microsoft.com/develop/python/) mnóstwo pomocy instalacji do dokumentacji z samouczków.  Należy wykonać niektóre z najważniejszych:  
- Przewodniki z instrukcjami:
  - [Obiekt Blob magazynu](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Kolejki magazynu](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Tabela magazynu](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Kolejki usługi Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Usługa Service Bus tematów/subskrypcji](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Zarządzanie usługami](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Obliczeń naukowych

Oprócz wszystkich Python analityk danych bibliotek narzędzi Python Tools for Visual Studio obsługuje IPython i Notesy programu IPython, które mogą być hostowane na platformie Azure.

Firma Microsoft zaleca uzyskiwanie IPython i naukowych bibliotek obliczeń (matplotlib, scipy, numpy itp.) z [uniwersytet kalifornijski, Irvine](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Zobacz też  

[Wprowadzenie do narzędzi PTVS: Konfigurowanie programu Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[rozpoczęcie pracy z narzędziami PTVS: Rozpoczęcie kodowania (projekty)](../python/getting-started-with-ptvs-start-coding-projects.md)
[rozpoczęcie pracy z narzędziami PTVS: Edytowanie kodu](../python/getting-started-with-ptvs-editing-code.md)
[rozpoczęcie pracy z narzędziami PTVS: Debugowanie](../python/getting-started-with-ptvs-debugging.md)
[rozpoczęcie pracy z narzędziami PTVS: Interaktywny język Python](../python/getting-started-with-ptvs-interactive-python.md)
[rozpoczęcie pracy z narzędziami PTVS: Tworzenie witryny sieci Web na platformie Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
