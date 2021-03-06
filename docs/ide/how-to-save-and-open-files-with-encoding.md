---
title: 'Instrukcje: zapisywanie i otwieranie plików przy użyciu kodowania'
description: Dowiedz się, jak zapisywać i otwierać pliki przy użyciu określonego kodowania, aby podczas otwierania pliku program Visual Studio prawidłowo wyświetlał plik.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d19b6f8e2e614ed397dee2e75807ded895a82d81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927915"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Instrukcje: zapisywanie i otwieranie plików przy użyciu kodowania

Pliki z określonym kodowaniem znaków można zapisać w celu obsługi języków dwukierunkowych. Możesz również określić kodowanie podczas otwierania pliku, aby program Visual Studio prawidłowo wyświetlał plik.

## <a name="to-save-a-file-with-encoding"></a>Aby zapisać plik z kodowaniem

1. Z menu **plik** wybierz polecenie **Zapisz plik jako**, a następnie kliknij przycisk listy rozwijanej obok przycisku **Zapisz** .

     Zostanie wyświetlone okno dialogowe **Zaawansowane opcje zapisywania** .

2. W obszarze **kodowanie** wybierz kodowanie, które ma być używane dla pliku.

3. Opcjonalnie w obszarze **końce wiersza** wybierz format znaków końca wiersza.

     Ta opcja jest przydatna, jeśli zamierzasz wymieniać plik z użytkownikami innego systemu operacyjnego.

     Jeśli chcesz współpracować z plikiem, który znasz w określony sposób, możesz poinstruować program Visual Studio, aby używał tego kodowania podczas otwierania pliku. Używana metoda zależy od tego, czy plik jest częścią projektu.

> [!NOTE]
> Jeśli chcesz zapisać plik projektu z kodowaniem, opcja **Zapisz plik jako** nie jest włączona do momentu zwolnienia projektu.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Aby otworzyć zakodowany plik, który jest częścią projektu

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik i wybierz polecenie **Otwórz za pomocą**.

2. W oknie dialogowym **Otwórz za pomocą** wybierz Edytor, dla którego chcesz otworzyć plik.

     Wiele edytorów programu Visual Studio, takich jak edytor formularzy, automatycznie wykryje kodowanie i odpowiednio otworzy plik. W przypadku wybrania edytora, który umożliwia wybranie kodowania, wyświetlane jest okno dialogowe **kodowanie** .

3. W oknie dialogowym **kodowanie** wybierz kodowanie, które ma być używane przez Edytor.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Aby otworzyć zakodowany plik, który nie jest częścią projektu

1. W menu **plik** wskaż polecenie **Otwórz**, wybierz **plik** lub **plik z sieci Web**, a następnie wybierz plik do otwarcia.

2. Kliknij przycisk listy rozwijanej obok przycisku **Otwórz** i wybierz polecenie **Otwórz za pomocą**.

3. Wykonaj kroki 2 i 3 z poprzedniej procedury.

## <a name="see-also"></a>Zobacz też

- [Kodowanie i podziały wierszy](encodings-and-line-breaks.md)
- [Kodowanie i globalizacja Windows Forms](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Globalizacja i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)
