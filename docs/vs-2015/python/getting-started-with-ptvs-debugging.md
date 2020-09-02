---
title: 'Wprowadzenie z PTVS: debugowanie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 82803559-1d60-4c57-98fb-2dc1e0182b42
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: b636dd4f3a5c5265231898573bfdf52de2dff84e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197713"
---
# <a name="getting-started-with-ptvs-debugging"></a>Pierwsze kroki z narzędziami PTVS: debugowanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interaktywny debuger programu Visual Studio ułatwia diagnozowanie i rozwiązywanie problemów z kodem języka Python.  
  
 Możesz obejrzeć te instrukcje w bardzo krótkim [filmie wideo](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4)w serwisie YouTube.  
  
 W poprzednim temacie Wprowadzenie można utworzyć pusty projekt aplikacji w języku Python i wprowadzić następujący kod do PythonApplication1.py:  
  
```python  
from math import sin, cos, radians  
import sys  
  
def make_dot_string(x):  
    return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
  
assert make_dot_string(90) == "          o"  
assert make_dot_string(180) == "o"  
  
def main():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
  
if __name__ == "__main__":  
    sys.exit(int(main() or 0))  
```  
  
 Zwykle podczas pracy nad kodem w programie Visual Studio, zaczniesz uruchamiać kod, naciskając klawisz F5.  To polecenie kompiluje wszystkie części projektu, które muszą zostać skompilowane i rozpocznie uruchamianie kodu w debugerze.  Możesz nacisnąć klawisze CTRL + F5, aby skompilować i uruchomić swój kod bez debugera.  Dzięki debugerowi kod jest uruchamiany nieco wolniej, ale uzyskasz doskonałe funkcje debugowania dla tego kosztu.  
  
 Innym sposobem na uruchomienie kodu jest przechodzenie krok po kroku polecenia (zwykle powiązane z klawiszem F11).  Jest to podobne do F5, ale wstrzymuje wykonywanie w każdej instrukcji.  Jeśli chcesz przerwać program w pewnym momencie, możesz nacisnąć przycisk lewego wskaźnika na lewym marginesie edytora kodu, aby ustawić punkt przerwania.  Po naciśnięciu klawisza F5 wykonywanie programu zostanie przerwane lub zatrzymane w wierszu z punktem przerwania.  Menu Debugowanie zawiera więcej opcji wykonywania kroków; na przykład Przekrocz instrukcje wywołania funkcji (F10), Wkrocz do wywołania funkcji (F11) lub Pomiń na końcu funkcji (Shift-F11).  
  
 W debugerze można wykonać kilka czynności.  Okno zmienne lokalne pokazuje bieżące wartości zmiennych lokalnych.  Po przekroczeniu kodu ustawienia lokalne są wyświetlane automatycznie.  Okno zmiennych, które pokazuje zmienne w bieżącym wierszu, w których wykonywanie zostało zatrzymane.  W okno wyrażeń kontrolnych można wpisać dowolne wyrażenie języka Python, które debuger będzie automatycznie aktualizować po każdym zatrzymaniu wykonywania.  Można również umieścić wskaźnik nad zmiennymi w oknach edytora, aby wyświetlić podręczny ekran wartości zmiennej, a wyświetlacz przedstawiający dane pozwala na inspekcję obiektów.  Niektóre typy danych mają specjalne Wizualizatory, które są dostępne z wyświetlania etykietki danych (na przykład ciągi z formatowaniem specjalnym, takim jak HTML, XML czy JSON).  
  
 Okno stos wywołań zawiera oczekujące wywołania funkcji, które doprowadziły do bieżącej instrukcji, w której debuger jest zatrzymany.  Możesz wybrać różne ramki stosu (linie w stosie wywołań), aby przejść do lokalizacji, w której kod będzie kontynuował wykonywanie w każdej funkcji, odszukać wartości zmiennych i tak dalej.  
  
 Możesz obejrzeć te instrukcje w bardzo krótkim [filmie wideo](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4)w serwisie YouTube.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja typu wiki](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [PTVS Wprowadzenie i głębokie wideo szczegółowe](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
