---
title: 'Instrukcje: zapisywanie i otwieranie plików przy użyciu kodowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9285a72137e4c2f3bdf54ef9f6535dedaa2cd5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670778"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Porady: zapisywanie i otwieranie kodowanych plików
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pliki z określonym kodowaniem znaków można zapisać w celu obsługi języków dwukierunkowych. Możesz również określić kodowanie podczas otwierania pliku, aby program Visual Studio prawidłowo wyświetlał plik.

### <a name="to-save-a-file-with-encoding"></a>Aby zapisać plik z kodowaniem

1. Z menu **plik** wybierz polecenie **Zapisz plik jako**, a następnie kliknij przycisk listy rozwijanej obok przycisku **Zapisz** .

     Zostanie wyświetlone okno dialogowe **Zaawansowane opcje zapisywania** .

2. W obszarze **kodowanie**wybierz kodowanie, które ma być używane dla pliku.

3. Opcjonalnie w obszarze **końce wiersza**wybierz format znaków końca wiersza.

     Ta opcja jest przydatna, jeśli zamierzasz wymieniać plik z użytkownikami innego systemu operacyjnego.

     Jeśli chcesz współpracować z plikiem, który znasz w określony sposób, możesz poinstruować program Visual Studio, aby używał tego kodowania podczas otwierania pliku. Używana metoda zależy od tego, czy plik jest częścią projektu.

### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Aby otworzyć zakodowany plik, który jest częścią projektu

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik i wybierz polecenie **Otwórz za pomocą**.

2. W oknie dialogowym **Otwórz za pomocą** wybierz Edytor, dla którego chcesz otworzyć plik.

     Wiele edytorów programu Visual Studio, takich jak edytor formularzy, automatycznie wykryje kodowanie i odpowiednio otworzy plik. W przypadku wybrania edytora, który umożliwia wybranie kodowania, wyświetlane jest okno dialogowe **kodowanie** .

3. W oknie dialogowym **kodowanie** wybierz kodowanie, które ma być używane przez Edytor.

### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Aby otworzyć zakodowany plik, który nie jest częścią projektu

1. W menu **plik** wskaż polecenie **Otwórz**, wybierz **plik** lub **plik z sieci Web**, a następnie wybierz plik do otwarcia.

2. Kliknij przycisk listy rozwijanej obok przycisku **Otwórz** i wybierz polecenie **Otwórz za pomocą**.

3. Wykonaj kroki 2 i 3 z poprzedniej procedury.

## <a name="see-also"></a>Zobacz też
 [Kodowanie i Windows Forms](https://msdn.microsoft.com/library/22e8965d-a712-42b3-8167-3ee346bd70f9) globalizacja [i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)
