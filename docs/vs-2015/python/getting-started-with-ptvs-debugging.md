---
title: 'Wprowadzenie do narzędzi PTVS: Debugowanie | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197713"
---
# <a name="getting-started-with-ptvs-debugging"></a>Wprowadzenie do narzędzi PTVS: Debugowanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interaktywny debuger programu Visual Studio ułatwia diagnozowanie i rozwiązywanie problemów w kodzie języka Python.  
  
 Możesz obserwować te instrukcje w bardzo krótkim [wideo usługi youtube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
 W poprzednim temacie wprowadzenie pobierania Utwórz pusty projekt aplikacji w języku Python i crda PythonApplication1.py, następujący kod:  
  
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
  
 Zwykle podczas pracy nad kodem w programie Visual Studio rozpoczyna wykonywanie Twojego kodu, naciskając klawisz F5.  To polecenie tworzy żadnych części projektu, które muszą zostać skompilowane i uruchamiania kodu w debugerze.  Możesz wcisnąć Ctrl + F5, aby skompilować i uruchomić kod bez debugera.  Za pomocą debugera Twój kod działa nieco wolniej, ale możesz uzyskać wspaniałe funkcje debugowania koszty.  
  
 Innym sposobem, aby uruchomić kod jest za pomocą polecenia Wkrocz (zazwyczaj powiązane z F11).  Jest on podobny do F5, ale wstrzymuje wykonywanie w każdej instrukcji.  Jeśli chcesz przerwać program w pewnym momencie, możesz nacisnąć przycisk wskaźnik po lewej stronie w lewy margines edytora kodu, aby ustawić punkt przerwania.  Po naciśnięciu klawisza F5 wykonanie programu break, lub zatrzyma wiersz zawierający punkt przerwania.  Menu Debugowanie ma więcej opcji przechodzenie krok po kroku; na przykład Przekrocz nad wywołania funkcji (F10), krok po kroku do wywołania funkcji (F11), lub przejdź na końcu funkcji (shift-F11).  
  
 Istnieje więcej, możesz zrobić po podziale w debugerze.  W oknie zmienne lokalne są wyświetlane bieżące wartości zmiennych lokalnych.  Podczas wykonywania kroków kodu wyświetlanie zmiennych lokalnych jest automatycznie aktualizowany.  Okno zmiennych automatycznych pokazujący zmiennych w bieżącym wierszu gdy wykonywanie zostało zatrzymane.  W oknie czujki można wpisać dowolne wyrażenie języka Python, które automatycznie zaktualizuje debuger zatrzymuje każdego czasu wykonywania.  Możesz również umieścić kursor wskaźnik zmiennych w oknach Edytora, aby zobaczyć wyskakujące wyświetlanie wartości zmiennej, a ten ekran Porada danych umożliwia inspekcję na obiekty.  Niektóre typy danych mają specjalne wizualizatorów, które są dostępne z ekranu Porada danych (na przykład ciągi przy użyciu specjalnego formatowania, takich jak HTML, XML lub JSON).  
  
 W oknie stosu wywołań wyświetlane wywołania oczekujące funkcji, które doprowadziły do bieżącej instrukcji, w której debuger został zatrzymany.  Istnieje możliwość ramek stosu różnych (linie w stosie wywołań) przejdź do których kod będzie kontynuować wykonywanie w każdej funkcji, sprawdź wartości zmiennych i tak dalej.  
  
 Możesz obserwować te instrukcje w bardzo krótkim [wideo usługi youtube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja witryny typu wiki](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [Wprowadzenie rozpoczęcie pracy i Deep Dive wideo narzędzi PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
