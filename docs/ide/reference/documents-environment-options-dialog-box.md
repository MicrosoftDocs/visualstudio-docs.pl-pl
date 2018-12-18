---
title: Dokumenty, środowisko, opcje — Okno dialogowe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3009f32adeb70dd376d7116280de6e3e1b557e7a
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388929"
---
# <a name="documents-environment-options-dialog-box"></a>Dokumenty, środowisko, opcje — Okno dialogowe

Ta strona **opcje** okno dialogowe, aby kontrolować wyświetlanie dokumentów w zintegrowanym środowisku programistycznym (IDE) i zarządzanie zmianami zewnętrzne dokumenty i pliki. To okno dialogowe można skorzystać, klikając **opcje** na **narzędzia** menu, a następnie wybierając **dokumenty** w **środowiska** węzła. Jeśli **dokumenty** nie ma na liście, wybierz opcję **Pokaż wszystkie ustawienia** w **opcje** okno dialogowe.

**Użyj ponownie bieżące okno dokumentu, jeśli zapisane**

Po wybraniu powoduje zamknięcie bieżącego dokumentu, jeśli zostały zapisane i zostanie otwarty nowy dokument, w tym samym oknie. Jeśli nie został zapisany bieżącego dokumentu, pozostaje otwarty, a nowy dokument jest otwarty w osobnym oknie. Gdy ta opcja jest zaznaczona, nowe dokumenty zawsze Otwórz w oddzielnych okien.

Jeśli wykonania wielu dokumentów wycinania i wklejania rzadko i chcesz zminimalizować liczbę otwartych dokumentów i systemu windows w obszarze roboczym, użyj tej opcji.

**Wykryj, kiedy plik jest zmieniany poza środowiskiem**

Gdy ta opcja jest zaznaczona, komunikat natychmiast powiadamia o zmianach w otwartego pliku, które zostały wprowadzone przez Edytor poza IDE. Komunikat informuje, jak ponownie załadować plik z magazynu.

**Automatyczne ładowanie zmian, jeśli zapisane**

Jeśli masz **Wykryj, kiedy plik jest zmieniany poza środowiskiem** zaznaczone, a domyślnie generowany jest plikiem otwartym w zmiany w środowisku IDE poza IDE komunikat ostrzegawczy. Jeśli ta opcja jest włączona, zostanie wyświetlone nie ostrzeżenie i dokument zostanie ponownie załadowana w środowisku IDE w celu zastosowania zmian zewnętrznych.

**Zezwól na edytowanie plików tylko do odczytu. Ostrzegaj przy próbie zapisu**

Gdy ta opcja jest włączona, możesz otwierać i edytować plików tylko do odczytu. Gdy to zrobisz, musisz użyć **Zapisz jako** polecenie, aby zapisać plik przez nową nazwę, jeśli chcesz zapisać rekord zmiany.

**Otwórz plik używając katalogu aktualnie aktywnego dokumentu**

Po wybraniu tej opcji określa, że **Otwórz plik** okno dialogowe wyświetla katalog aktywnego dokumentu. Gdy ta opcja jest wyczyszczone, **Otwórz plik** okno dialogowe wyświetla katalog ostatnio używany do otwierania pliku.

**Sprawdź spójność końców wierszy przy ładowaniu**

Wybierz tę opcję, aby edytora skanowania końce wierszy w pliku i wyświetlić okno komunikatu, jeśli zostaną wykryte niespójności, w jak sformatowane końce wierszy.

**Wyświetlana ikona ostrzeżenia, gdy globalne cofanie modyfikuje edytowane pliki**

Wybierz tę opcję, aby wyświetlić komunikat przypadku **globalne cofanie** polecenia wycofa refaktoryzacji zmian w plikach, które zostały zmienione po wykonaniu operacji refaktoryzacji. Zwraca plik do stanu refaktoryzacji pre może odrzucić kolejne zmiany wprowadzone w pliku.

**Pokaż różne pliki w Eksploratorze rozwiązań**

Wybierz tę opcję, aby wyświetlić **różne pliki** w węźle **Eksploratora rozwiązań**. Różne pliki to pliki, które nie są skojarzone z projektu lub rozwiązania, ale może być wyświetlany w **Eksploratora rozwiązań** dla Twojej wygody.

> [!NOTE]
> Wybierz tę opcję, aby umożliwić **Pokaż w przeglądarce** polecenie **pliku** menu dla dokumentów sieci web, które nie są uwzględnione w aplikacji sieci web usługi active.

**\<** *n* **> Elementy zapisywane w projekcie plików pozostałych**

Określa liczbę plików, aby trwale w **MiscellaneousFiles** folderu **Eksploratora rozwiązań**. Te pliki są wyświetlane, nawet jeśli nie są już otwarty w edytorze. Można określić liczbę całkowitą z zakresu od 0 do 256. Wartość domyślna to 0.

Na przykład, jeśli dla tej opcji do 5, otwartych 10 różne pliki, gdy zamkniesz wszystkie 10 plików 5 pierwszych będzie nadal widoczny we **różne pliki** folderu.

**Zapisz dokumenty jako Unicode, gdy nie można zapisać danych w stronie kodowej**

Wybierz tę opcję, aby spowodować, że pliki zawierające informacje niezgodne z wybranej strony kodowej można zapisać w formacie Unicode domyślnie.

## <a name="see-also"></a>Zobacz także

- [Środowisko, Opcje — okno dialogowe](../../ide/reference/environment-options-dialog-box.md)
- [Różne pliki](../../ide/reference/miscellaneous-files.md)
- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)