---
title: 'Instrukcje: Zapisywanie i otwieranie plików z zastosowaniem kodowania'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd3d7ccc248785c127c1eaf34da8840f824e4195
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104034"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Instrukcje: Zapisywanie i otwieranie plików z zastosowaniem kodowania

Pliki można zapisać przy użyciu określonych znaków kodowania w celu włączenia obsługi języków dwukierunkowych. Można również określić kodowanie podczas otwierania pliku, tak aby program Visual Studio Wyświetla plik poprawnie.

## <a name="to-save-a-file-with-encoding"></a>Aby zapisać plik z kodowaniem

1. Z **pliku** menu, wybierz **Zapisz plik jako**, a następnie kliknij przycisk listy rozwijanej obok pola **Zapisz** przycisku.

     **Zaawansowane opcje zapisywania** zostanie wyświetlone okno dialogowe.

2. W obszarze **kodowanie**, wybierz kodowanie do użycia dla pliku.

3. Opcjonalnie w obszarze **zakończenia wierszy**, wybierz format znaki końca wiersza.

     Ta opcja jest przydatna, jeśli zamierzasz wymiany plików z użytkownicy systemów operacyjnych.

     Jeśli chcesz pracować z pliku, który został zakodowany w określony sposób można stwierdzić, Visual Studio, aby użyć kodowania podczas otwierania pliku. Metody, których używasz, zależy od tego, czy plik jest częścią projektu.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Aby otworzyć plik zakodowany, który jest częścią projektu

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik i wybierz **Otwórz za pomocą**.

2. W **Otwórz za pomocą** okno dialogowe, wybierz Otwórz plik w edytorze.

     Wiele edytorów programu Visual Studio, takich jak edytor formularzy spowoduje automatyczne wykrywanie kodowania i Otwórz plik odpowiednio. Jeśli wybierzesz Edytor który pozwala wybrać kodowanie **kodowanie** zostanie wyświetlone okno dialogowe.

3. W **kodowanie** okna dialogowego Wybierz kodowanie, który ma być używany w edytorze.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Aby otworzyć plik zakodowany, który nie jest częścią projektu

1. Na **pliku** menu wskaż **Otwórz**, wybierz **pliku** lub **plik z sieci Web**, a następnie wybierz plik aby otworzyć.

2. Kliknij przycisk listy rozwijanej obok pozycji **Otwórz** przycisk, a następnie wybierz **Otwórz za pomocą**.

3. Wykonaj kroki 2 i 3 poprzedniej procedury.

## <a name="see-also"></a>Zobacz także

- [Kodowanie i linia podziału](encodings-and-line-breaks.md)
- [Globalizacja formularzy Windows i kodowanie](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Sprzedawać i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)