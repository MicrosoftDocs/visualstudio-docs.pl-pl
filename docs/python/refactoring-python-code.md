---
title: Refaktoryzator kodu Pythona
description: Visual Studio ułatwia refaktoryzowanie kodu języka Python, zmieniając nazwy identyfikatorów, wyodrębniając metody, dodając import i usuwając nieużywane importy.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: db1a551e20c597f98052471910bcb696c878675f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62429901"
---
# <a name="refactor-python-code"></a>Refaktoryzator kodu Pythona

Program Visual Studio udostępnia kilka poleceń do automatycznego przekształcania i czyszczenia kodu źródłowego języka Python:

- [Zmiana nazwy](#rename) zmienia nazwę wybranej klasy, metody lub nazwy zmiennej
- [Metoda wyodrębniania](#extract-method) tworzy nową metodę z wybranego kodu
- [Dodaj import](#add-import) udostępnia tag inteligentny, aby dodać brakujący import
- [Usuwanie nieużywanego importu](#remove-unused-imports) usuwa nieużywane importy

## <a name="rename"></a>Zmiana nazwy

1. Kliknij prawym przyciskiem myszy identyfikator, którego nazwę chcesz zmienić, a następnie wybierz pozycję **Zmień nazwę**lub umieść daszek w tym identyfikatorze i wybierz polecenie menu Edytuj**regenerator** >  **Edit** > **rename** (**F2**).
2. W wyświetlonym oknie dialogowym **Zmień nazwę** wprowadź nową nazwę identyfikatora i wybierz przycisk **OK:**

   ![Zmień nazwę monitu o nową nazwę identifer](media/code-refactor-rename-1.png)

3. W następnym oknie dialogowym wybierz pliki i wystąpienia w kodzie, do których należy zastosować zmianę nazwy; wybierz dowolne pojedyncze wystąpienie, aby wyświetlić podgląd konkretnej zmiany:

   ![Zmień nazwę okna dialogowego, aby wybrać miejsce zastosowania zmian](media/code-refactor-rename-2.png)

4. Wybierz **pozycję Zastosuj,** aby wprowadzić zmiany w plikach kodu źródłowego. (Tę akcję można cofnąć).

## <a name="extract-method"></a>Wyodrębnianie metody

1. Wybierz wiersze kodu lub wyrażenia, aby wyodrębnić do oddzielnej metody.
2. Zaznacz polecenie menu Menu metody **Edytuj** > **refaktoryzatora** > **Extract method** lub wpisz **Klawisze Ctrl**+**R** > **M**.
3. W wyświetlonym oknie dialogowym wprowadź nową nazwę metody, wskaż, gdzie ją wyodrębnić, i wybierz dowolne zmienne zamknięcia. Zmienne niewybrane do zamknięcia są przekształcane w argumenty metody:

   ![Okno dialogowe Wyodrębnianie metody](media/code-refactor-extract-method-1.png)

4. Wybierz **przycisk OK,** a kod zostanie odpowiednio zmodyfikowany:

   ![Wpływ wyodrębnienia metody](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Dodaj import

Po umieszczeniu karetki na identyfikator, który nie zawiera informacji o typie, Visual Studio udostępnia tag inteligentny (ikona `import` żarówki po lewej stronie kodu), którego polecenia dodają niezbędne lub `from ... import` instrukcje:

![Dodawanie tagu inteligentnego importu](media/code-refactor-add-import-1.png)

Visual Studio `import` oferuje uzupełnienia dla pakietów najwyższego poziomu i modułów w bieżącym projekcie i standardowej bibliotece. Visual Studio `from ... import` oferuje również uzupełnienia dla podmodułów i podpakietów, a także członków modułu. Uzupełnienia obejmują funkcje, klasy lub eksportowane dane. Wybranie jednej z opcji powoduje dodanie instrukcji w górnej części pliku po `from ... import` innych importowaniu lub do istniejącej instrukcji, jeśli ten sam moduł jest już zaimportowany.

![Wynik dodania importu](media/code-refactor-add-import-2.png)

Visual Studio próbuje odfiltrować członków, które nie są faktycznie zdefiniowane w module, takich jak moduły, które są importowane do innego, ale nie są elementami podrzędnymi modułu podczas importowania. Na przykład wiele modułów `import sys` `from xyz import sys`używać, a nie , więc nie `sys` widać zakończenia importowania z innych `__all__` modułów, `sys`nawet jeśli moduły brakuje elementu członkowskiego, który wyklucza .

Podobnie visual studio filtruje funkcje, które są importowane z innych modułów lub z wbudowanego obszaru nazw. Na przykład, jeśli moduł `settrace` importuje `sys` funkcję z modułu, to teoretycznie można zaimportować go z tego modułu. Ale najlepiej jest używać `import settrace from sys` bezpośrednio, a więc Visual Studio oferuje tej instrukcji w szczególności.

Na koniec, jeśli coś normalnie zostanie wykluczone, ale ma inne wartości, które zostaną uwzględnione (ponieważ nazwa została przypisana wartość w module, na przykład), Visual Studio nadal wyklucza importu. To zachowanie zakłada, że wartość nie powinna być eksportowana, ponieważ jest zdefiniowana w innym module, a zatem dodatkowe przypisanie może być wartością fikcyjną, która również nie jest eksportowana.

## <a name="remove-unused-imports"></a>Usuwanie nieużywanych importów

Podczas pisania kodu, łatwo skończyć `import` z instrukcji dla modułów, które nie są używane w ogóle. Ponieważ visual studio analizuje kod, można automatycznie `import` określić, czy instrukcja jest potrzebna, patrząc na czy zaimportowana nazwa jest używana w zakresie poniżej, gdzie występuje instrukcja.

Kliknij prawym przyciskiem myszy w dowolnym miejscu edytora i wybierz polecenie **Usuń import,** co daje opcje usuwania ze **wszystkich zakresów** lub tylko **bieżącego zakresu:**

![Menu Usuń import](media/code-refactor-remove-imports-1.png)

Visual Studio następnie wprowadza odpowiednie zmiany w kodzie:

![Efekt usuwania importu](media/code-refactor-remove-imports-2.png)

Należy zauważyć, że visual studio nie uwzględnia przepływu sterowania; przy użyciu nazwy `import` przed instrukcja jest traktowana tak, jakby nazwa była w rzeczywistości używana. Visual Studio ignoruje `from __future__` również wszystkie importy, import, które są wykonywane `from ... import *` wewnątrz definicji klasy, a także z instrukcji.
