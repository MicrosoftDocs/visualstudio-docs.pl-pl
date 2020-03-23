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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7813a2e7686bef5a146e7472bce7f2c24baf9cd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570066"
---
# <a name="options-dialog-box-environment--documents"></a>Okno dialogowe \> Opcje: Dokumenty środowiskowe

Ta strona okna dialogowego **Opcje** służy do kontrolowania wyświetlania dokumentów w zintegrowanym środowisku programistycznym (IDE) i zarządzania zewnętrznymi zmianami w dokumentach i plikach. Dostęp do tego okna dialogowego można uzyskać, klikając polecenie **Opcje** w menu **Narzędzia,** a następnie wybierając polecenie**Dokumenty** **środowiska** > .

**Wykrywanie zmiany pliku poza środowiskiem**

Gdy ta opcja jest zaznaczona, natychmiast zostanie wyświetlony komunikat informujący o zmianach w otwartym pliku wprowadzonych przez edytor spoza IDE. Komunikat umożliwia ponowne załadowanie pliku z magazynu.

**Ponowne ładowanie zmodyfikowanych plików, chyba że istnieją niezapisane zmiany**

Po **wykryciu, gdy plik jest zmieniany poza wybranym środowiskiem** i otwarty plik w IDE zmienia się poza IDE, komunikat ostrzegawczy jest generowany domyślnie. Jeśli ta opcja jest włączona, nie pojawia się ostrzeżenie i dokument jest ponownie ładowany w IDE, aby odebrać zmiany zewnętrzne.

**Zezwalaj na edycję plików tylko do odczytu; ostrzegaj podczas próby zapisania**

Gdy ta opcja jest włączona, można otworzyć i edytować plik tylko do odczytu. Po zakończeniu należy użyć polecenia **Zapisz jako,** aby zapisać plik według nowej nazwy, jeśli chcesz zapisać rekord zmian.

**Otwieranie pliku przy użyciu katalogu aktualnie aktywnego dokumentu**

Po zaznaczeniu tej opcji opcja określa, że w oknie dialogowym **Otwieranie pliku** jest wyświetlany katalog aktywnego dokumentu. Gdy ta opcja jest wyczyszczona, w oknie dialogowym **Otwórz plik** jest wyświetlany katalog ostatnio używany do otwierania pliku.

**Sprawdzanie spójnych zakończeń linii przy obciążeniu**

Wybierz tę opcję, aby edytor skanował zakończenia wierszy w pliku i wyświetlał okno komunikatu, jeśli zostaną wykryte niespójności w sposobie formatowania zakończeń linii.

**Wyświetlanie ostrzeżenia, gdy globalne cofanie zmodyfikuje edytowane pliki**

Wybierz tę opcję, aby wyświetlić okno komunikatu, gdy polecenie **Globalne cofnij** spowoduje wycofanie zmian refaktoryzacji wprowadzonych w plikach, które również zostały zmienione po operacji refaktoryzacji. Zwracanie pliku do stanu wstępnej refaktoryzacji może odrzucić kolejne zmiany wprowadzone w pliku.

**Pokaż różne pliki w Eksploratorze rozwiązań**

Wybierz tę opcję, aby wyświetlić węzeł **Różne pliki** w **Eksploratorze rozwiązań**. Różne pliki to pliki, które nie są skojarzone z projektem lub rozwiązaniem, ale mogą pojawić się w **Eksploratorze rozwiązań** dla Twojej wygody.

> [!NOTE]
> Wybierz tę opcję, aby włączyć polecenie **Wyświetl w przeglądarce** w menu **Plik** dla dokumentów internetowych, które nie zostały uwzględnione w aktywnej aplikacji sieci web.

**Elementy zapisane w projekcie Różne pliki**

Określa liczbę plików, które mają być zachowywane w folderze **Różne pliki** **Eksploratora rozwiązań**. Te pliki są wyświetlane, nawet jeśli nie są już otwarte w edytorze. Można określić dowolną liczbę całkowita od 0 do 256. Domyślna liczba to 0.

Jeśli na przykład ta opcja zostanie ustawiona na 5 i otworzy się 10 różnych plików, po zamknięciu wszystkich 10 plików pierwsze 5 będzie nadal wyświetlane w folderze **Różne pliki.**

**Zapisywanie dokumentów jako Unicode, gdy danych nie można zapisać na stronie kodowej**

Wybierz tę opcję, aby domyślnie zapisywać pliki zawierające informacje niezgodne z wybraną stroną kodową jako Unicode.

## <a name="see-also"></a>Zobacz też

- [Różne pliki](../../ide/reference/miscellaneous-files.md)
- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)
