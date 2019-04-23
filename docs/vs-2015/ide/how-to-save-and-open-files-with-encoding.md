---
title: 'Instrukcje: Zapisywanie i otwieranie plików z kodowaniem | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bb4e07f90f3a05f61957898c579b9a70da6e5ce1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039230"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Instrukcje: Zapisywanie i otwieranie plików z kodowaniem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pliki można zapisać przy użyciu określonych znaków kodowania w celu włączenia obsługi języków dwukierunkowych. Można również określić kodowanie podczas otwierania pliku, tak aby program Visual Studio Wyświetla plik poprawnie.  
  
### <a name="to-save-a-file-with-encoding"></a>Aby zapisać plik z kodowaniem  
  
1. Z **pliku** menu, wybierz **Zapisz plik jako**, a następnie kliknij przycisk listy rozwijanej obok pola **Zapisz** przycisku.  
  
     **Zaawansowane opcje zapisywania** zostanie wyświetlone okno dialogowe.  
  
2. W obszarze **kodowanie**, wybierz kodowanie do użycia dla pliku.  
  
3. Opcjonalnie w obszarze **zakończenia wierszy**, wybierz format znaki końca wiersza.  
  
     Ta opcja jest przydatna, jeśli zamierzasz wymiany plików z użytkownicy systemów operacyjnych.  
  
     Jeśli chcesz pracować z pliku, który został zakodowany w określony sposób można stwierdzić, Visual Studio, aby użyć kodowania podczas otwierania pliku. Metody, których używasz, zależy od tego, czy plik jest częścią projektu.  
  
### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Aby otworzyć plik zakodowany, który jest częścią projektu  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik i wybierz **Otwórz za pomocą**.  
  
2. W **Otwórz za pomocą** okno dialogowe, wybierz Otwórz plik w edytorze.  
  
     Wiele edytorów programu Visual Studio, takich jak edytor formularzy spowoduje automatyczne wykrywanie kodowania i Otwórz plik odpowiednio. Jeśli wybierzesz Edytor który pozwala wybrać kodowanie **kodowanie** zostanie wyświetlone okno dialogowe.  
  
3. W **kodowanie** okna dialogowego Wybierz kodowanie, który ma być używany w edytorze.  
  
### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Aby otworzyć plik zakodowany, który nie jest częścią projektu  
  
1. Na **pliku** menu wskaż **Otwórz**, wybierz **pliku** lub **plik z sieci Web**, a następnie wybierz plik aby otworzyć.  
  
2. Kliknij przycisk listy rozwijanej obok pozycji **Otwórz** przycisk, a następnie wybierz **Otwórz za pomocą**.  
  
3. Wykonaj kroki 2 i 3 poprzedniej procedury.  
  
## <a name="see-also"></a>Zobacz też  
 [Kodowanie i globalizacja formularzy Windows](http://msdn.microsoft.com/library/22e8965d-a712-42b3-8167-3ee346bd70f9)   
 [Globalizowanie i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)
