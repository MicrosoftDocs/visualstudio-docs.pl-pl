---
title: 'Wprowadzenie z PTVS: edytowanie kodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 2e883970b4b265b1864d53ef6e1f347160e5aeb9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62550915"
---
# <a name="getting-started-with-ptvs-editing-code"></a>Pierwsze kroki z narzędziami PTVS: edytowanie kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS oferuje wydajne środowisko edytora programu Visual Studio dla języka Python.  
  
 Możesz obejrzeć te instrukcje w bardzo krótkim [filmie wideo](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)w serwisie YouTube.  
  
 Zacznij od podstawowego, pustego szablonu projektu aplikacji języka Python.  
  
 Zacznij wpisywać `from … import` wiersz w edytorze.  Zostanie wyświetlona lista uzupełniania wyskakujących okienek z pełną listą modułów dostępnych do zaimportowania.  Ta lista różni się w zależności od używanej wersji języka Python i bibliotek, które zostały zainstalowane.  Użyj biblioteki matematycznej jako przykładu.  Należy zauważyć, że podczas wpisywania listy filtrów ukończenia do tych elementów, w tym wpisanych znaków.  Ukończ instrukcję, importując `sin` Identyfikator.  
  
```python  
from math import sin  
  
```  
  
 Podczas kodowania, jeśli używasz niepowiązanego identyfikatora, ale można go znaleźć w bibliotekach, PTVS oferuje podręczną szybką poprawkę w celu dodania odpowiedniej instrukcji importu.  Na przykład, jeśli wpisano `cos` , zobaczysz opcję **Importuj z oferty matematycznej** .  
  
 Możesz użyć fragmentu do wygenerowania kodu.  W menu Edycja wybierz pozycję IntelliSense, a następnie Wstaw fragment kodu.  Teraz wybierz Python, a następnie def.  Wywołaj funkcję `make_dot_string` i Dodaj jeden parametr `x` .  Możesz teraz dodać potwierdzenia do pliku na potrzeby programowania testowego i zobaczysz, że PTVS już może oferować nową funkcję na listach uzupełniania.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 Teraz wróć do nowej funkcji i zacznij pisać następujące treści:  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 Zobaczysz, że PTVS zakłada, że parametr jest liczbą całkowitą, ponieważ PTVS przeanalizować Lokacje wywołań do tej funkcji.   Należy również użyć szybkiej poprawki do zaimportowania `radians` .  
  
 Użyj innego fragmentu kodu, aby utworzyć główny blok, wpisując `main` na najwyższego poziomu, wywołując interfejs użytkownika tagów inteligentnych i używając karty, aby wybrać "def Main...".  Napisz pętlę podstawową do wywołania `make_dot_string` .  Zobaczysz PTVS wie, że funkcja zwraca ciąg, jeśli naciśniesz pozycję kropka i zobaczysz proponowane zakończenia.  Informacje o tym typie będą przepływać w całym programie, więc wszędzie tam, gdzie wartości zakończą się, możemy udostępnić etykietki narzędzi i uzupełniania, które pomogą lepiej zrozumieć i napisać kod.  
  
 Dodaj wywołanie do drukowania i powinny być podobne do następujących:  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 Jeśli naciśniesz klawisz F5, kod zostanie uruchomiony w oknie cmd.exe i zobaczysz sekwencję kropki z tyłu i do przodu.  
  
 Możesz obejrzeć te instrukcje w bardzo krótkim [filmie wideo](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)w serwisie YouTube.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja typu wiki](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [PTVS Wprowadzenie i głębokie wideo szczegółowe](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
