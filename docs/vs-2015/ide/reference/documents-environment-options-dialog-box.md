---
title: Dokumenty, środowisko, Opcje — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
- VS.ToolsOptionsPag.Environment.Documents
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 705b1a5992d1a3e7931c316c713d46e7e8c7f72e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657769"
---
# <a name="documents-environment-options-dialog-box"></a>Dokumenty, środowisko, opcje — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Za pomocą tej strony okna dialogowego **Opcje** można sterować wyświetlaniem dokumentów w zintegrowanym środowisku programistycznym (IDE) i zarządzać zmianami zewnętrznymi do dokumentów i plików. Możesz uzyskać dostęp do tego okna dialogowego, klikając opcję **Opcje** w menu **Narzędzia** , a następnie wybierając **dokumenty** w węźle **środowisko** . Jeśli **dokumenty** nie są wyświetlane na liście, wybierz pozycję **Pokaż wszystkie ustawienia** w oknie dialogowym **Opcje** .

> [!NOTE]
> Opcje dostępne w oknach dialogowych oraz nazwy i lokalizacje poleceń menu, które są widoczne, mogą się różnić od tego, co opisano w pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Ponownie Użyj bieżącego okna dokumentu, jeśli zapisano** Po wybraniu powoduje zamknięcie bieżącego dokumentu, jeśli został on zapisany, i otwarcie nowego dokumentu w tym samym oknie. Jeśli bieżący dokument nie został zapisany, pozostaje otwarty i nowy dokument zostanie otwarty w osobnym oknie. Gdy ta opcja jest wyczyszczona, nowe dokumenty są zawsze otwierane w oddzielnych oknach.

 Jeśli wykonujesz nierzadko operacje wycinania i wklejania wielu dokumentów, a chcesz zminimalizować liczbę otwartych dokumentów i okien w miejscu pracy, wypróbuj tę opcję.

 **Wykryj, kiedy plik zostanie zmieniony poza środowiskiem** Gdy ta opcja jest zaznaczona, komunikat natychmiast powiadamia o zmianach w otwartym pliku, który został utworzony przez Edytor poza IDE. Komunikat umożliwia ponowne załadowanie pliku z magazynu.

 **Automatyczne ładowanie zmian, jeśli zapisano** Gdy **wykryjesz, gdy plik zostanie zmieniony poza środowiskiem** wybranym, a otwarty plik w IDE ulegnie zmianie poza IDE, domyślnie generowany jest komunikat ostrzegawczy. Jeśli ta opcja jest włączona, nie są wyświetlane żadne ostrzeżenie i dokument zostanie ponownie załadowany w środowisku IDE w celu pobrania zewnętrznych zmian.

 **Zezwalaj na edytowanie plików tylko do odczytu; Ostrzegaj przy próbie zapisu** Gdy ta opcja jest włączona, można otworzyć i edytować plik tylko do odczytu. Po zakończeniu należy użyć polecenia **Zapisz jako**, aby zapisać plik o nowej nazwie, jeśli chcesz zapisać rekord zmian.

 **Otwórz plik, używając katalogu aktualnie aktywnego dokumentu** Po wybraniu tej opcji określa, że okno dialogowe **Otwórz plik** wyświetla katalog aktywnego dokumentu. Gdy ta opcja jest wyczyszczona, w oknie dialogowym **Otwórz plik** zostanie wyświetlony katalog ostatnio używany do otwierania pliku.

 **Sprawdź spójność końców wierszy przy ładowaniu** Zaznacz tę opcję, aby Edytor skanował końce wiersza w pliku i wyświetlał okno komunikatu w przypadku wykrycia niespójności w sposobie formatowania końców wierszy.

 **Wyświetl ostrzeżenie, gdy globalne cofanie modyfikuje edytowane pliki** Wybierz tę opcję, aby wyświetlić okno komunikatu, gdy **globalne polecenie Cofnij** spowoduje wycofanie zmian refaktoryzacji wprowadzonych w plikach, które również zostały zmienione po operacji refaktoryzacji. Przywrócenie pliku do jego stanu sprzed refaktoryzacji może spowodować odrzucenie kolejnych zmian wprowadzonych w pliku.

 **Pokaż różne pliki w Eksplorator rozwiązań** Wybierz tę opcję, aby wyświetlić węzeł **różne pliki** w **Eksplorator rozwiązań**. Różne pliki są plikami, które nie są skojarzone z projektem lub rozwiązaniem, ale mogą występować w **Eksplorator rozwiązań** dla wygody użytkownika.

> [!NOTE]
> Wybierz tę opcję, aby włączyć polecenie **Widok w przeglądarce** w menu **plik** dla dokumentów sieci Web, które nie są uwzględnione w aktywnej aplikacji sieci Web.

 ** \<** *n* **> elementy zapisywane w projekcie różne pliki** określa liczbę plików, które mają być utrwalane w folderze **MiscellaneousFiles** **Eksplorator rozwiązań**. Te pliki są wyświetlane nawet wtedy, gdy nie są już otwierane w edytorze. Można określić dowolną liczbę całkowitą od 0 do 256. Wartość domyślna to 0.

 Na przykład jeśli ustawisz tę opcję na 5 i masz otwarte 10 różnych plików, po zamknięciu wszystkich 10 plików, pierwsze 5 będzie nadal wyświetlane w folderze **różne pliki** .

 **Zapisuj dokumenty jako Unicode, gdy nie można zapisać danych na stronie kodowej** Wybierz tę opcję, aby spowodować, że pliki zawierające informacje niezgodne z wybraną stroną kodową mają być domyślnie zapisane w formacie Unicode.

## <a name="see-also"></a>Zobacz też
 [Okno dialogowe Opcje środowiska](../../ide/reference/environment-options-dialog-box.md) [różne pliki](../../ide/reference/miscellaneous-files.md) [Wyszukiwanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)
