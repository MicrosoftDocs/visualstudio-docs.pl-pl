---
title: 'Wprowadzenie do narzędzi PTVS: Edytowanie kodu | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54758403"
---
# <a name="getting-started-with-ptvs-editing-code"></a>Wprowadzenie do narzędzi PTVS: Edytowanie kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS zawiera wydajne środowisko edytora programu Visual Studio dla języka Python.  
  
 Możesz obserwować te instrukcje w bardzo krótkim [wideo usługi youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Uruchom przy użyciu podstawowych pusty szablon projektu aplikacji w języku Python.  
  
 Zacznij wpisywać ciąg `from … import` wiersza w edytorze.  Zobaczysz, że na liście uzupełniania wyskakującego zawiera pełną listę modułów, które są dostępne dla importu.  Tej listy różni się w zależności od wersji języka Python i co bibliotek został zainstalowany.  Na przykład, należy użyć biblioteka funkcji matematycznych.  Można zauważyć, że podczas wpisywania lista filtrów uzupełnienia do tych elementów, z uwzględnieniem znaków została wpisana.  Wykonaj instrukcję, importując `sin` identyfikatora.  
  
```python  
from math import sin  
  
```  
  
 Podczas kodowania, jeśli należy użyć identyfikatora niepowiązanych ale który można znaleźć w bibliotekach, PTVS oferuje wyskakującego szybkiej poprawki, aby dodać odpowiednią instrukcję importu potrzebne.  Na przykład, jeśli został wpisany `cos`, można zobaczyć, a następnie **importowanego matematyczne** oferowana.  
  
 Fragment kodu służy do generowania kodu.  W obszarze menu Edycja wybierz funkcję IntelliSense, a następnie Wstaw fragment kodu.  Teraz wybierz języka Python, a następnie def.  Wywołaj funkcję `make_dot_string` i Dodaj jeden parametr `x`.  Można dodać potwierdzenia teraz tworzenie testów opartych na pliku, a zobaczysz, że PTVS już zaoferować nową funkcję w listach uzupełniania.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 Teraz wróć do nowych funkcji i rozpocząć pisanie następujące treści:  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 Zobaczysz, że PTVS przyjęto założenie, że parametr jest liczbą całkowitą, ponieważ PTVS został przeanalizowany wywołań tej funkcji.   Należy również użyć szybkiej poprawki, aby zaimportować `radians`.  
  
 Użyj innego fragment kodu, aby utworzyć bloku głównego, wpisując `main` na najwyższego poziomu, wywoływanie tagu inteligentnego interfejsu użytkownika, a za pomocą karty wybrać "def main..."  Zapisywanie podstawowe pętli do wywołania `make_dot_string`.  Zobaczysz, że PTVS wie, że funkcja zwraca ciąg, jeśli naciśnij okres i zobacz oferowane uzupełnienia.  Informacje o tym typie będą przepływać przez cały całego programu, więc wszędzie tam, gdzie znajdą się wartości, firma Microsoft zapewnia etykietki narzędzi uzupełnień, które pomogą Ci aby lepiej zrozumieć i napisać kod.  
  
 Dodaj wywołanie do drukowania, a powinien mieć główny podobny do następującego:  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 Po naciśnięciu klawisza F5, kod jest uruchamiany w oknie cmd.exe, a zobaczysz kropka Densytometr i z powrotem.  
  
 Możesz obserwować te instrukcje w bardzo krótkim [wideo usługi youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja witryny typu wiki](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [Wprowadzenie rozpoczęcie pracy i Deep Dive wideo narzędzi PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
