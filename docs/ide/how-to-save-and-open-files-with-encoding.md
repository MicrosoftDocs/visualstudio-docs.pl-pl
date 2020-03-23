---
title: 'Jak: Zapisywanie i otwieranie plików za pomocą kodowania'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e1e562771567a6ff4f9dc35c9e98ceb5441a074
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596180"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Jak: Zapisywanie i otwieranie plików za pomocą kodowania

Pliki z określonym kodowaniem znaków można zapisywać w celu obsługi języków dwukierunkowych. Można również określić kodowanie podczas otwierania pliku, tak aby program Visual Studio wyświetlał plik poprawnie.

## <a name="to-save-a-file-with-encoding"></a>Aby zapisać plik z kodowaniem

1. Z menu **Plik** wybierz polecenie **Zapisz plik jako**, a następnie kliknij przycisk rozwijany obok przycisku **Zapisz.**

     Zostanie wyświetlone okno dialogowe **Zaawansowane opcje zapisywania.**

2. W **obszarze Kodowanie**wybierz kodowanie, które ma być używane dla pliku.

3. Opcjonalnie w **obszarze Zakończenia wiersza**wybierz format znaków końca wiersza.

     Ta opcja jest przydatna, jeśli zamierzasz wymienić plik z użytkownikami innego systemu operacyjnego.

     Jeśli chcesz pracować z plikiem, o którym wiesz, że jest zakodowany w określony sposób, możesz powiedzieć programowi Visual Studio, aby używał tego kodowania podczas otwierania pliku. Metoda, której używasz, zależy od tego, czy plik jest częścią projektu.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Aby otworzyć zakodowany plik, który jest częścią projektu

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik i wybierz polecenie **Otwórz za pomocą**.

2. W oknie dialogowym **Otwieranie za pomocą** wybierz edytor, za pomocą za pomocą który ma otworzyć plik.

     Wiele edytorów programu Visual Studio, takich jak edytor formularzy, automatycznie wykryje kodowanie i odpowiednio otworzy plik. Jeśli wybierzesz edytor, który umożliwia wybranie kodowania, zostanie wyświetlone okno dialogowe **Kodowanie.**

3. W oknie dialogowym **Kodowanie** wybierz kodowanie, którego powinien używać edytor.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Aby otworzyć zakodowany plik, który nie jest częścią projektu

1. W menu **Plik** wskaż polecenie **Otwórz**, wybierz **polecenie Plik** lub Plik z **sieci Web**, a następnie wybierz plik do otwarcia.

2. Kliknij przycisk rozwijany obok przycisku **Otwórz** i wybierz pozycję **Otwórz z .**

3. Wykonaj kroki 2 i 3 z poprzedniej procedury.

## <a name="see-also"></a>Zobacz też

- [Kodowanie i podziały wierszy](encodings-and-line-breaks.md)
- [Globalizacja kodowania i formularzy systemu Windows](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Globalizacja i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)
