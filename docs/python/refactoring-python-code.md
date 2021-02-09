---
title: Refaktoryzacja kodu w języku Python
description: Program Visual Studio ułatwia refaktoryzację kodu Python przez zmianę nazw identyfikatorów, wyodrębnianie metod, Dodawanie importów i usuwanie nieużywanych importów.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8eb46f324359549d7f74e8edd90d3056820e234e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902390"
---
# <a name="refactor-python-code"></a>Refaktoryzacja kodu w języku Python

Program Visual Studio udostępnia kilka poleceń umożliwiających automatyczne przekształcanie i czyszczenie kodu źródłowego języka Python:

- [Zmiana nazwy zmienia](#rename) nazwę wybranej klasy, metody lub nazwy zmiennej
- [Metoda Extract](#extract-method) tworzy nową metodę z wybranego kodu
- [Dodaj Import](#add-import) udostępnia tag inteligentny, aby dodać brakujący import
- [Usuń nieużywane Importy](#remove-unused-imports) usuwa nieużywane Importy

## <a name="rename"></a>Zmień nazwę

1. Kliknij prawym przyciskiem myszy identyfikator, którego nazwę chcesz zmienić, a następnie wybierz polecenie **Zmień nazwę** lub Umieść karetkę w tym identyfikatorze, a następnie wybierz polecenie **Edytuj**  >    >  **Zmień nazwę pliku** refaktoryzacji (**F2**).
2. W wyświetlonym oknie dialogowym **zmiany nazwy** wprowadź nową nazwę identyfikatora i wybierz **przycisk OK**:

   ![Zmień nazwę monitu o nową nazwę identyfikator](media/code-refactor-rename-1.png)

3. W następnym oknie dialogowym Wybierz pliki i wystąpienia w kodzie, do których ma zostać zastosowana zmiana nazwy; Wybierz dowolne pojedyncze wystąpienie, aby wyświetlić podgląd określonej zmiany:

   ![Zmień nazwę okna dialogowego, aby wybrać miejsce zastosowania zmian](media/code-refactor-rename-2.png)

4. Wybierz pozycję **Zastosuj** , aby wprowadzić zmiany w plikach kodu źródłowego. (Tę akcję można cofnąć).

## <a name="extract-method"></a>Wyodrębnianie metody

1. Wybierz wiersze kodu lub wyrażenie, które ma zostać wyodrębnione w oddzielną metodę.
2. Wybierz polecenie **Edytuj**  >    >  **metodę Wyodrębnij wyciąg z metody** lub wpisz **Ctrl** + **R**  >  **M**.
3. W wyświetlonym oknie dialogowym wprowadź nową nazwę metody, wskaż, gdzie wyodrębnić ją do i wybierz wszystkie zmienne zamknięcia. Zmienne, które nie zostały wybrane do zamknięcia, są włączone do argumentów metody:

   ![Okno dialogowe wyodrębniania metody](media/code-refactor-extract-method-1.png)

4. Wybierz **przycisk OK** , a kod zostanie odpowiednio zmodyfikowany:

   ![Efekt wyodrębnienia metody](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Dodaj Import

Po umieszczeniu karetki na identyfikatorze, który nie ma informacji o typie, program Visual Studio udostępnia tag inteligentny (ikona żarówki z lewej strony kodu), którego polecenia dodają wymagane `import` lub `from ... import` instrukcję:

![Dodaj tag inteligentny importowania](media/code-refactor-add-import-1.png)

Program Visual Studio oferuje `import` uzupełnianie dla pakietów i modułów najwyższego poziomu w bieżącym projekcie i w standardowej bibliotece. Program Visual Studio oferuje również `from ... import` uzupełniania dla modułów podrzędnych i podpakietów oraz elementów członkowskich modułu. Zakończenia obejmują funkcje, klasy lub wyeksportowane dane. Wybranie dowolnej opcji powoduje dodanie instrukcji do góry pliku po innych importach lub do istniejącej `from ... import` instrukcji, jeśli ten sam moduł jest już zaimportowany.

![Wynik dodania importu](media/code-refactor-add-import-2.png)

Program Visual Studio próbuje odfiltrować elementy członkowskie, które nie są w rzeczywistości zdefiniowane w module, takie jak moduły, które są importowane do innego, ale nie są elementami podrzędnymi modułu importującego. Na przykład wiele modułów używa `import sys` zamiast `from xyz import sys` , dlatego nie widzisz zakończenia importowania `sys` z innych modułów, nawet jeśli w modułach brakuje `__all__` elementu członkowskiego, który wyklucza `sys` .

Podobnie program Visual Studio filtruje funkcje, które są importowane z innych modułów lub z wbudowanej przestrzeni nazw. Na przykład jeśli moduł importuje `settrace` funkcję z `sys` modułu, w teorii można zaimportować ją z tego modułu. Najlepiej jest jednak używać `import settrace from sys` bezpośrednio, a więc program Visual Studio oferuje szczegółowe instrukcje.

Na koniec, jeśli coś zwykle zostanie wykluczone, ale ma inne wartości, które byłyby uwzględnione (ponieważ nazwa została przypisana do modułu, na przykład), program Visual Studio nadal wyklucza import. W przypadku tego zachowania przyjęto założenie, że wartość nie powinna być eksportowana, ponieważ jest zdefiniowana w innym module, w związku z czym dodatkowe przypisanie jest prawdopodobnie wartością fikcyjną, która również nie została wyeksportowana.

## <a name="remove-unused-imports"></a>Usuń nieużywane Importy

Podczas pisania kodu można łatwo kończyć się `import` instrukcjami dla modułów, które nie są używane. Ponieważ program Visual Studio analizuje kod, może automatycznie określić, czy `import` instrukcja jest potrzebna, sprawdzając, czy zaimportowana nazwa jest używana w zakresie, w którym występuje instrukcja.

Kliknij prawym przyciskiem myszy w dowolnym miejscu w edytorze i wybierz pozycję **Usuń Importy**, co umożliwia usunięcie ze **wszystkich zakresów** lub tylko **bieżącego zakresu**:

![Usuń menu Importy](media/code-refactor-remove-imports-1.png)

Program Visual Studio następnie wprowadza odpowiednie zmiany w kodzie:

![Efekt usuwania importów](media/code-refactor-remove-imports-2.png)

Należy zauważyć, że program Visual Studio nie obsługuje przepływu sterowania; użycie nazwy przed `import` instrukcją jest traktowane jak w przypadku użycia nazwy. Program Visual Studio ignoruje także wszystkie `from __future__` Importy, Importy, które są wykonywane wewnątrz definicji klasy, a także `from ... import *` instrukcji.
