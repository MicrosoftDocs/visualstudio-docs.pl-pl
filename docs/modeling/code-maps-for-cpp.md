---
title: Wyświetlanie zależności między plikami źródłowymi i nagłówkami języka C++
description: Zawiera informacje o mapach kodu dla projektów w języku C++.
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93ac1f7364e23ef9ed2b44ecd1c536a7ab2b3d40
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389673"
---
# <a name="code-maps-for-c-projects"></a>Mapy kodu dla projektów w języku C++

Jeśli chcesz utworzyć bardziej kompletne mapy dla projektów języka C++, ustaw opcję przeglądania kompilatora informacji **(/FR)** dla tych projektów. W przeciwnym razie pojawi się komunikat i monit o ustawienie tej opcji. Jeśli wybierzesz **przycisk OK,** spowoduje to ustawienie opcji tylko dla bieżącej mapy. Możesz ukryć komunikat dla wszystkich późniejszych map.

Po otwarciu rozwiązania, które zawiera projekty Visual C++, aktualizacja bazy danych w technologii IntelliSense może zająć trochę czasu. W tym czasie tworzenie map kodu dla plików nagłówka *(h* lub ) może być możliwe dopiero po zakończeniu aktualizacji bazy `#include` danych IntelliSense. Można monitorować postęp uaktualnienia na pasku stanu programu Visual Studio.

- Aby wyświetlić zależności między wszystkimi plikami źródłowymi i plikami nagłówków w rozwiązaniu, wybierz pozycję **Architektura**  >  **Generuj wykres plików dołączanych.**

   ![Wykres zależności dla kodu natywnego](../modeling/media/dependencygraphgeneral_nativecode.png)

- Aby wyświetlić zależności między aktualnie otwartym plikiem i powiązanymi plikami źródłowymi i plikami nagłówków, otwórz plik źródłowy lub plik nagłówkowy. Otwórz menu skrótów do pliku w dowolnym miejscu w pliku. Wybierz **pozycję Generuj wykres plików dołączanych.**

   ![Wykres zależności pierwszego poziomu dla pliku h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Rozwiązywanie problemów z mapami kodu dla kodu C i C++

Te elementy nie są obsługiwane w przypadku kodu C i C++:

- Typy podstawowe nie są wyświetlane na mapach, które zawierają hierarchię nadrzędną.

- Większość **elementów** menu Pokaż nie jest dostępna dla kodu C i C++.

Te problemy mogą wystąpić podczas tworzenia map kodu dla kodu C i C++:

|**Problem**|**Możliwa przyczyna**|**Rozwiązanie**|
|-|-|-|
|Nie można wygenerować mapy kodu.|Żadne projekty w rozwiązaniu nie zostały pomyślnie skompilowane.|Napraw błędy kompilacji, które wystąpiły, a następnie ponownie wygeneruj mapę.|
|Visual Studio przestaje odpowiadać podczas próby wygenerowania mapy kodu z menu **Architektura.**|Plik bazy danych programu (.pdb) może być uszkodzony.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Kompiluj rozwiązanie ponownie, a następnie spróbuj jeszcze raz.|
|Niektóre ustawienia dla bazy danych przeglądania IntelliSense są wyłączone.|Niektóre ustawienia funkcji IntelliSense mogą być wyłączone w oknie dialogowym Visual Studio **opcje.**|Włącz te ustawienia.<br /><br /> Zobacz [Opcje, Edytor tekstu, C/C++, Zaawansowane.](../ide/reference/options-text-editor-c-cpp-advanced.md)|
|Komunikat **Nieznane metody pojawia** się w węźle metody.<br /><br /> Ten problem występuje, ponieważ nie można rozpoznać nazwy metody.|Plik binarny może nie mieć podstawowej tabeli relokacji.|Włącz opcję **/FIXED:NO** w linkerze.|
||Plik bazy danych programu (.pdb) może nie być skompilowany.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Włącz opcję **/DEBUG** w programie linker.|
||Nie można otworzyć lub znaleźć pliku .pdb w oczekiwanych lokalizacjach.|Upewnij się, że plik .pdb istnieje w oczekiwanych lokalizacjach.|
||Informacje o debugowaniu pochodzą z pliku .pdb.|Jeśli **/PDBSTRIPPED** opcja została użyta w programie linker, zamiast tego należy dołączyć pełny plik .pdb.|
||Obiekt wywołujący nie jest funkcją i jest albo osadzony w pliku binarnym, albo stanowi wskaźnik w sekcji danych.|Gdy wywołujący jest fragmentem, spróbuj użyć funkcji , `_declspec(dllimport)` aby uniknąć tego fragmentu.|

## <a name="see-also"></a>Zobacz też

- [Mapowanie zależności za pomocą map kodu](../modeling/map-dependencies-across-your-solutions.md)
