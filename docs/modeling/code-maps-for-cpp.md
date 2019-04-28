---
title: Zobacz zależności między plikami źródłowymi C++ a plikami nagłówkowymi
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3904ff08496257d18589e36e5878f49404bbdf7c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422184"
---
# <a name="code-maps-for-c-projects"></a>Mapy kodu dla projektów języka C++

Jeśli chcesz utworzyć pełniejsze mapy dla projektów w języku C++, należy ustawić opcji Przeglądaj informacje kompilatora (**/FR**) w tych projektach. W przeciwnym razie pojawi się komunikat i monit o ustawienie tej opcji. Jeśli wybierzesz **OK**, to ustawienie opcji dla bieżącej mapy. Można ukryć komunikat dla wszystkich nowszych mapy.

Po otwarciu rozwiązania, które zawiera projekty Visual C++, aktualizacja bazy danych w technologii IntelliSense może zająć trochę czasu. W tym czasie nie można utworzyć mapy kodu dla nagłówka (*.h* lub `#include`) plików, dopóki nie zakończy się aktualizowania bazy danych IntelliSense. Można monitorować postęp uaktualnienia na pasku stanu programu Visual Studio.

- Aby wyświetlić zależności między wszystkie pliki źródłowe i pliki nagłówkowe w rozwiązaniu, wybierz **architektury** > **generowania wykresu z pliki dołączane**.

   ![Wykres zależności dla kodu natywnego](../modeling/media/dependencygraphgeneral_nativecode.png)

- Aby wyświetlić zależności między aktualnie otwarty plik oraz pokrewne pliki źródłowe i pliki nagłówkowe, otwórz plik źródłowy lub plik nagłówkowy. Otwórz menu skrótów plików w dowolne miejsce wewnątrz pliku. Wybierz **Generowanie grafu plików dołączanych**.

   ![Wykres zależności pierwszego poziomu dla pliku .h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Rozwiązywanie problemów z mapami kodu dla kodu C i C++

Te elementy nie są obsługiwane dla kodu C i C++:

- Typy podstawowe nie pojawiają się na mapach, zawierających hierarchię nadrzędną.

- Większość **Pokaż** elementów menu nie są dostępne dla kodu C i C++.

Po utworzeniu map kodu dla kodu C i C++, mogą wystąpić następujące problemy:

|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|
|-|-|-|
|Nie można wygenerować mapy kodu.|Żadne projekty w rozwiązaniu nie zostały pomyślnie skompilowane.|Napraw błędy kompilacji, które wystąpiły, a następnie ponownie wygenerować mapę.|
|Program Visual Studio przestaje odpowiadać przy próbie Generuj mapę kodu, z **architektury** menu.|Plik bazy danych programu (.pdb) może być uszkodzony.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Kompiluj rozwiązanie ponownie, a następnie spróbuj jeszcze raz.|
|Niektóre ustawienia dla bazy danych przeglądania IntelliSense są wyłączone.|Niektóre ustawienia opcji IntelliSense mogą być wyłączone w programie Visual Studio **opcje** okno dialogowe.|Włącz te ustawienia.<br /><br /> Zobacz [opcje, Edytor tekstu, C/C++, zaawansowane](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Komunikat **nieznane metody** w węźle metody zostanie wyświetlony.<br /><br /> Ten problem występuje, ponieważ nie można rozpoznać nazwy metody.|Plik binarny może nie mieć podstawowej tabeli relokacji.|Włącz **/Fixed: No** opcji w konsolidatorze.|
||Plik bazy danych programu (.pdb) może nie być skompilowany.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Włącz **/DEBUG** opcji w konsolidatorze.|
||Nie można otworzyć lub znaleźć pliku .pdb w oczekiwanych lokalizacjach.|Upewnij się, że plik .pdb istnieje w oczekiwanych lokalizacjach.|
||Informacje o debugowaniu pochodzą z pliku .pdb.|Jeśli **/pdbstripped** w konsolidatorze użyto opcji, zamiast dołączyć kompletny plik .pdb.|
||Obiekt wywołujący nie jest funkcją i jest albo osadzony w pliku binarnym, albo stanowi wskaźnik w sekcji danych.|Jeśli element wywołujący jest sekcją thunk, spróbuj użyć `_declspec(dllimport)` Aby uniknąć osadzenia.|

## <a name="see-also"></a>Zobacz także

- [Mapowanie zależności z mapami kodu](../modeling/map-dependencies-across-your-solutions.md)