---
title: 'Wprowadzenie z PTVS: Interactive Python | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62550990"
---
# <a name="getting-started-with-ptvs-interactive-python"></a>Pierwsze kroki z narzędziami PTVS: interaktywny język Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interaktywne monity lub pętle Read-eval-Print (REPLs) to kluczowe narzędzie do tworzenia wydajnych języków programowania.  Umożliwiają one wykonywanie fragmentów kodu w celu odnajdywania i uczenia interfejsów API, eksperymentowania z użyciem interfejsu API i interaktywnego opracowywania kodu roboczego do dołączenia do projektów lub programów.  
  
 Możesz obejrzeć te instrukcje w bardzo krótkim [filmie wideo](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)w serwisie YouTube.  
  
 W oknie środowiska języka Python zostanie wyświetlona lista wszystkich środowisk języka Python.  Można wybrać jedną z nich, aby otworzyć okno interaktywne lub REPL.  Jeśli kiedykolwiek wcześniej uruchomiono Python.exe w wierszu polecenia, zobaczysz już REPL języka Python.  REPL wyświetla komunikat i można wprowadzić kod, nacisnąć klawisz ENTER i natychmiast zobaczyć wyniki kodu.  Jest to kontekst wykonywania na żywo obejmujący wszystkie stany wszystkich wykonań, przypisań zmiennych itp.  Można odwoływać się do zmiennych, które prowadzą w późniejszych przesłaniu do monitu REPL.  Można napisać wiele wierszy kodu i wykonać je wszystkie jednocześnie (na przykład deklarację metody lub wiele instrukcji).  
  
 Po rozpoczęciu korzystania z nowej biblioteki REPL jest doskonałym sposobem wypróbowania biblioteki.  Możesz zaimportować bibliotekę, sprawdzić pakiety podrzędne, klasy i funkcje.  Język Python może powiedzieć wszystkie te informacje za poorednictwem `help()` funkcji.  Ponadto Python Tools for Visual Studio (PTVS) udostępnia sugestie i dokumentację w oparciu o Modelowanie kodu używane w edytorze, które nie wymaga wykonywania biblioteki.  Gdy wykonujesz kod, PTVS korzysta z informacji z środowiska uruchomieniowego języka Python w celu poprawy PTVS sugestii.  
  
 Okno interaktywne jest również przydatne w przypadku iteracji i ewolucji kodu programistycznego, w tym testowania kodu podczas jego tworzenia.  Możesz wybrać funkcję w oknie edytora, nacisnąć prawy wskaźnik myszy, a następnie wybrać polecenie Wyślij do interaktywne.  To polecenie kopiuje zaznaczenie do okna interaktywnego jako kolejne dane wejściowe i wykonuje je.  Wyniki są natychmiast widoczne.  Jeśli musisz wprowadzić zmiany w poprzednich danych wejściowych, możesz nacisnąć strzałkę w górę, aby odzyskać kod, zmodyfikować go i nacisnąć klawisze CTRL + ENTER, aby wykonać kod.  Naciśnięcie klawisza Enter na końcu danych wejściowych wykonuje go, ale naciśnięcie klawisza ENTER w środku danych wejściowych wstawia nowy wiersz.  
  
 Można otworzyć okno interaktywne dla każdej instalacji języka Python, tak jak chcesz.  W górnej części okna znajdują się przyciski, aby wyczyścić ekran, zresetować kontekst wykonywania itd.  Historia pozostanie nienaruszona.  
  
 Możesz obejrzeć te instrukcje w bardzo krótkim [filmie wideo](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)w serwisie YouTube.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja typu wiki](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [PTVS Wprowadzenie i głębokie wideo szczegółowe](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
