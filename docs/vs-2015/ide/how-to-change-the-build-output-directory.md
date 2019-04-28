---
title: 'Instrukcje: Zmiana katalogu wyjściowego kompilacji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 03288cdfce66527fb48a16891e745765a72615f4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439271"
---
# <a name="how-to-change-the-build-output-directory"></a>Instrukcje: Zmiana katalogu wyjściowego kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Należy określić lokalizację danych wyjściowych, na podstawie — konfiguracja (w przypadku debugowania, wersji lub obie) wygenerowany przez projekt.  
  
> [!NOTE]
> Jeśli masz **Instalatora** projektu patrz Uwaga na końcu tego artykułu.  
  
## <a name="changing-the-build-output-directory"></a>Zmiana katalogu wyjściowego kompilacji  
  
#### <a name="to-change-the-build-output-directory"></a>Aby zmienić katalog wyjściowy kompilacji  
  
1. Na pasku menu wybierz **projektu**, *Appname* **właściwości**. Również kliknięciu prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.  
  
2. Jeśli masz projekt języka Visual Basic, wybierz **skompilować** kartę. Jeśli masz projekt Visual C#, wybierz **kompilacji** kartę. Jeśli masz projekt języka C++ lub projektu w języku JavaScript, wybierz opcję **ogólne** kartę.  
  
3. W konfiguracji listy rozwijanej u góry wybierz konfigurację, której dane wyjściowe pliku lokalizacji, aby zmienić (debugowanie, wydanie lub wszystkie).  
  
     Znajdź pozycję Ścieżka danych wyjściowych (**ścieżkę wyjściową kompilacji** w języku Visual Basic **katalog wyjściowy** w programie Visual C++ **ścieżkę wyjściową** w języku JavaScript i C#). Określ nowy katalog danych wyjściowych kompilacji względem katalogu projektu.  
  
> [!NOTE]
> W projekcie programu Instalatora **nazwę pliku wyjściowego** okno zmienia lokalizację pliku Setup.exe, a nie lokalizacja plików projektów. Aby uzyskać więcej informacji, zobacz **kompilacji, właściwości konfiguracji, okno dialogowe właściwości projektu wdrożenia**.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [Strona właściwości ogólnych (projekt)](http://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45)   
 [Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md)
