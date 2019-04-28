---
title: 'Wprowadzenie do narzędzi PTVS: Interaktywny język Python | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: fa594314-bdd0-4da5-874a-57b03414b675
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 4fba8bf658a50a7a7e28abace1eb622ab14f5f26
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62550990"
---
# <a name="getting-started-with-ptvs-interactive-python"></a>Wprowadzenie do narzędzi PTVS: Interaktywny język Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interaktywne monity lub odczytu eval-print pętli (REPLs) to główne narzędzie wydajność języków programowania.  Umożliwiają wykonywanie fragmenty kodu w celu odnajdywania i Dowiedz się, interfejsów API, eksperymentować, przy użyciu interfejsu API i interaktywnie tworzyć działającego kodu, które mają zostać objęte projektów lub programów.  
  
 Możesz obserwować te instrukcje w bardzo krótkim [wideo usługi youtube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 W oknie środowiska Python możesz wyświetlić listę wszystkich środowisk języka Python.  Można wybrać jeden z nich, aby otworzyć okno interaktywne lub replikacja  Jeśli kiedykolwiek uruchomieniu Python.exe w wierszu polecenia, a następnie w tym samouczku python REPL przed.  REPL monit i można wprowadzić kod, naciśnij klawisz enter i od razu Zobacz wyniki kodu.  To jest kontekst wykonywania na żywo, który zawiera wszystkie stany wszystkie swoje wykonań przypisania zmiennych, itp.  Mogą odwoływać się do zmiennych, zawierający wyniki w późniejszym oświadczenia REPL monitu.  Można napisać kilka wierszy kodu i wykonać je w całości (na przykład deklaracji metody lub wiele instrukcji).  
  
 Po uruchomieniu przy użyciu nowej biblioteki, rozwiązaniu REPL jest doskonałym sposobem na wypróbowanie biblioteki.  Można zaimportować bibliotekę, inspekcja pakietów sub, klasy i funkcje.  Python udzieli wszystkie te informacje za pośrednictwem jego `help()` funkcji.  Ponadto narzędzia Python Tools for Visual Studio (PTVS) zapewnia sugestie i dokumentacji oparty na jego modelowania kod używany w edytorze robi bez konieczności wykonywania biblioteki.  Podczas wykonywania kodu, narzędzi PTVS używa informacji ze środowiska wykonawczego języka Python do ulepszenia narzędzi PTVS sugestie.  
  
 Okno interaktywne to również przydatne w przypadku tworzenia kodu iteracji lub ewolucyjny, łącznie z testowaniem kodu podczas jego tworzenia.  Można wybierz funkcję w oknie edytora, naciśnij przycisk prawo wskaźnika i wybierz opcję Wyślij do środowiska interaktywnego.  To polecenie kopiuje zaznaczenie do okna interaktywnego jako dane wejściowe następnej i uruchamia go.  Natychmiastowe zobaczenie wyników.  Jeśli trzeba dokonać zmian poprzednim dane wejściowe, możesz wcisnąć strzałka, aby wrócić kod, Modyfikuj, a następnie naciśnij klawisz Ctrl + Enter w górę do wykonywania kodu.  Naciśnięcie klawisza Enter na końcu danych wejściowych jest wykonywana, ale naciśnięcie klawisza Enter w trakcie wprowadzania wstawia nowy wiersz.  
  
 Możesz otworzyć okno interaktywne dla każdej instalacji języka Python, tyle w taki sposób, jak chcesz.  Dostępne są przyciski w górnej części okna, aby wyczyścić ekran, Resetowanie kontekstu wykonania itd.  Historię pozostaną nienaruszone.  
  
 Możesz obserwować te instrukcje w bardzo krótkim [wideo usługi youtube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja witryny typu wiki](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [Wprowadzenie rozpoczęcie pracy i Deep Dive wideo narzędzi PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
