---
title: Refaktoryzacja kodu w języku Python
description: Visual Studio ułatwia refaktoryzacji kodu języka Python, zmieniając nazwę identyfikatorów, wyodrębnianie metody, dodając Importy i usuwanie nieużywanych importuje.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 26a9fa2ee8673b3e8773484409ee680f14780d7a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859110"
---
# <a name="refactor-python-code"></a>Refaktoryzacja kodu w języku Python

Program Visual Studio zapewnia kilka poleceń dla automatycznie Przekształcanie i czyszczenie kodu źródłowego języka Python:

- [Zmień nazwę](#rename) zmienia nazwę wybranej klasy, metody lub nazwę zmiennej
- [Wyodrębnij metodę](#extract-method) tworzy nową metodę z zaznaczonego kodu
- [Dodaj import](#add-import) zapewnia tagu inteligentnego, aby dodać brakujący importu
- [Usuwanie nieużywanych dyrektyw import](#remove-unused-imports) spowoduje usunięcie nieużywanych dyrektyw Import

## <a name="rename"></a>Zmień nazwę

1. Kliknij prawym przyciskiem myszy identyfikator, który chcesz zmienić nazwę i wybierz **Zmień nazwę**, lub ustaw karetkę identyfikatora i wybierz **Edytuj** > **Refaktoryzuj**  >  **Zmień nazwę** polecenia menu (**F2**).
2. W **Zmień nazwę** wyświetlonym oknie dialogowym wprowadź nową nazwę dla identyfikatora, a następnie wybierz pozycję **OK**:

   ![Zmień nazwę monit o podanie nowej nazwy identyfikator](media/code-refactor-rename-1.png)

3. W następnym oknie dialogowym Wybierz pliki i wystąpienia w kodzie, do którego należy zastosować, zmianę nazwy; Wybierz wszystkie poszczególne wystąpienia określonej zmiany w wersji zapoznawczej:

   ![Zmienianie nazwy okna dialogowego, aby wybrać lokalizację zastosować zmiany](media/code-refactor-rename-2.png)

4. Wybierz **Zastosuj** będzie wprowadzenie zmian do plików kodu źródłowego. (Tę akcję można cofnąć.)

## <a name="extract-method"></a>Wyodrębnianie metody

1. Wybierz wiersze kodu lub wyrażenie które ma wyodrębnić do oddzielnych metodach.
2. Wybierz **Edytuj** > **Refaktoryzuj** > **Extrahovat metodu** polecenie menu lub typ **Ctrl** + **R** > **M**.
3. W wyświetlonym oknie dialogowym wprowadź nową nazwę metody, wskaż, gdzie Wyodrębnij ją, a następnie wybierz pozycję Wszystkie zmienne zamknięcia. Zmienne, które nie zostały wybrane do zamknięcia są przekształcane w argumenty metody:

   ![Wyodrębnij metodę okna dialogowego](media/code-refactor-extract-method-1.png)

4. Wybierz **OK** i kod zostanie odpowiednio zmodyfikowany:

   ![Efekt wyodrębnianie metody](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Dodaj import

Po umieszczeniu karetkę na identyfikator informacje typu nie ma program Visual Studio udostępnia tagu inteligentnego (ikonę żarówki po lewej stronie kodu), której polecenia Dodaj niezbędne `import` lub `from ... import` instrukcji:

![Dodawanie tagów inteligentnych importu](media/code-refactor-add-import-1.png)

Program Visual Studio oferuje `import` uzupełnienia dla najwyższego pakiety i moduły w bieżącym projekcie i standardową bibliotekę. Program Visual Studio oferuje również `from ... import` uzupełnienia dla modułów podrzędnych i podpakietów, jak również elementy członkowskie modułu. Uzupełnianie obejmują funkcje, klasy lub wyeksportowane dane. Wybierając jedną z opcji dodaje instrukcję, aby w górnej części pliku, po innych Importy lub z istniejącymi `from ... import` instrukcji, jeśli w tym samym module jest już zaimportowana.

![Wynikiem dodania importu](media/code-refactor-add-import-2.png)

Program Visual Studio próbuje odfiltrować elementy członkowskie, które faktycznie nie są zdefiniowane w module, takie jak moduły są importowane do innego, które nie są elementy podrzędne, wykonując importu modułu. Na przykład użyć wielu modułów `import sys` zamiast `from xyz import sys`, więc nie widzisz zakończenia importowania `sys` z innych modułów, nawet jeśli brak modułów `__all__` elementu członkowskiego, który wyklucza `sys`.

Podobnie program Visual Studio filtruje funkcje, które są importowane z innymi modułami lub z wbudowanego obszaru nazw. Na przykład jeśli importuje moduł `settrace` funkcji z `sys` modułu, a następnie teoretycznie można go zaimportować z tego modułu. Ale najlepiej użyć `import settrace from sys` bezpośrednio, a zatem program Visual Studio udostępnia specjalnie tej instrukcji.

Ponadto jeśli coś zwykle można wykluczyć, ale ma inne wartości, które mogłyby zostać uwzględnione w (ponieważ jest to nazwa została przypisana wartość w module, na przykład), program Visual Studio nadal nie obejmuje importowania. To zachowanie przyjęto założenie, że wartość nie powinna wyeksportowany, ponieważ jest on zdefiniowany w innym module, a zatem dodatkowego przydziału jest prawdopodobnie fikcyjnego wartość, która eksportowane są również nie.

## <a name="remove-unused-imports"></a>Usuwanie nieużywanych dyrektyw Import

Podczas pisania kodu, jest łatwo skończyć z `import` instrukcji dla modułów, które nie są w ogóle używane. Ponieważ program Visual Studio analizuje kod, można określić automatycznie czy `import` instrukcji jest potrzebny, analizując czy zaimportowane nazwa jest używana w zakresie, poniżej której występuje instrukcja.

Kliknij prawym przyciskiem myszy w dowolnym miejscu w edytorze i wybierz pozycję **Usuń Importy**, które zapewnia opcje, aby usunąć z **wszystkie zakresy** lub po prostu **bieżącego zakresu**:

![Usuwanie menu Importy](media/code-refactor-remove-imports-1.png)

Visual Studio następnie wprowadza odpowiednie zmiany w kodzie:

![Wpływ usunięcia Importy](media/code-refactor-remove-imports-2.png)

Należy pamiętać, że program Visual Studio nie uwzględnia się tego do przepływu sterowania; przy użyciu nazwy przed `import` instrukcji jest traktowany tak, jakby nazwa faktycznie został użyty. Program Visual Studio ignoruje także wszystkie `from __future__` importów, Importy, podczas których są wykonywane wewnątrz definicji klasy, jak również z `from ... import *` instrukcji.
