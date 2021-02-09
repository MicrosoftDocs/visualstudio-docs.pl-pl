---
title: Wyświetlanie zależności między plikami źródłowymi i nagłówkami C++
description: Zawiera informacje na temat map kodu dla projektów języka C++.
ms.date: 05/16/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9c2aa1e49c0465fcf75917f0d9bd134962794c74
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861754"
---
# <a name="code-maps-for-c-projects"></a>Mapy kodu dla projektów C++

Jeśli chcesz utworzyć dokładniejsze mapy dla projektów języka C++, ustaw dla tych projektów opcję **/fr**(przeglądanie informacji kompilatora). W przeciwnym razie pojawi się komunikat i monit o ustawienie tej opcji. Jeśli wybierzesz **OK**, spowoduje to ustawienie opcji tylko dla bieżącej mapy. Możesz wybrać opcję ukrycia komunikatu dla wszystkich późniejszych map.

Po otwarciu rozwiązania, które zawiera projekty Visual C++, aktualizacja bazy danych w technologii IntelliSense może zająć trochę czasu. W tym czasie może nie być możliwe utworzenie map kodu dla plików nagłówkowych (*. h* lub `#include` ), dopóki nie zakończy się aktualizowanie bazy danych IntelliSense. Można monitorować postęp uaktualnienia na pasku stanu programu Visual Studio.

- Aby wyświetlić zależności między wszystkimi plikami źródłowymi i plikami nagłówkowymi w rozwiązaniu, wybierz pozycję **Architektura**  >  **generowanie grafu plików dołączanych**.

   ![Wykres zależności dla kodu natywnego](../modeling/media/dependencygraphgeneral_nativecode.png)

- Aby wyświetlić zależności między aktualnie otwartym plikiem i powiązanymi plikami źródłowymi i plikami nagłówkowymi, Otwórz plik źródłowy lub plik nagłówkowy. Otwórz menu skrótów pliku w dowolnym miejscu w pliku. Wybierz pozycję **Generuj Graf plików dołączanych**.

   ![Wykres zależności pierwszego poziomu dla pliku h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Rozwiązywanie problemów z mapami kodu dla kodu C i C++

Te elementy nie są obsługiwane dla kodu C i C++:

- Typy podstawowe nie są wyświetlane na mapach, które zawierają hierarchię nadrzędną.

- Większość elementów menu **Pokaż** jest niedostępna dla kodu C i C++.

Te problemy mogą wystąpić podczas tworzenia map kodu dla kodu C i C++:

|**Wykonaj**|**Możliwa przyczyna**|**Rozwiązanie**|
|-|-|-|
|Nie można wygenerować mapy kodu.|Żadne projekty w rozwiązaniu nie zostały pomyślnie skompilowane.|Napraw błędy kompilacji, które wystąpiły, a następnie ponownie Wygeneruj mapę.|
|Program Visual Studio przestaje odpowiadać przy próbie wygenerowania mapy kodu z menu **architektury** .|Plik bazy danych programu (.pdb) może być uszkodzony.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Kompiluj rozwiązanie ponownie, a następnie spróbuj jeszcze raz.|
|Niektóre ustawienia dla bazy danych przeglądania IntelliSense są wyłączone.|Niektóre ustawienia IntelliSense można wyłączyć w oknie dialogowym **Opcje** programu Visual Studio.|Włącz te ustawienia.<br /><br /> Zobacz [Opcje, Edytor tekstu, C/C++, zaawansowane](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Komunikat **nieznane metody** pojawi się w węźle metody.<br /><br /> Ten problem występuje, ponieważ nie można rozpoznać nazwy metody.|Plik binarny może nie mieć podstawowej tabeli relokacji.|Włącz opcję **/FIXED: No** w konsolidatorze.|
||Plik bazy danych programu (.pdb) może nie być skompilowany.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Włącz opcję **/Debug** w konsolidatorze.|
||Nie można otworzyć lub znaleźć pliku .pdb w oczekiwanych lokalizacjach.|Upewnij się, że plik .pdb istnieje w oczekiwanych lokalizacjach.|
||Informacje o debugowaniu pochodzą z pliku .pdb.|Jeśli w konsolidatorze użyto opcji **/PDBSTRIPPED** , Dołącz do niej kompletny plik. pdb.|
||Obiekt wywołujący nie jest funkcją i jest albo osadzony w pliku binarnym, albo stanowi wskaźnik w sekcji danych.|Gdy obiekt wywołujący jest thunk, spróbuj użyć, `_declspec(dllimport)` Aby uniknąć thunk.|

## <a name="see-also"></a>Zobacz też

- [Mapowanie zależności za pomocą map kodu](../modeling/map-dependencies-across-your-solutions.md)
