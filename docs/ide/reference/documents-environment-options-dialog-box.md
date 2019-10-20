---
title: Dokumenty, środowisko, opcje — Okno dialogowe
ms.date: 03/28/2019
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff1b5e83d9aaca0181699e3cc7effcc973ef2349
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661632"
---
# <a name="options-dialog-box-environment--documents"></a>Opcje — okno dialogowe: \> środowiska dokumenty

Za pomocą tej strony okna dialogowego **Opcje** można sterować wyświetlaniem dokumentów w zintegrowanym środowisku programistycznym (IDE) i zarządzać zmianami zewnętrznymi do dokumentów i plików. Możesz uzyskać dostęp do tego okna dialogowego, klikając opcję **Opcje** w menu **Narzędzia** , a następnie wybierając **środowisko**  > **dokumenty**.

**Wykryj, kiedy plik zostanie zmieniony poza środowiskiem**

Gdy ta opcja jest zaznaczona, komunikat natychmiast powiadamia o zmianach w otwartym pliku, który został utworzony przez Edytor poza IDE. Komunikat umożliwia ponowne załadowanie pliku z magazynu.

**Załaduj ponownie zmodyfikowane pliki, chyba że istnieją niezapisane zmiany**

Gdy **wykryjesz, gdy plik zostanie zmieniony poza środowiskiem** wybranym, a otwarty plik w IDE ulegnie zmianie poza IDE, domyślnie generowany jest komunikat ostrzegawczy. Jeśli ta opcja jest włączona, nie są wyświetlane żadne ostrzeżenie i dokument zostanie ponownie załadowany w środowisku IDE w celu pobrania zewnętrznych zmian.

**Zezwalaj na edytowanie plików tylko do odczytu; Ostrzegaj przy próbie zapisu**

Gdy ta opcja jest włączona, można otworzyć i edytować plik tylko do odczytu. Po zakończeniu należy użyć polecenia **Zapisz jako** , aby zapisać plik o nowej nazwie, jeśli chcesz zapisać rekord zmian.

**Otwórz plik, używając katalogu aktualnie aktywnego dokumentu**

Po wybraniu tej opcji określa, że okno dialogowe **Otwórz plik** wyświetla katalog aktywnego dokumentu. Gdy ta opcja jest wyczyszczona, w oknie dialogowym **Otwórz plik** zostanie wyświetlony katalog ostatnio używany do otwierania pliku.

**Sprawdź spójność końców wierszy przy ładowaniu**

Zaznacz tę opcję, aby Edytor skanował końce wiersza w pliku i wyświetlał okno komunikatu w przypadku wykrycia niespójności w sposobie formatowania końców wierszy.

**Wyświetl ostrzeżenie, gdy globalne cofanie modyfikuje edytowane pliki**

Wybierz tę opcję, aby wyświetlić okno komunikatu, gdy **globalne polecenie Cofnij** spowoduje wycofanie zmian refaktoryzacji wprowadzonych w plikach, które również zostały zmienione po operacji refaktoryzacji. Przywrócenie pliku do jego stanu sprzed refaktoryzacji może spowodować odrzucenie kolejnych zmian wprowadzonych w pliku.

**Pokaż różne pliki w Eksplorator rozwiązań**

Wybierz tę opcję, aby wyświetlić węzeł **różne pliki** w **Eksplorator rozwiązań**. Różne pliki są plikami, które nie są skojarzone z projektem lub rozwiązaniem, ale mogą występować w **Eksplorator rozwiązań** dla wygody użytkownika.

> [!NOTE]
> Wybierz tę opcję, aby włączyć polecenie **Widok w przeglądarce** w menu **plik** dla dokumentów sieci Web, które nie są uwzględnione w aktywnej aplikacji sieci Web.

**Elementy zapisywane w projekcie różne pliki**

Określa liczbę plików, które mają być przechowywane w folderze **różne pliki** **Eksplorator rozwiązań**. Te pliki są wyświetlane nawet wtedy, gdy nie są już otwierane w edytorze. Można określić dowolną liczbę całkowitą od 0 do 256. Wartość domyślna to 0.

Na przykład jeśli ustawisz tę opcję na 5 i masz otwarte 10 różnych plików, po zamknięciu wszystkich 10 plików, pierwsze 5 będzie nadal wyświetlane w folderze **różne pliki** .

**Zapisuj dokumenty jako Unicode, gdy nie można zapisać danych na stronie kodowej**

Wybierz tę opcję, aby spowodować, że pliki zawierające informacje niezgodne z wybraną stroną kodową mają być domyślnie zapisane w formacie Unicode.

## <a name="see-also"></a>Zobacz także

- [Różne pliki](../../ide/reference/miscellaneous-files.md)
- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)